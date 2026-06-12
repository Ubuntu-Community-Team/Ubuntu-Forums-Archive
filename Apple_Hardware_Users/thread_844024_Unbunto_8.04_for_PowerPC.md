---
title: "Unbunto 8.04 for PowerPC"
date: 2008-06-29
forum: Apple Hardware Users
---

### Post by eaglewealth on 2008-06-29
Hi

I do have Unbunto 8.04 Live i386 CD.  Does it really able to boot on G4? 

I'm a newbie on Unbunto and I had been thro9ugh a lot of linux distro on pc over the years.  I'm not an advanced but am trying to figure out how to install application after downloading programs off the internet.

Unbunto 7.04 Live CD PPC won't run on Ibook G3 which is a pity. 

Any suggestion?

Regards

Jennifer Henry
Australia

---

### Post by ditsch on 2008-06-29
> **eaglewealth said:**
> I do have Unbunto 8.04 Live i386 CD.  Does it really able to boot on G4?
No, you will have to pick the Hardy PPC CD from there: [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

---

### Post by stream303 on 2008-06-29
Other tips:

Burn the installer image as an iso, and not just copied over to a CD-R.  Don't use CD-RW.  Burn at a low speed, low enough for your cdrom to handle.  Many suggest 2x or 4x for those older cdrom drives in the G3's.  Boot by holding down the "C" key upon powerup, or hold down the "C" key *very quickly* after powerup, and hold it long enough to ensure that it is booting from the cdrom.

If your machine doesn't have at least 256mb of ram, use the "alternate" installer image that uses a text/ncurses interface which doesn't need so much ram to just install, and will still give you a full gui afterwards.

Search out other ibook owner threads as you may have to manually edit some files, like /etc/X11/xorg.conf specifically for your machine.

These two faqs should help get you started:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by eaglewealth on 2008-06-29
Hi

Thanks Ditsch for the tip, I will look into the link you provided me and I will definetely will download it as Powerpc version. iso and hopefully will work.:)

Stream303 - Yes I was using CD-R for burning ISO Linux Distros. I guess it was the wrong Unbunto version that designed for pc as Ditsch told me to download as powerpc.  :)

By the way the firefox need adobe flash player and if I download it, do you know how to install the flash player for firefox? :cool:

---

### Post by ditsch on 2008-06-29
The Adobe flash player won't work on PowerPC, sorry. You have to use a free alternative like swfdec or Gnash.

---

### Post by Old_Grey_Wolf on 2008-07-05
> **ditsch said:**
> The Adobe flash player won't work on PowerPC, sorry. You have to use a free alternative like swfdec or Gnash.

The only reason my grandchildren won't use an old PPC I have is because they cant play the Flash games on Cartoon Network. Does the swfdec work with those games? The last time I tried gnash it didn't work. 

Thanks

---

### Post by stream303 on 2008-07-06
For a flash-game machine, Ubuntu PPC (or any Linux PPC distro) makes a poor choice based mostly on the fact that PPC support for flash from the commercial entities is not forthcoming.

I wouldn't wait for Intrepid either - while one of it's objectives is to have better flash support, it is unlikely that the commercial entities will do anything different for PPC.

---

