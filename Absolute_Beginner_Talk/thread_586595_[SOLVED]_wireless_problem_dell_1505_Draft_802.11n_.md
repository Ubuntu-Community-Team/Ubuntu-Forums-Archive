---
title: "[SOLVED] wireless problem dell 1505 Draft 802.11n Rev 2.0"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by mate84 on 2007-10-22
I think I'm the newest on ubuntu and I don't know what can I do with my wireless, because ti isn't working. I use ubuntu 7.10 on my external hard drive. My laptop is a dell vostro 1000 with Dell Wireless 1505 Draft 802.11n WLAN Mini-Card Rev 2.0 Chipset: BCM4328. I have allredy searched for this in this forum and I found this: [http://ubuntuforums.org/showthread.php?t=572335](http://ubuntuforums.org/showthread.php?t=572335) , but how can I do it and install this or is this the right way? I don't know anything about this. Please somebody help me!

---

### Post by Pumalite on 2007-10-22
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

---

### Post by maximilianhauser on 2007-10-22
Hello,
I'm  from Germany and my English is not very good, but I will try to help you. My Laptop has the same Wlan Chipset.
At first you have to install ndiswrapper. This is described here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Configure after installing the ndiswrapper with the windows2000 wlan driver from this: [ftp://ftp.hp.com/pub/softpaq/sp34501-35000/sp34510.exe](ftp://ftp.hp.com/pub/softpaq/sp34501-35000/sp34510.exe) site. 

Don't forget ```
sudo ndiswrapper -m
``` and ```
sudo modprobe ndiswrapper
```

---

### Post by mate84 on 2007-10-23
Thanks the fast reply! I think I installed ndiswrapper, but I'm not sure. How can I install it normali and where can I find: my wireless driver, xxx.sys, xxx.inf, because I find just .exe file. I hope somebody can understand my English and can help me (please)!

---

### Post by mate84 on 2007-10-23
Sorry I forget this things. I got error1 and 2 for the ndiswrapper and what does it mean: uname. I know that I hawe lots of problem, but please....

---

### Post by mate84 on 2007-10-23
I am an absolute beginner on ubuntu and I don't know how can I do/install this things and I'm really interest for this, but first of all I need the wireless conection!!! Please somebody give me a specification!

---

### Post by Pumalite on 2007-10-23
I have a collection of links here. Take a look and see if you can find your answer:

[https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9](https://help.ubuntu.com/community/RadeonDriver#head-363954c23963c39e3a7d633c7ad8667c8e0949c9)
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by mate84 on 2007-10-24
I can't make it. Finally I get this: no wireless extension. And now?

---

### Post by piresloh7 on 2007-10-24
hello, 
i think this will be helpful.
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

thx

---

### Post by mate84 on 2007-10-26
Thanks this great reply, but before I started to use it, I found an other one and its working:). I used this one with step 2d  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
The connection just 4% and  it' show just 2 networks, but when I use window$ the connection 100% and I can find at least 4 networks. How can I get higher connection %? What kind of program can I use?

---

### Post by mate84 on 2007-10-26
Ahhh I forget it: and in the restricted drivers manager is not show me any wireless driver. It's normal?

---

### Post by analfabeta on 2007-10-29
Hi, i have this problem too. Nothing in restricted drivers. 
My wireless is Dell Wireless&#8482; 1505 - Broadcom BCM4328 (rev 03). Not work with bcm43xx driver and i try ndiswrapper, but doesnt work. I'll try again this night.

---

### Post by mate84 on 2007-10-30
Hi analfabeta,
Did you find, the right driver? Have you tryed this with step 2d [https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff) ? It's working for me with this, but is not perfect.

---

### Post by ijn on 2007-11-14
you guys remind me myself 8 months ago:)
ok, im on a dell inspiron 1505/ 6400 US/Europe. my wireless card is a dell wireless mini card 802.11 draft n. 
the only way you can make your wireless card work is the ndiswrapper (last version 1.49) method. it works on feisty and gutsy with the windows driver R151517, (download it from dell driver support)

here is what to do and you should do it from terminal, it means that you will copy/paste some commands. do not freak out, just copy/paste and your machine will do the rest.

1)make a fresh install of ubuntu 7.10  AND  you should have at least internet connection via dhcp (lan or modem). this howto may not work if you have tried before to settle up your wireless, cause im sure you messed up your distro. 

2)draft N is the fastest technology on wireless (up to 300mbps) from broadcom. the world even in W*****S it is not still updated to this. so the most you will get it will be 54mbps. it means that if u will make it with this howto your wireless will be known to your wireless router or modem as a draft G or lower. you can't do nothing if they don't implement the driver draft N to linux kernel, even than you should have a router draft N to profit of your dell wireless draft N up to 300mbps.

ok now just copy/paste on terminal as administrator. !!!THE COMMANDS ARE TYPED ONE BY ONE!! EVERY LINE IS A COMMAND!!! where it says pass..... write down your ubuntu password. after every command hit ENTER. after the last command turn on the wireless key on your dell laptop and check if it is lighted.

sudo -s

pass:..........

echo blacklist bcm43xx >> /etc/modprobe.d/blacklist

wget [http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz](http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz)

tar -xzvf ndiswrapper-1.49.tar.gz

cd ndiswrapper-1.49

sudo apt-get update

apt-get install build-essential

apt-get install linux-headers-`uname -r`

sudo make unistall

sudo make

sudo make install

ls

unzip -a R151517.EXE

cd DRIVER

sudo ndiswrapper -i bcmwl5.inf

sudo ndiswrapper -l

sudo ndiswrapper -m

sudo modprobe ndiswrapper

:):):):):) this must be your face.
feedback me if you have any questions.
take care

---

### Post by st33med on 2007-11-14
[http://ubuntuforums.org/showthread.php?t=297092&highlight]("http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+e1505")
Try that link. Not sure if you have the right wireless card, but, it should work.

---

### Post by ijn on 2007-11-14
it's me again.
I forgot something very important.
after command: sudo make install
and before command:ls
go to dell web site and download dell wireless driver as you normally do it in W*****S.
download it in home folder. the last version should be R 151517.
then procced the rest of commands.

---

