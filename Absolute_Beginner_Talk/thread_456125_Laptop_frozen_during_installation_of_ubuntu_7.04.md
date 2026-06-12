---
title: "Laptop frozen during installation of ubuntu 7.04"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by fengjing99 on 2007-05-27
Compaq Presario V6110US laptop was frozen during the first-time start-up/install of ubuntu 7.04.
The computer specifications are:
AMD Turion 64x2 TL-50 1.6GHz
100G Hard disk
1.25GB Memory DDR2-667 (1x1GB + 1x256MB)
nVidia GeForce GO 6150 video card
I checked the BIOS setting, but I have no option to change. I tried 32bit and 64bit version of 7.04. Both gave weird lined gray frozen screen after passing some tests. The CDs worked fine on other old computers.
Thanks for your help!
Feng

---

### Post by taurus on 2007-05-27
Sounds like it is having a little technical difficulty with your video/monitor.  Try using the alternate CD to install it.

---

### Post by fengjing99 on 2007-05-27
Taurus,
Thanks for your answer. When you talk about "the alternate CD", do you mean the same ubuntu 7.04 version but burned separately, or another version of ubuntu? Thanks again!
Feng

---

### Post by Brightbelt on 2007-05-27
Hi, On the main download page of this site, right where you choose your version of Ubuntu to install, there is a check box that says "Check here for alternate CD version".  Check that box, and then download Ubuntu. 

Basically it's a text install version of Ubuntu and not a LiveCD. The text install is very easy.

Good Luck!
Frank Bright

---

### Post by taurus on 2007-05-27
> **fengjing99 said:**
> Taurus,
Thanks for your answer. When you talk about "the alternate CD", do you mean the same ubuntu 7.04 version but burned separately, or another version of ubuntu? Thanks again!
Feng

Just scroll down from the link below and you will see an alternate CD versions for i386 & AMD64.  Personally, I would recommend you use i386 since more stuff is available for it.  And don't forget to burn it at a slow speed like 4x.

[http://ubuntu-releases.cs.umn.edu/7.04/](http://ubuntu-releases.cs.umn.edu/7.04/)

---

### Post by fengjing99 on 2007-05-27
Thanks Brighbelt and Taurus! I am trying the alternate CD.
Feng

---

### Post by fengjing99 on 2007-05-27
I installed the alternate CD without any problem during the installation. But the frozen gray screen came back when I restarted the computer. Does anybody have this problem?
Thank you for your help!
Feng

---

### Post by taurus on 2007-05-27
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
If you are not sure about a question, just use the default value.  And if **nv** driver doesn't work, run that command again (after booting into recovery mode) but this time, use **vesa** driver instead.

Reboot into normal mode with

```
shutdown -r now
```

---

### Post by fengjing99 on 2007-05-28
Thanks Taurus! Finally I installed Feisty Fawn and now I can log in without crashes any more. But the video driver still gave me trouble. I have changed the VESA driver to GeForce 6150 driver from restricted drivers manager. But my 1280*800 screen can only be set 1024*768 maximum. Any suggestions on this? Thank you very much!
Feng

---

### Post by taurus on 2007-05-28
What resolution you want to use?  You can add that resolution to /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```
(Scroll down until you get almost the the end where you see a bunch of lines with different resolutions.  Just the one you desire to the front of those.  Save the change and restart X with <Ctrl><Alt>Backspace.)

---

### Post by josel777 on 2007-06-07
I am having the same exact problem with my laptop (Compaq V6110US).

---

### Post by josel777 on 2007-06-09
I am also using the Alternate installation CD, but for some reason I am unable to resize the XP partition. I am getting the following message:
----------------------------------------------------------------------------------------------
The resize operation is impossible
Because of an unknown reason it is impossible to resize this partition.
Check /var/log/syslog or see virtual console 4 for details.
---------------------------------------------------------------------------------------------------

I have tried using partition magic and will not recognize any partition letters. Any help is most appreciated.

---

### Post by josel777 on 2007-06-13
I was finally able to install Ubuntu on my laptop. However, booting keeps on halting. I either get 3 or 12 bars before it freezes. 
I have tried the  NV and VESA drives without success. What else can I try?

Update: now the process bar on the Ubuntu booting screen fills up all the way, I then get a blinking _  on the left top corner and then screen goes black.

---

