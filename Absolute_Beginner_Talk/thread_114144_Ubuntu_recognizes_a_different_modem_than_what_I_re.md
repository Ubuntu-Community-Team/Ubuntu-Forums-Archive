---
title: "Ubuntu recognizes a different modem than what I really have."
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by mrfixer27 on 2006-01-07
:confused: Ok I am very new at Linux. I am sick of windows and got myself a copy of Ubuntu. I ran the live CD and liked what I saw. I had some problems with monitor resolution (can only get 640x480) and no internet connection. I have read a lot of stuff in this forum and though it is probably staring me right in the face, I seem to be ignorant of any answers. I finally concluded that perhaps  there are limitaions to what is available and what can be done on the live CD and that maybe I would need to just install Ubuntu. So I opted to install and keep Windows 98SE. I found the installation a little complicated as I have never been introduced to Linux before and have grown with Windows from the 3.1 era through XP SP2. Anyway I worked my way through it and had 2 problems 1 having to do with syncronizing the clocks and 2 could not connect to the internet to download some packages. After the install everything came up looking good so I looked in the device manager and noticed that Ubunto says that I have a Lucent Winmodem while Windows claims that I have an Agere Systems PCI Softmodem. I am quite convinced that Windows is correct because I can connect from there. I believe that my monitor resolution problems will be solved once I can get on the internet and find the proper drivers. I also have problems with some software not working at all which I believe is because it was never really installed because of no internet connection. Could someone please help me figure out how to force Ubunto to correctly recognize my modem and get me connected to the internet?

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=mrfixer27]:confused: Ok I am very new at Linux. I am sick of windows and got myself a copy of Ubuntu. I ran the live CD and liked what I saw. I had some problems with monitor resolution (can only get 640x480) and no internet connection. I have read a lot of stuff in this forum and though it is probably staring me right in the face, I seem to be ignorant of any answers. I finally concluded that perhaps  there are limitaions to what is available and what can be done on the live CD and that maybe I would need to just install Ubuntu. So I opted to install and keep Windows 98SE. I found the installation a little complicated as I have never been introduced to Linux before and have grown with Windows from the 3.1 era through XP SP2. Anyway I worked my way through it and had 2 problems 1 having to do with syncronizing the clocks and 2 could not connect to the internet to download some packages. After the install everything came up looking good so I looked in the device manager and noticed that Ubunto says that I have a Lucent Winmodem while Windows claims that I have an Agere Systems PCI Softmodem. I am quite convinced that Windows is correct because I can connect from there. I believe that my monitor resolution problems will be solved once I can get on the internet and find the proper drivers. I also have problems with some software not working at all which I believe is because it was never really installed because of no internet connection. Could someone please help me figure out how to force Ubunto to correctly recognize my modem and get me connected to the internet?[/QUOTE]
They may actually mean the same thing.  Agere is a spinoff company of Lucent.  And generally, Winmodem == sowftware driven modem (softmodem).

Not sure about your modem drivers, but you might just need to adjust your xorg settings to get the resolution you want.  What kind of video card do you have?

---

### Post by mesocool on 2006-01-08
[QUOTE=mrfixer27]:confused: Ok I am very new at Linux. I am sick of windows and got myself a copy of Ubuntu. I ran the live CD and liked what I saw. I had some problems with monitor resolution (can only get 640x480) and no internet connection. I have read a lot of stuff in this forum and though it is probably staring me right in the face, I seem to be ignorant of any answers. I finally concluded that perhaps  there are limitaions to what is available and what can be done on the live CD and that maybe I would need to just install Ubuntu. So I opted to install and keep Windows 98SE. I found the installation a little complicated as I have never been introduced to Linux before and have grown with Windows from the 3.1 era through XP SP2. Anyway I worked my way through it and had 2 problems 1 having to do with syncronizing the clocks and 2 could not connect to the internet to download some packages. After the install everything came up looking good so I looked in the device manager and noticed that Ubunto says that I have a Lucent Winmodem while Windows claims that I have an Agere Systems PCI Softmodem. I am quite convinced that Windows is correct because I can connect from there. I believe that my monitor resolution problems will be solved once I can get on the internet and find the proper drivers. I also have problems with some software not working at all which I believe is because it was never really installed because of no internet connection. Could someone please help me figure out how to force Ubunto to correctly recognize my modem and get me connected to the internet?[/QUOTE]

Yea, modem issue is annoying.. After I install different version of Ubuntus for several times, I find that you need 3 packages in order to connect to internet via soft modem. First of all, I think we got the same modem.

Then, you might want to download 3 packages from [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) (It took me a lot of time to find these packages because they are not initially added to the install CD).

They are module-assistant_0.9.5ubuntu1_all.deb, 

module-assistant_0.9.5ubuntu1_all.deb, sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb and sl-modem-source_2.9.10+2.9.9d-6ubuntu1_i386.deb

install them and try the tutorial from [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

I think it should be working after this. That's what I did.

Gook luck..

---

### Post by mesocool on 2006-01-08
finally, got them again.. hard to find.

1.  [http://archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.9.5ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/m/module-assistant/module-assistant_0.9.5ubuntu1_all.deb)

2. [http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.10+2.9.9d-6ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-source_2.9.10+2.9.9d-6ubuntu1_i386.deb)

3. [http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sl-modem/sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb)

You might want to keep them in case some day you want to reinstall your system..

Good Luck.. :rolleyes:

---

### Post by jefri_surya on 2006-01-08
Hi guys,
 If you have a problem with your winmodem, who use connexant or another chipset you can try to visit [http://www.linuxant.com/drivers/hsf/full/downloads.php]("http://www.linuxant.com/drivers/hsf/full/downloads.php").
 There's a lot of driver for another distro and support for ubuntu 5.10 winmodem driver. Happy surfing the net with ubuntu.:D

---

