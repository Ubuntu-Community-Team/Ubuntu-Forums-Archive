---
title: "Microarchitectural Data Sampling (MDS) security vulnerabilities in Intel CPUs"
date: 2019-05-18
forum: Announcements &amp; News
---

### Post by wildmanne39 on 2019-05-18
More information can be found at the following links:
[https://people.canonical.com/~ubuntu-security/cve/2018/CVE-2018-12126.html](https://people.canonical.com/~ubuntu-security/cve/2018/CVE-2018-12126.html)

Canonical recommends turning off "Hyper-Threading" 

according to:

[https://blog.ubuntu.com/2019/05/14/ubuntu-updates-to-mitigate-new-microarchitectural-data-sampling-mds-vulnerabilities](https://blog.ubuntu.com/2019/05/14/ubuntu-updates-to-mitigate-new-microarchitectural-data-sampling-mds-vulnerabilities)

Intel microcode and kernels with upgraded patches to fix this issue are located here:

[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/MDS?_ga=2.254131528.1796320856.1558226451-1313768811.1550809221](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/MDS?_ga=2.254131528.1796320856.1558226451-1313768811.1550809221)

Ubuntu users with Intel processors that use KVM virtualization should also ensure that they have the updated qemu packages installed, they are also in the link above with the Intel microcode and the upgraded kernels:

---

