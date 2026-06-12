---
title: "Fail to fetch install problem"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by truet on 2007-09-10
**So im trying to urgently install ntfs-3g and ntfs-config so that i can write to ntfs discs. I have problems with trying to install via both synaptic and terminal. Via Synaptic, the following error shows when trying to instll ntfs-3g,**
[I]
W: Failed to fetch [http://flomertens.keo.in/ubuntu/dist...417-1_i386.deb](http://flomertens.keo.in/ubuntu/dist...417-1_i386.deb)
Could not resolve ‘flomertens.keo.in’


W: Failed to fetch [http://flomertens.keo.in/ubuntu/dist...417-1_i386.deb](http://flomertens.keo.in/ubuntu/dist...417-1_i386.deb)
Could not resolve ‘flomertens.keo.in[/I]’

**When trying to install ntfs-config via synaptic the following as soon as i click "mark" the following error shows**

[I]Could not mark all packages for installation upgrade

ntfs-config:
Depends: libdbus-1-2 (>=0.60) but it is not installable[/I]

**So i decided to try Terminal, and yep you guessed it, more errors. Heres what happens with ntfs 3g**

[I]jonathan@Aishwarya:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
libntfs-3g1
The following NEW packages will be installed
libntfs-3g1 ntfs-3g
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 123kB of archives.
After unpacking 369kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
libntfs-3g1 ntfs-3g
Install these packages without verification [y/N]? y
Err [http://flomertens.keo.in](http://flomertens.keo.in) dapper/main libntfs-3g1 1:1.417-1
Could not resolve ‘flomertens.keo.in’
Err [http://flomertens.keo.in](http://flomertens.keo.in) dapper/main ntfs-3g 1:1.417-1
Could not resolve ‘flomertens.keo.in’
Failed to fetch [http://flomertens.keo.in/ubuntu/dist...417-1_i386.deb](http://flomertens.keo.in/ubuntu/dist...417-1_i386.deb) Could not resolve ‘flomertens.keo.in’
Failed to fetch [http://flomertens.keo.in/ubuntu/dist...417-1_i386.deb](http://flomertens.keo.in/ubuntu/dist...417-1_i386.deb) Could not resolve ‘flomertens.keo.in’
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/I]

**and heres ntfs-config**

[I]
jonathan@Aishwarya:~$ sudo apt-get install ntfs-config
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
ntfs-config: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages[/I]
[B]
Thank you very much for all your help. I need to get this solved urgently and apretiate any suggestions. Thanks again.[/B]

---

### Post by overdrank on 2007-09-10
HI maybe these  link will help
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Good luck!:KS

---

### Post by truet on 2007-09-10
Sorry had a read throguh but cant figure out what to do. any suggestions?

---

### Post by univremonster on 2007-09-10
I could be completely off base here, but I would guess that the site is down temporarily and that if you try back in a few hours it would be fine.. I'm not 100% sure, mind you, but that has been the only thing which has given me errors of that sort in the past.  By the way, there weren't more errors in terminal, they were the same ones...

---

### Post by truet on 2007-09-10
I thought that but been trying since thursday... any other suggestions?

---

