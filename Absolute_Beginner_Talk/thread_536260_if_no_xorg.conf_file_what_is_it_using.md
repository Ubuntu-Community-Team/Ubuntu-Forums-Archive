---
title: "if no xorg.conf file what is it using?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-08-27
i had this big struggle with my xorg.conf when i tried to add S-Video to it but it went all haywire even after doing sudo dpkg-reconfigure xserver-xorg i still couldn't get my xserver back up and running.  So i flat out deleted my xorg.conf file from command line and rebooted and everything was back to normal!  i am curious to know wat file it is using, here are the contents of etc/X11:

app-defaults             xkb                                             xserver
cursors                  xorg.conf.20070803204934                        Xsession
default-display-manager  xorg.conf.20070803204934_27.08.07_02:29:41\ PM  Xsession.d
fonts                    xorg.conf.20070803214731                        Xsession.options
gdm                      xorg.conf.20070803224708                        XvMCConfig
rgb.txt                  xorg.conf.20070803225033                        Xwrapper.config
X                        xorg.conf.20070826202912
xinit                    Xresources

is there a command i can type in the terminal that would tell me wat xorg file is in use?

Thanks, Alain

---

### Post by dwhitney67 on 2007-08-27
The xorg.conf file in use is located in /etc/X11.  But then with Ubuntu, maybe a copy is stuffed deep in the bowels of another folder.

If a file doesn't work, deleting it is not necessarily the best option.  Don't delete your /etc/X11/xorg.conf file!

---

### Post by Inxsible on 2007-08-27
> **S15_88 said:**
> i had this big struggle with my xorg.conf when i tried to add S-Video to it but it went all haywire even after doing sudo dpkg-reconfigure xserver-xorg i still couldn't get my xserver back up and running.  So i flat out deleted my xorg.conf file from command line and rebooted and everything was back to normal!  i am curious to know wat file it is using, here are the contents of [COLOR=Red]etc/X11[/COLOR]:

app-defaults             xkb                                             xserver
cursors                  xorg.conf.20070803204934                        Xsession
default-display-manager  xorg.conf.20070803204934_27.08.07_02:29:41\ PM  Xsession.d
fonts                    xorg.conf.20070803214731                        Xsession.options
gdm                      xorg.conf.20070803224708                        XvMCConfig
rgb.txt                  xorg.conf.20070803225033                        Xwrapper.config
X                        xorg.conf.20070826202912
xinit                    Xresources

is there a command i can type in the terminal that would tell me wat xorg file is in use?

Thanks, AlainYou do know that etc/X11 and /etc/X11 are two totally different entities. I hope that's just a typo. The xorg.conf file is in /etc/X11. Also when you do a sudo dpkg -reconfigure, it automatically creates a new xorg.conf file for you.

---

### Post by jordanmthomas on 2007-08-27
I believe recent versions of the xserver (7.3 and up?) can detect your hardware and automatically set itself up.  I know mine did on ArchLinux.  I ended making an xorg.conf anyway because I needed the Composite extension enabled.

So, short answer:  nowhere, it makes a new one.

---

### Post by S15_88 on 2007-08-27
yes i did mean the /etc/X11 and i deleted my xorg.conf file because i knew i had 5 backups in that folder!  and yes i know that when u do a sudo dpkg -reconfigure it creates a new one and that one didn't work even using generic vesa and it was a big mess so i deleted it hoping that when i rebooted it would use one of the old backup files and i presume it did but i would like to know which one so i can delete the rest make a backup of the current then rename the current to just xorg.conf then be on my way with attempting to set up my S-Video again.  I've read many threads and online guides about editing the xorg.conf to use S-Video but none have worked so far! anyone have their S-Video working that could share their xorg.conf file so i could take a gander and see if i could incorporate it into mine with some adjustments.

Thanks, Alain

---

### Post by forestpixie on 2007-08-27
I put my s-video settings in your other post, did you see that.

what graphics card do you have?

---

### Post by asmoore82 on 2007-08-27
[http://ubuntuforums.org/showthread.php?p=3259768#post3259768](http://ubuntuforums.org/showthread.php?p=3259768#post3259768)

---

### Post by S15_88 on 2007-08-27
i've got an Intel Corporation Mobile 945GM - VGA compatible, i'll admit right now i'm so lost i don't have a xorg.conf fiile.  

i had copied mine into a text document prior to making the S-Video changes and when i create a xorg.conf using that text, which worked yesterday, i reboot and it can't start the xserver.  I've tried just starting again doing a sudo dpkg -reconfigure but even when i use the VESA driver and reboot i get my log in screen but no desktop only a white screen.  i've had alot of trouble with my xserver when i first installed it and then again when i wanted 1440x900 resolution and now again with S-Video!  I need help haha or at least some guidance.  Thanks again for all the help.

Thanks, Alain

---

### Post by S15_88 on 2007-08-27
well i can deal with this so called auto detected hardware caffuffle for now but i need to get  S-Video working soon and just a last final question:  when i do 
> 
 sudo dpkg-reconfigure xserver-xorg

and select VESA and all the default settings then reboot it doesn't work!  wat am i missing! why does ubuntu hate my set up so much!  here is my lspci output:
> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)



Thank you very much everyone for all your help, Alain

---

### Post by dwhitney67 on 2007-08-27
I have come across two threads within the Ubuntu forum.  Try searching next time for an answer.

Anyhow, here are your choices for instructions:

1)  [http://ubuntuforums.org/showthread.php?t=281275](http://ubuntuforums.org/showthread.php?t=281275)

or

2) [http://ubuntuforums.org/showthread.php?t=282767](http://ubuntuforums.org/showthread.php?t=282767)

In the second Post, one person believes that the 915resolution package is needed, while in the first Post that is not the case.  I don't think it will hurt to try either one.  If I read it correctly,  Post #2 can be summarized as follows:

[FONT="Courier New"]Step 1:  sudo aptitude install 915resolution vbetool
Step 2:  sudo dpkg-reconfigure xserver-xorg
Step 3:  <reboot>[/FONT]

---

### Post by S15_88 on 2007-08-31
just wanted to let everyone know i got a new xorg.conf working and it's all good and i'm going to try again with the S-Video! i've read many people's xorg files and their descriptions of wat they did to get it to work so hopefully i'll have more luck this time.

thanks again to everyone that lent a helping hand, this forum is wicked!

Thanks, Alain

---

