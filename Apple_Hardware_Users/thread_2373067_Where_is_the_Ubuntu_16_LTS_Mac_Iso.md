---
title: "Where is the Ubuntu 16 LTS Mac Iso ?"
date: 2017-10-02
forum: Apple Hardware Users
---

### Post by adigma on 2017-10-02
Just fighting since days to get Ubuntu 16 LTS installed on my old mac book (intel cpu 2ghz, actually it should run on it) 

But non of the iso is accepted to be bootable on the mac.
It boots fine with tails, knoppix, and so on. But the Ubuntu iso doesn't work. 
it's not even recognized as a readable DVD after burning the iso. 
Neither the 32bit nor the 64 bit.

On this page I read if the iso doesn't work I should try the mac image.
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

But where is the mac image ?

Any other ideas how to make the ubuntu iso boot on mac ?

---

### Post by QIII on 2017-10-02
Moved to Apple Hardware Users for a better fit.

---

### Post by &amp;KyT$0P# on 2017-10-02
> **adigma said:**
> non of the iso is accepted to be bootable on the mac.
It boots fine with tails, knoppix, and so on. But the Ubuntu iso doesn't work. 
it's not even recognized as a readable DVD after burning the iso. 
Neither the 32bit nor the 64 bit.
Did you install [rEFInd]("http://www.rodsbooks.com/refind/") on your Mac?

---

### Post by Bucky Ball on 2017-10-02
Welcome. Your machine has an Intel CPU so the regular image *should* be fine.

[This any help]("https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0") to you? See the last step 7, 'Boot your system'. There might be some issues happening there?

And yes, try refind.

---

### Post by valvestate163 on 2017-10-08
Might not be relevant, but I had no problems dd'ing to an SD card and booting from that. I did not bother burning to disc. - mid-2011 MBA

---

### Post by kevin160 on 2017-10-08
[Ubuntu 15.04 on Mac Mini 2,1 with EFI boot (2007 Intel) - Ubuntu ...]("https://www.google.ca/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwiY3eq9v-LWAhXDh1QKHW6JCIIQFggmMAA&url=https%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D2287767&usg=AOvVaw2CxSEa0-T2exoox5C5ycit") if your Mac is early Intel.

---

### Post by capriotti-carlos on 2017-10-16
[valvestate163]("https://ubuntuforums.org/member.php?u=2079304"), hi. Looks like you've tried doing your homework and found the page 

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

where it stated that there is a mac iso. That is no longer the case and you can use one of the regular images BUT you will most likely need a hack: Your system has an Intel GPU that - in my experience with a Macbook Pro - does not play ball with Ubuntu's installer.

You will have to improvise a little, adapting instructions you can find here:

[https://orville.thebennettproject.com/articles/installing-ubuntu-14-04-lts-on-a-2011-macbook-pro/](https://orville.thebennettproject.com/articles/installing-ubuntu-14-04-lts-on-a-2011-macbook-pro/)

IMO, all you will need is the part where these commands are entered on grub:

i915.lvds_channel_mode=2 i915.modeset=1 i915.lvds_use_ssc=0

Alternatively, instead of those commands, you can try to use the option 

nomodeset

on grub. I know the page above refers to 14 LTS. It works the same on 16.

Other than that, I expect everything to work fine on your mac with Ubuntu 16 LTS. My wife's macbook pro 2011 is working fine. The only point to raise an eyebrow could be wifi: check if the installed drive works with both 2.4 and 5 GHz networks. If not, you will have to install other broadcom drivers.   

This depends on the chipset installed on that computer.

---

