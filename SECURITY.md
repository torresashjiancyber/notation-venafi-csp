# Security Policy

## Supply Chain Risk Exceptions

This document tracks known supply chain risks and their mitigation status.

### Dependency Risk Assessment

#### Azure/go-ntlmssp (Unmaintained)

- **Status**: Risk Accepted
- **Last Release**: 2021
- **CWE**: CWE-1104 (Use of Unmaintained Third Party Components)
- **Severity**: Medium
- **Justification**: This dependency is pulled in transitively through `github.com/go-ldap/ldap/v3`. The codebase only uses `ldap.ParseDN()` for Distinguished Name parsing and does not make LDAP connections or use NTLM authentication. The NTLM code path is unreachable in our usage.
- **Mitigation**: The code does not exercise any NTLM-related functionality. Future work should consider migrating to a DN-parsing-only library if one becomes available.
- **Tracking**: VC-53645

#### digitorus/pkcs7 (Stale Pseudo-Version)

- **Status**: Risk Accepted - Monitoring
- **Last Update**: 2023-08-18 (pseudo-version)
- **CWE**: CWE-1104 (Use of Unmaintained Third Party Components)
- **Severity**: Medium
- **Justification**: This dependency is pulled in transitively through `github.com/digitorus/timestamp`, which is actively used for RFC 3161 timestamp operations in signature creation.
- **Mitigation**: Tracking the notaryproject ecosystem for migration to a maintained PKCS#7 implementation. This is a transitive dependency; replacement would require either updating digitorus/timestamp or replacing it with an alternative timestamp library.
- **Tracking**: VC-53645

## Reporting a Vulnerability

Please report security vulnerabilities to the Venafi security team.
