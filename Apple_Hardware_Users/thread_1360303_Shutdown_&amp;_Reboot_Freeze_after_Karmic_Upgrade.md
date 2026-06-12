---
title: "Shutdown &amp; Reboot Freeze after Karmic Upgrade"
date: 2009-12-20
forum: Apple Hardware Users
---

### Post by edog76 on 2009-12-20
I have an old powerpc iBook G4. Upgraded to Karmic today and all is well aside from the shutdown and reboot freeze. This appears to be a widespread problem for both pc and ppc users from searching for a solution today.

Last messages on the screen are:
init: usplash post-start process (1944) terminated with status 1
* Shutting down ALSA...
* Asking all remaining processes to terminate...

I found this post: [http://ubuntuforums.org/showthread.php?t=1306789&highlight=asking+all+remaining+processes+to+terminate](http://ubuntuforums.org/showthread.php?t=1306789&highlight=asking+all+remaining+processes+to+terminate)
which has some fixes, but they are geared to pc users, and I'm unsure how to translate.

Anyone have any ideas?

---

### Post by rednose0607 on 2009-12-22
> **edog76 said:**
> I have an old powerpc iBook G4. Upgraded to Karmic today and all is well aside from the shutdown and reboot freeze. This appears to be a widespread problem for both pc and ppc users from searching for a solution today.

Last messages on the screen are:
init: usplash post-start process (1944) terminated with status 1
* Shutting down ALSA...
* Asking all remaining processes to terminate...

I found this post: [http://ubuntuforums.org/showthread.php?t=1306789&highlight=asking+all+remaining+processes+to+terminate](http://ubuntuforums.org/showthread.php?t=1306789&highlight=asking+all+remaining+processes+to+terminate)
which has some fixes, but they are geared to pc users, and I'm unsure how to translate.

Anyone have any ideas?

Hi,
I had the same prob. on my PB aluminium 15". In my case It happened to be the b43 module (wifi). Problem solved upgrading to the new kernel (bugs.launchpad.com search for karmic ppc and go for the kernel patched). See [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/476154](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/476154)
Good luck!

---

### Post by edog76 on 2009-12-24
thanks, rednose,

that did the trick. For anyone else looking I patched by following the link provided by one of the developers in the thread, and patched with the .31.16 kernel.

---

### Post by edog76 on 2009-12-25
Spoke too soon. I installed kubuntu, and a few other apps. Then glanced at a list of package updates and approved. One of them was a kernel upgrade to .31.16-#53. The previous kernel patch was for #51, and now the shutdown freeze is back on. I could just update to the .32 kernel. According to the launchpad thread, the patch is in that kernel. But, I'd like to know if anyone else is successfully using that kernel on an old ppc first. Alternatively, anyone know how to edit the yaboot.conf file to be able to choose the #51 kernel? On my PC, this is pretty easy, but I've never touched yaboot.

---

### Post by jay.ar.oh on 2009-12-27
not entirely sure if this is completely related to the problems seen above, but I ran into the issue of not being able to reboot after installing 9.10 server edition on a brand new Mac Mini.  After a lot of digging around I took a shot at updating the boot option to contain "reboot=pci".  From the initial look of things, it worked.  

in /etc/default/grub

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **reboot=pci**"
GRUB_CMDLINE_LINUX=""
```

---

### Post by edog76 on 2009-12-27
Thanks Jay, 
but there's no grub on powerpcs and I don't know where in the yaboot.conf to put a command like that. The examples I've found online are all pretty simple. The main problem appears to be that the kernel and the broadcom wireless chip do not get along.

---

