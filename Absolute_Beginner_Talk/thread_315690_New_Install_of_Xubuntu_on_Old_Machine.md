---
title: "New Install of Xubuntu on Old Machine"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by oleyeller on 2006-12-09
I am currently running Ubuntu on one of my machines.  I am a newbie, but I am really impressed.

I am looking at installing Xubuntu on an old machine (pentium, but running Windows 95 - poorly) - and it does not have the option in the bios to boot from a CD.  

Of course, I already have a live CD of Xubuntu Edgy, but I now need to create some sort of boot floppy so that I can do the install, since I cannot boot from the live CD on the old machine.

So here's what I am looking for:
Some step by stem instructions answering the question....
How do I create a boot floppy in Ubuntu that can be used to boot up the old machine and then run the Xubuntu live CD?  Can someone help me with some step by step instructions?  

I know that the live CD has SmartBoot Manager on it (I can see smb.bin), I just don't know how to create a boot floppy  with smb.bin on it.

Thanks

---

### Post by jorn on 2006-12-09
I did it once. Something like this:
Open terminal:
dd if=/media/cd/install/smb.bin of=/dev/fd0

---

### Post by goatflyer on 2006-12-09
First off, if there isn't enough ram on the old computer (>=128MB) then you will need the Xubuntu alternate CD, not the Desktop one.

2nd: you want SmartBootManager:  Get it here at:
  [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

you write it to floppy, boot your old computer with it, select CDROM boot, and boot the Xubuntu alternate CD (or any CD, like Puppy or DSL if you want).

You didn't give the specs of your old machine, but if its too small even for Xubuntu you could try Puppy...

---

### Post by oleyeller on 2006-12-10
Thanks - I have made made up a boot disk using SMB.  I'll download the alternate CD instead of the desktop if required, but I think the machine has 128MB of RAM.

I am set and I appreciate the quick answers.

---

