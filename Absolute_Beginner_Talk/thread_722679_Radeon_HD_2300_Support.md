---
title: "Radeon HD 2300 Support?"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Cruciatum on 2008-03-12
How well is this graphics card supported in linux? I don't mean the 2400, I have the HD 2300 graphics card.

Through a bit of hard work, I've got desktop effects working, but apparently direct rendering is a no no for me, is there anything out there now or in the near future that give me some kind of support for my 2300?

I mean, I love Linux, but I need to get back to my gaming, I can only stop playing World of Warcraft for so long :)

---

### Post by Cruciatum on 2008-03-12
So I'll take that as a no :(

---

### Post by Rocket2DMn on 2008-03-12
Looking on ati's website for drivers at [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) I don't see specific support for the HD 2300 yet in linux, but hopefully they will release some soon.
How new is this card?

---

### Post by Cruciatum on 2008-03-12
Well, I got the laptop as a birthday present, back in september/october time, it was brand new then and top of the range I think, so it's got to be fairly new I suppose.

---

### Post by Rocket2DMn on 2008-03-12
OK, well if you're set on getting it to work, you can try googling around for some workarounds or hacks to get it to work with better functionality.  Such hacks would probably involved editing /etc/X11/xorg.conf or installing specific driver versions.

---

### Post by Cruciatum on 2008-03-12
> **Rocket2DMn said:**
> OK, well if you're set on getting it to work, you can try googling around for some workarounds or hacks to get it to work with better functionality.  Such hacks would probably involved editing /etc/X11/xorg.conf or installing specific driver versions.


Heh, I have a horrible trait of making my computer load to a fabulous blank screen when I do that, I guess I'll just wait. I've still got the house desktop to play my games on :)

I'm also seemingly unable to install Vista back again, though that's not too depressing :)

Thanks anyway for your help.

---

### Post by Rocket2DMn on 2008-03-12
Blank screens are annoying, but not so difficult to fix - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
good luck.

---

### Post by inyoka on 2008-05-13
I had a friend with an Acer Aspire 4710 and an ATi Radeon HD2300.  Hardy installs to a blank screen, but in addition to this I cannot Ctl+Alt F1 into terminal 1.  

I fixed it by installing a command line system (F4 at the boot screen), then once booted into the newly installed system I mounted the cd-rom with "sudo apt-cdrom add"  then "sudo apt-get update" && "sudo apt-get install ubuntu-desktop".  This gave me a system that still didn't have a GUI but at least the command line worked.  I then booted up with the 7.10 CD, mounted my hard drive "sudo mkdir /home/ubuntu/Desktop/hd" "sudo mount /dev/sda5 /home/ubuntu/Desktop/hd" and copied the system xorg.conf to the hard drives "sudo cp /etc/X11/xorg.conf /home/ubuntu/Desktop/hd/etc/X11/xorg.conf".  When I rebooted the login prompt was there and all was okay.

How you should try fixing it:  You could probably just install Hardy normally and then boot into the CD for Gutsy and copy the xorg.conf straight away, but I was worried by the lack of command line and didnt try this as I thought it might not work, and I had a deadline to get the laptop working

3D desktop, despite Hardy's, problems once you have copied the xorg.conf, you can enable 3D graphics through the restricted driver gui as usual and it works fine :)  If you have already got Gutsy installed do a dist-upgrade and you shouldn't get this problem (do not goto the Ati site for the driver, use the ubuntu repo's!!!!).  

Hope this helps someone.

---

