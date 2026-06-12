---
title: "problem installing amd proprietary drivers"
date: 2013-03-16
forum: Any Other OS
---

### Post by johnnygr on 2013-03-16
Hi,

I'm running xbmcbuntu and my amd-e450 system did not run fullhd while it should do so ( and did ). something went probably wrong in some update.

now I'm having problem installing the amd propriarity drivers. somewhere i messed things up.
I think the problem lies in update-alternatives. 

$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320]

$ update-alternatives --get-selections | grep gl_conf
i386-linux-gnu_gl_conf         auto     /usr/lib/nvidia-current/ld.so.conf
x86_64-linux-gnu_gl_conf       auto     /usr/lib/nvidia-current/alt_ld.so.conf
( my system is 32 bit )

shouldn't this be pointing to amd directories? ( i found /usr/lib/fglrx)

$ amdconfig
-bash: amdconfig: command not found



but "amdconfig" is installed, it is in /usr/lib/fglrx/bin/, but somehow no symbolic links are set.

how do i solve this? or is something else my problem?

---

