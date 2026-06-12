---
title: "Need help to know if linux will work on this machine"
date: 2008-06-24
forum: Apple Hardware Users
---

### Post by cosmo15900 on 2008-06-24
ok so i play lots and lots of half life. i want to make a server for it and want to run it on my older mac. yes it is a server type mac, but i need it for this. the specs are 

Apple Xserve Server 2GB RAM
 
SPECIFICATIONS
Make/Model: Apple Xserver G4
Processor Speed: G4 1GHz
RAM: 2GB
Hard Drive: 4*200GB drives
DVD(rw)
Operating System: wish for linux but got mac 10.4.9
 
3 firewire 400 ports, 2 USB ports,  ATI Radeon 32MB Video Card,  Gigabit NIC, VGA output
i was wondering if it will be possible for linux to go on this machine and if there is a guide how 2 install, and were i can get linux from. if anyone can help with this info that would be wonderful.. thank you

---

### Post by Bubba64 on 2008-06-24
I don't know anything about Macs but you can down load the ISO of the desktop CD version, then burn a CD, of whatever distribution your thinking of and not install it but see if it runs on your computer.

---

### Post by oswaldkelso on 2008-06-24
If I was feeling like showing you you options I'd send you to the distrowatch link

[http://distrowatch.com/search.php?category=Server&origin=All&basedon=All&desktop=All&architecture=powerpc&status=Active](http://distrowatch.com/search.php?category=Server&origin=All&basedon=All&desktop=All&architecture=powerpc&status=Active)

If I was given 2 seconds to answer I'd give you this one.

[http://www.debian.org/CD/http-ftp/#stable](http://www.debian.org/CD/http-ftp/#stable)

---

### Post by d^2 on 2008-06-24
i have just gotten ubuntu 8.04 (hardy) up and running on the Xserve G4 1.33 ghz machine.

the sticky message at the top of the apple users forum here tells where you can get ubuntu for ppc.

as suggested, burn a live cd and see if it will boot your machine (the live cd doesn't install anything, it loads to your machine's RAM).  if the live cd detects all your stuff, you will most likely be able to install it.

if the live cd appears to work, and you decide to install, post questions here and people will offer suggestions about things to try!

one thing to note is that PPC is different than x86, so some software may not be built for your PPC (there are technical details on the machine code level that prevent some software from being ported, even despite being open source).  i'd make sure that the server software you'd like to run can be installed on PPC hardware.

---

### Post by owlgorithm on 2008-06-25
It should work fine, but you can doublecheck here to make sure:

[https://help.ubuntu.com/8.04/installation-guide/powerpc/hardware-supported.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/hardware-supported.html)

---

### Post by stream303 on 2008-06-25
> **owlgorithm said:**
> It should work fine, but you can doublecheck here to make sure:

Thanks for pointing out that supported hardware page.  It raises an issue about smp that I'll bring up in another thread.  I think the docs may be misleading / out of date.

---

