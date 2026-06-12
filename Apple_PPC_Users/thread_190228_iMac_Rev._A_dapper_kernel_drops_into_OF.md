---
title: "iMac Rev. A dapper kernel drops into OF"
date: 2006-06-06
forum: Apple PPC Users
---

### Post by paraparker on 2006-06-06
Hi folks - noob alert so sorry in advance for what will be painfully obvious to most I'm sure. I went to upgrade from Breezy to Dapper on an iMac Rev. A and ran into the, now well known I guess, kernel problem of dropping into Open Firmware, which barks something about chunk size, ramdisk etc. etc.

I would like to boot from the older vmlinux-2.6.12-10-powerpc kernel in /etc/boot as I hear that works, but being a noob I don't know how to switch kernels for boot. Is it as simple as deleting the existing initrd.img and vmlinux links and creating new links pointing to the older kernel?

I've honestly tried searching around for an answer, but am having search brain farts tonight and can't seem to find out how to boot from an older kernel. TIA

---

### Post by warp99 on 2006-06-06
Know issue and a bug fix is in the works:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508")

Should be resolved very soon. :cool:

---

### Post by warp99 on 2006-06-06
[QUOTE=paraparker]
I would like to boot from the older vmlinux-2.6.12-10-powerpc kernel in /etc/boot as I hear that works, but being a noob I don't know how to switch kernels for boot. Is it as simple as deleting the existing initrd.img and vmlinux links and creating new links pointing to the older kernel?
[/QUOTE]

That's what I did since I didn't want to update the yaboot bin. I also wanted to make is very easy to boot into the old kernel if the new kernel didn't work for some reason. :cool:

---

