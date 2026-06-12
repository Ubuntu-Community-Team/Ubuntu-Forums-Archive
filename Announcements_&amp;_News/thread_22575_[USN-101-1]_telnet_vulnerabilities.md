---
title: "[USN-101-1] telnet vulnerabilities"
date: 2005-03-28
forum: Announcements &amp; News
---

### Post by Martin Pitt on 2005-03-28
===========================================================
Ubuntu Security Notice USN-101-1	     March 28, 2005
netkit-telnet vulnerabilities
CAN-2004-0911, CAN-2005-0469
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 4.10 (Warty Warthog)

The following packages are affected:

telnet
telnetd

The problem can be corrected by upgrading the affected package to
version 0.17-24ubuntu0.1.  In general, a standard system upgrade is
sufficient to effect the necessary changes.

Details follow:

A buffer overflow was discovered in the telnet client's handling of
the LINEMODE suboptions. By sending a specially constructed reply
containing a large number of SLC (Set Local Character) commands, a
remote attacker (i. e. a malicious telnet server) could execute
arbitrary commands with the privileges of the user running the telnet
client. (CAN-2005-0469)

Michal Zalewski discovered a Denial of Service vulnerability in the
telnet server (telnetd). A remote attacker could cause the telnetd
process to free an invalid pointer, which caused the server process to
crash, leading to a denial of service (inetd will disable the service
if telnetd crashed repeatedly), or possibly the execution of arbitrary
code with the privileges of the telnetd process (by default,
the 'telnetd' user). Please note that the telnet server is not
officially supported by Ubuntu, it is in the "universe"
component. (CAN-2004-0911)

  Source archives:

    [http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/netkit-telnet_0.17-24ubuntu0.1.diff.gz](http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/netkit-telnet_0.17-24ubuntu0.1.diff.gz)
      Size/MD5:    25956 9128f1f018f467891fccb2f201f4b996
    [http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/netkit-telnet_0.17-24ubuntu0.1.dsc](http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/netkit-telnet_0.17-24ubuntu0.1.dsc)
      Size/MD5:      607 a89242a368dcef4ecdd2edfa07b0416e
    [http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/netkit-telnet_0.17.orig.tar.gz](http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/netkit-telnet_0.17.orig.tar.gz)
      Size/MD5:   133749 d6beabaaf53fe6e382c42ce3faa05a36

  amd64 architecture (Athlon64, Opteron, EM64T Xeon)

    [http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/telnet_0.17-24ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/telnet_0.17-24ubuntu0.1_amd64.deb)
      Size/MD5:    68950 2804dc3a5a57869a2dfdc137bb54d49c
    [http://security.ubuntu.com/ubuntu/pool/universe/n/netkit-telnet/telnetd_0.17-24ubuntu0.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/n/netkit-telnet/telnetd_0.17-24ubuntu0.1_amd64.deb)
      Size/MD5:    43932 041bb557db0e071de540dae8ba703aac

  i386 architecture (x86 compatible Intel/AMD)

    [http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/telnet_0.17-24ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/telnet_0.17-24ubuntu0.1_i386.deb)
      Size/MD5:    62892 37527def740efa14d836b69dc27f1b53
    [http://security.ubuntu.com/ubuntu/pool/universe/n/netkit-telnet/telnetd_0.17-24ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/n/netkit-telnet/telnetd_0.17-24ubuntu0.1_i386.deb)
      Size/MD5:    40264 782d910cecdb2e54c70428ce1ab95c51

  powerpc architecture (Apple Macintosh G3/G4/G5)

    [http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/telnet_0.17-24ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/n/netkit-telnet/telnet_0.17-24ubuntu0.1_powerpc.deb)
      Size/MD5:    68312 0f428ccfee13a0cd327249a99bd61138
    [http://security.ubuntu.com/ubuntu/pool/universe/n/netkit-telnet/telnetd_0.17-24ubuntu0.1_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/universe/n/netkit-telnet/telnetd_0.17-24ubuntu0.1_powerpc.deb)
      Size/MD5:    42526 2eb26f374295a63137b8735b1225927b

-- 
ubuntu-security-announce mailing list
[email]ubuntu-security-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.5 (GNU/Linux)

iD8DBQFCSEnvDecnbV4Fd/IRArhLAKCd/L2g3JXheL2MAumoy+oslALgwACbBOM7
Wye41/pCnHXYx4E9w9Hy2Gs=
=h9jA
-----END PGP SIGNATURE-----

---

