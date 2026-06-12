---
title: "Ubuntu on Transformer Pad Infinity TF700T"
date: 2012-07-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Zelbion on 2012-07-20
Is it possible to dual boot Ubuntu 12.04 LTS on the new Asus TF700T tablet (Ice Cream Sandwich OS) without losing any existing data on the tablet or voiding the warranty. Is there an "official and tested" way to do it? Thanks.

---

### Post by MefistoIV on 2012-07-29
> **Zelbion said:**
> [...]without losing any existing data on the tablet or voiding the warranty. Is there an "official and tested" way to do it?

I am also interested whether it's possible to install Ubuntu and I am searching for a good instruction to do it. Since a few days, the Boot Unlocker can be downloaded - but installing a second OS or other ROM on your device will definitely make you lose your warranty for that product.

Greetings and also thanks in advance!

---

### Post by kd5snu on 2012-07-31
I'm working on trying to port 12.04 to the TF700T. With any luck I'll be able to dual boot as well, and keep the old data. It's not an easy task, to be sure.

I'm not sure that my end goal will be Ubuntu. If it is, I want to try and strip as much of the fluff out of it as possible. True, this may be a quad-core machine, but I'm afraid the fluff will take too much processing power and take away from the feel of the machine.

---

### Post by Auctionedllama@gmail.com on 2012-07-31
I am very interested in installing Ubuntu as well. Is there any official developers working on this, like XDA?

---

### Post by knewbsauce on 2012-08-06
i have looked on XDA and no luck there i have ran the "linux installer" app on my infinity but that is not a true dual boot. it runs 12.04 on top of the ICS which like you all is not what i want to do, i want to dual boot on my infinity

---

### Post by pingaan on 2012-09-15
Any progress?

---

### Post by jaithehulk on 2012-09-17
This seems to be a good idea...I would like to install 12.04 on my samsung s3. Please keep posting ur results here ... :)

---

### Post by Dream91 on 2012-09-26
I am interested to install Ubuntu on Asus Transformer Pad Infinity TF700T too.

---

### Post by scampbell70 on 2012-10-10
I am wanting to do this with my Transformer Pad Infinity TF700T I want to replace my laptop with this tablet for work but I cant because of 1 application that I cant run on android but will run on Ubuntu.

---

### Post by haukew on 2012-10-21
Any progress, kd5snu?

---

### Post by kd5snu on 2012-11-30
> **haukew said:**
> Any progress, kd5snu?

Not yet. Class started for me and bogged me down. I'm going to give it a shot again in a couple weeks. I'll let y'all know what I come up with.

---

### Post by mJayk on 2012-12-08
oo I must keep watching this thread would be very good if I could get ubuntu on this little thing :)

---

### Post by snakerock on 2012-12-08
**There are two working ports of Ubuntu 12.04:**

_[http://forum.xda-developers.com/showthread.php?t=1988174]("http://forum.xda-developers.com/showthread.php?t=1988174")_ and _[http://forum.xda-developers.com/showthread.php?t=1988174]("http://forum.xda-developers.com/showthread.php?t=1988174")_
First is installed to the /data/ubuntu/ directory in internal tablet memory (personally I use this), second is installed to external SD-card connected to the Dock`s cardreader.

Haven`t tried the second port, but the first runs wonderful! It supports practically everything (!) since all vital packages have armhf-versions. Veery little and not serious lags of interface.

**But there are two problems:**

1. With the first port Ubuntu doesn`t find wi-fi APs (for me). Solution is to connect to your known APs as to hidden wireless networks - after that internet works fine.
2. I can`t change the DPI of the screen. Infinity Pad has really great resolution for tablet, but Ubuntu uses default 96 dpi instead of real 220 that makes interface elements too small. I have tried almost everything to change it: reconfigured Xorg.conf, called "xrandr --dpi 220", changed Font Scaling in environment configurations, but it doesn`t enlarge controls...

**Can anybody advise how to change the DPI in Ubuntu 12.04? I can tell more about failed tries and show my Xorg.conf and Xorg log.**

---

### Post by ftwlol on 2013-02-21
[COLOR=#000000][FONT=Verdana]Step by step process for install ubuntu 12.10 on my Asus Infinity TF700T[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 1: Download these files and save them into your computer: [COLOR=#336699]tf700-rootfs-0.7.1.tar.lzma[/COLOR] (667Mb) and [COLOR=#336699]boot_installer-0.7.1.1.zip[/COLOR] (11 Mb). Just put them in a directory you can easily find and access; there’s no need to extract them.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 2: Connect your device  to your computer using the USB cable and copy the packages into the root  directory of the device’s internal memory. After that disconnect your  device and turn it off.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 3: Boot it into recovery mode and flash *boot_installer-0.7.1.1.zip* . You need to choose a kernel at this point. While all of them are supposed to work, the most recommended is 1.3-1.8.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 4: Once the installation is complete, wipe cache/dalvik.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 5: Turn your device off  again but this time connect the keyboard dock and boot it into recovery  mode. Since you have just installed a new boot loader, you must be  seeing penguins while the device loads. After a short while, you will  see four options: Android, Linux, Install and Shell.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 6: You still need to install so choose press “I” on your keyboard. The device automatically searches for *tf700-rootfs-0.7.1.tar.lzma*. You need to choose the Ubuntu image size and press “Yes” to confirm.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 7: It will take several  minutes to complete the installation process. Refrain from touching  anything on your device until everything is done to avoid messing up the  process.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Step 8: Once the installation  is complete, press any key on your keyboard to return to boot options.  Press “1&#8243; to boot Ubuntu 12.10; the default password is “ubuntu” but you  have to change it to your own password for security reason.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]This is just one of the ways to install Ubuntu on Pad Infinity TF700. We advise you to visit [COLOR=#336699]XDA devs forums[/COLOR] to learn other ways to flash this custom OS.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by nights815 on 2013-03-28
> **snakerock said:**
> **There are two working ports of Ubuntu 12.04:**

_[http://forum.xda-developers.com/showthread.php?t=1988174](http://forum.xda-developers.com/showthread.php?t=1988174)_ and _[http://forum.xda-developers.com/showthread.php?t=1988174](http://forum.xda-developers.com/showthread.php?t=1988174)_



They are the same.. Was this accidental?

---

