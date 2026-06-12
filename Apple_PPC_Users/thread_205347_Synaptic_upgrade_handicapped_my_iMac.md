---
title: "Synaptic upgrade handicapped my iMac"
date: 2006-06-28
forum: Apple PPC Users
---

### Post by gtomorrow on 2006-06-28
hello,

i have a rev. a bondi iMac that i had installed Breezy. about a week or so ago (maybe more?) the update notifier informed me i could install the Dapper upgrade. as i like to keep the system current, i said "do it!"

during the upgrade (breezy to dapper) the installer threw, IIRC, 3 errors which unfortunately i did not record. maybe there's a specific log i need to consult? i rebooted crossing my fingers and luckily all went well...except no sound and partial USB. Synaptic said were two broken packages, linux-image-powerpc and linux-image-2.6.15-25-powerpc. so, thanks to the ubuntu forums, i "sudo apt-get -f remove"'d them.

at least the update notifier wasn't telling me there are broken packages anymore. but nevertheless, i still have no sound and gnome fails to see my thumb drive. 

sound in breezy used to have two options (ALSA and OSS). now i have only OSS, even though i reinstalled the ALSA drivers.

now when i try to update, i always get...
```
Cannot install all available updates

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

the following updates will be skipped:
gdk-imlib1
libautotrace3
openexr
```

furthermore if i try to "manually" upgrade the kernel i get this
```
E: /var/cache/apt/archives/linux-image-2.6.15-25-powerpc_2.6.15-25.43_powerpc.deb: failed in buffer_write(fd) (10, ret=-1)

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgnomecupsui1.0-1c2a linux-image-2.6.15-25-powerpc
Suggested packages:
  linux-doc-2.6.15 linux-source-2.6.15
The following packages will be REMOVED:
  libgnomecupsui1.0-1
The following NEW packages will be installed:
  libgnomecupsui1.0-1c2a linux-image-2.6.15-25-powerpc
0 upgraded, 2 newly installed, 1 to remove and 7 not upgraded.
5 not fully installed or removed.
Need to get 0B/22.3MB of archives.
After unpacking 65.0MB of additional disk space will be used.
(Reading database ... 115049 files and directories currently installed.)
Removing libgnomecupsui1.0-1 ...
Selecting previously deselected package libgnomecupsui1.0-1c2a.
(Reading database ... 115044 files and directories currently installed.)
Unpacking libgnomecupsui1.0-1c2a (from .../libgnomecupsui1.0-1c2a_0.31-1.1ubuntu13_powerpc.deb) ...
Unpacking linux-image-2.6.15-25-powerpc (from .../linux-image-2.6.15-25-powerpc_2.6.15-25.43_powerpc.deb) ...
The directory /lib/modules/2.6.15-25-powerpc still exists. Continuing as directed.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.15-25-powerpc_2.6.15-25.43_powerpc.deb (--unpack):
 failed in buffer_write(fd) (9, ret=-1): backend dpkg-deb during `./lib/modules/2.6.15-25-powerpc/kernel/fs/ocfs2/ocfs2.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Cannot delete /boot/initrd.img-2.6.15-25-powerpc, doesn't exist.
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.15-25-powerpc_2.6.15-25.43_powerpc.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

sorry to be so long about it, but i wanted to be thorough. any suggestions? what went wrong? at least the system "works" and i didn't lose anything in process.

any takers?
thanks --gt

---

### Post by gtomorrow on 2006-06-29
let's add to the mix...

alsactl, alsamixer and "lspci | grep audio" tell me the sound card isn't even detected!

--gt

---

### Post by gtomorrow on 2006-06-30
:confused: 
wow, nobody?

---

