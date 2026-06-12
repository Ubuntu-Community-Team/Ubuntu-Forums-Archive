---
title: "Help! new video card, cant get in to fix it."
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by jadugartir on 2007-07-08
Well last night i installed my new Geforce 8600gt. Since then i cannot get into ubuntu because the "x-server failed to start." i assume i need to install a driver, but im gonna need help to do so as i am only familiar with the graphical interface of ubuntu, and only basic knowledge of terminal commands.

Here is a little breakdown of my hardware:
gigabyte nforce socket 775 SLI motherboard
p4 64 bit 3.0 ghz
1gig ddr2 ram
and the new ASUS EN8600GT beast of a video card.

and my software:
300gb IDE drive with ubuntu dapper (i bought the ubuntu book and it came with dapper,, i would not mind upgrading if someone can help me thru it without use of a graphical interface)
100gb IDE drive with windows XP (what im trying to never use again)

Before i updated the card i was running a radeon x1300. I had it fully configured in ubuntu and even had gotten games to work on it with wine. perhaps ubuntu is trying to run my new card on my old driver? please help me get my new setup running on ubuntu,, as of now the only way to run it is to use my live cd with safe graphics mode

---

### Post by reset3x on 2007-07-08
See here: [http://ubuntuforums.org/showthread.php?t=495300](http://ubuntuforums.org/showthread.php?t=495300)

---

### Post by steve.horsley on 2007-07-08
I believe the command you need is:
**sudo dpkg-reconfigure xserver-xorg**

Just accept defaults on anything you don't understand. Then 
**sudo /etc/init.d/gdm restart**

---

### Post by jadugartir on 2007-07-08
Ok according to that first link, i booted into recovery mode and did the dpkg-reconfigure xserver-xorg command. It didnt fix my xserver problem. im still getting the same thing.

So im going to try sudo /etc/init.d/gdm restart after im done and see if that fixes it. thanks, ill report back.

---

### Post by jadugartir on 2007-07-08
No luck. same results.

on a side note, now i cant get into windows either. i get the blue screen upon loading. kind of strange considering it worked fine at first

---

### Post by jadugartir on 2007-07-08
Anything else i can do? reconfiguring did not help. I know ubuntu is capable of running with my video card because the live cd will run in safe graphics mode... if i could at least get my ubuntu to that point, i could go from there to try and find a driver that will run my card.

---

### Post by reset3x on 2007-07-08
Go back into recovery mode and reconfigure xorg to use the vesa driver... That should get you back to your desktop... You're going to need the newer proprietary drivers for Ubuntu to run with any 8000 series vid card... The drivers that come with Ubuntu don't support it... Once you get back to your desktop I would suggest you install Envy to get your new drivers and reconfigure xorg for you....

Hope this helps..

---

### Post by koshari on 2007-07-08
boot into the live cd , mount the filesystem and copy the live sessions xorg.conf file over to the install and try booting with that.

---

### Post by steve.horsley on 2007-07-09
> **koshari said:**
> boot into the live cd , mount the filesystem and copy the live sessions xorg.conf file over to the install and try booting with that.

What an excellent idea! Why didn't I think of that?

---

### Post by forrestcupp on 2007-07-09
> **reset3x said:**
> Go back into recovery mode and reconfigure xorg to use the vesa driver... That should get you back to your desktop... You're going to need the newer proprietary drivers for Ubuntu to run with any 8000 series vid card... The drivers that come with Ubuntu don't support it... Once you get back to your desktop I would suggest you install Envy to get your new drivers and reconfigure xorg for you....

Hope this helps..

This is the easiest way to do it.  But I would get the proprietary drivers with the Restricted Drivers Manager that is included in Ubuntu.  There is no need to install Envy.  The key here is choosing Vesa for your video device.

---

### Post by reset3x on 2007-07-09
> **forrestcupp said:**
> This is the easiest way to do it.  But I would get the proprietary drivers with the Restricted Drivers Manager that is included in Ubuntu.  There is no need to install Envy.  The key here is choosing Vesa for your video device.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

