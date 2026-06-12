---
title: "Mac mini not booting live CD"
date: 2011-04-18
forum: Apple Hardware Users
---

### Post by kpgalligan on 2011-04-18
I have a mac mini.  Recent model (december 2010).  I burned 10.10 32bit (twice, actually), and a beta of 11.04.  The 10.10 would seem to get pretty far.  Booting into the linux CD, then I could hear it running for a while, but after a minute-ish, the screen was blank and nothing would happen.  I tried switching terminals (which fixed a problem I had on my windows PC and installing).  Nothing.

11.04 booted into a blinking cursor, but nothing else.

Currently I'm downloading the alternate CD to try that.

I've been using ubuntu for years now, but this is my first mac.  I bought it to compile/test some iOS stuff, but I figured it would make a decent box for home.

Anyway, please help.  It seems like either I'm using the wrong build, or this whole brand of CD's simply doesn't boot right.

---

### Post by Anon7-2521 on 2011-04-19
Try using a bootable usb as well. I had this same problem on my MBP and using both worked. Plug in the USB, put the CD in, hold alt, load the CD, it'll load the livedesktop for you.

---

### Post by kpgalligan on 2011-04-19
I used the alternate cd which "worked".  It looks like the system was installed.  However, i didn't want to install grub in case that would mess anything up.  rEFIt is installed and seems to work fine.  I think all I need is to get rEFIt to point at the ubuntu partition as well as osx.  thoughts?

---

### Post by Anon7-2521 on 2011-04-19
I have no idea. I don't use rEFIt. I have grub installed.

---

### Post by kpgalligan on 2011-04-19
I guess that's the question.  If I just install grub will that work OK?  Grub I'm used to.  Didn't know if that was OK on mac or whatever.  Things I've read implied that you needed rEFIt.

---

### Post by Anon7-2521 on 2011-04-19
As far as I understand, all rEFIt does is remove the need to hold down the alt key at boot. If ubuntu isn't showing up I'd follow the instructions on the rEFIt page. I don't think it would hurt to install grub, just make sure all your stuff is backed up just in case.

---

### Post by kpgalligan on 2011-04-20
Put grub on the root of the drive.  Now I get grub and linux starts loading, but then it just stays blank.

OSX still boots, though, which is nice.

---

