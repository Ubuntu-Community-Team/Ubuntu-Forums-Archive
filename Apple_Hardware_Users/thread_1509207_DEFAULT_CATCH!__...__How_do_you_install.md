---
title: "DEFAULT CATCH!  ... ? How do you install?"
date: 2010-06-14
forum: Apple Hardware Users
---

### Post by quinnteq on 2010-06-14
I am attempting to install ubuntu 9.04 onto a NewWorld G3 iMac. 
Specs are as follows:
400MHz PowerPC processor
128 mb of RAM
13 GB HDD
cd/DVD drive (slot loading)

The original OS is not existent as when i purchased it the original HDD died and I'm using a new one. When booting using hte live CD i get to the black terminal screen where it askes me for instructions, i press enter to boot into the live CD and then i get to an open firmware prompt which says 

```
done
copying OF device tree ...
Can't allocate initial device-tree chunk

DEFAULT CATCH!, code=700 at   %SRR0: 01806bac    &SRR1: 00023030
```

Then i get a prompt:
  ok
0 >

Now I am a PC pro, a intermediate linux guy and a Mac newbie (first mac i picked up ever).
I want to make it run as this is just a side project for me. How do i get ubuntu to install onto this box? Am I doing something wrong? Or am I missing something?

---

### Post by 3rdalbum on 2010-06-14
I don't know what the error is; but it may be an incorrectly burned disc. Sounds like a dumb question, but you ARE using the PowerPC edition and not the i386 edition? That era of Macintosh used the PowerPC processor and requires its own special edition of Ubuntu.

---

### Post by linuxopjemac on 2010-06-14
some reading before you go on:
[http://mac.linux.be/content/apple-powerpc-wiki](http://mac.linux.be/content/apple-powerpc-wiki)

---

### Post by quinnteq on 2010-06-14
Yes, i am using the PPC version of Ubuntu. ( was clever enough to get that far :wink:) I get the ubuntu/yaboot prompt to boot up the live cd when i hold down the C key on the boot chime. Once i type live, or anything at all, then  press enter, I get the open firmware prompt.

This may sound silly, but can you use any HDD in a Mac? Maybe the HDD in it is dead? Not sure, i wouldn't know how to tell within just open firmware if its detected or not.

I have a ton of IDE drives lying around, but cracking this thing open is a terrible pain in the butt for just replacing one drive let alone trying a ton of them. I read the spec's online for my machine and it says that it uses ultra IDE so, will any IDE drive work? How can i tell if the one installed is detected?

---

### Post by linuxopjemac on 2010-06-14
At that point of the installation, your hard disk does not yet come into play. The problem is that it won't boot into the Linux environment after that. My personal experience is that CDROM drives of old Apple machines do not work well. I advise to do a net-installation.
Use this [mini.iso]("http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso") and follow [these directions]("http://mac.linux.be/content/mint-lxde-debian-lenny-ppc").

Good luck. I will see you back soon for solving your X problem ;)

---

### Post by quinnteq on 2010-06-15
ahahah, yea, im sure. I did find some tutorials out there for that. I'll give this a try this weekend when i get a chance to. Ill read this over and give it a shot as soon as i can.

Thanks!

---

### Post by KittyKitty on 2011-10-30
I had installed and had the system running with no problems, i believe my wife turned the box off without first shutting it down properly, but now I get this error message
using the yaboot loader i have tried to load alternate kernel images and they do load from the hard disk (so it may be in need of a fsck but it is not dead) but once the ramdisk is loaded it pops back to the open firmware prompt stating nearly identicle error

done
copying OF device tree ...
Can't allocate initial device-tree chunk

DEFAULT CATCH!, code=300 at   %SRR0: ...

this is an iMac (old blue bubble machine) 4Gb hd, 160Mb ram 233Mhz PPC

---

