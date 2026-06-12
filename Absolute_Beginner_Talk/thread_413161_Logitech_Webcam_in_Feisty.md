---
title: "Logitech Webcam in Feisty"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by DarkAngel5745 on 2007-04-18
[COLOR="Magenta"][FONT="Comic Sans MS"][SIZE="1"][B][CENTER]How do i get my webcam to work in Feisty?
 I'm not sure what all you need 
so just tell me everything you need 
and i will tell you as much as i can. 
Thanks.

~*_*~[/CENTER][/B][/SIZE][/FONT][/COLOR]

---

### Post by pragmatine on 2007-04-18
if you don't provide any details how can we help?

---

### Post by Buffalo Soldier on 2007-04-19
Go to the terminal and type:```
lsusb
```
It should list all the detected USB devices. Here's an example of my lsusb print out.

```
~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 001: ID 0000:0000
```

---

### Post by loell on 2007-04-19
my logitech webcam is detected in fiesty, yet another example.


```
lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:0928 Logitech, Inc. Quickcam Express
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
loell@loell-desktop:~$ 

```

---

### Post by DarkAngel5745 on 2007-04-22
lsusb
Bus 004 Device 003: ID 13b1:000d Linksys 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:0928 Logitech, Inc. Quickcam Express
Bus 001 Device 001: ID 0000:0000  


That is that is showed. How do i get the cam to work let to take pic.s and to use on messengers?

~*_*~

---

### Post by loell on 2007-04-22
install camorama or xawtv they are known webcam applications , it can show and record your webcam, and take pictures too.
you can also go to youtube and try to record from your webcam ;)


known messengers that support webcams are

-specific messenger

     **amsn **- msn messenger
     **gyachi **- yahoo messenger

-all purpose messngers

       **kopete **- KDE/ Kubuntu all purpose messenger
              supports yahoo and msn webcam.
      ** openwengo **- Qt/KDE all purpose messenger

-default

       **Ekiga **- installed by default in ubuntu, supports voice and video - a voip/voim application

---

### Post by DarkAngel5745 on 2007-04-22
[CENTER][B][FONT="Verdana"][SIZE="1"][COLOR="Magenta"]Thanks!
^_^

~*_*~[/COLOR][/SIZE][/FONT][/B][/CENTER]

---

### Post by DarkAngel5745 on 2007-04-26
[CENTER][COLOR="Magenta"][B][SIZE="1"]I'm sorry to bug you guys again,
but i install all the things you said
and i couldn't figure out how to do webcam on gaim.
Is there a way to?

~*_*~[/SIZE][/B][/COLOR][/CENTER]

---

### Post by nalmeth on 2007-04-26
This is the page you are looking for DarkAngel:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

GAIM doesn't support webcams yet.

---

### Post by Bloch on 2007-04-26
I installed camorama and then plugged in the webcam, turned on camorama and was surprised to see it working straight off.

I checked Ekiga and the webcam also works there, meaning I could see my room through it. But I haven't tested Ekiga with a video call (I'll have to look into that and see how Ekiga can work with a friend who has a windows machine.)

It's a pity skype doesn't support video calls.

---

### Post by nalmeth on 2007-04-26
Cool, my webcam didn't work automatically. The EasyCam program is pretty useful in that it searches for and installs the right driver for the camera.

And yeah, as I understand, Ekiga can work with Microsoft NetMeeting or something like that.

If you're looking for a video conferencing solution between Windows/Mac/Linux, OpenWengo might be the way to go. 

[http://www.openwengo.com/](http://www.openwengo.com/)

---

### Post by loell on 2007-04-26
or convice your freind to use ekiga for windows :)

[http://www.gnomemeeting.org/index.php?rub=5&path=windows/windows]("http://www.gnomemeeting.org/index.php?rub=5&path=windows/windows")

---

### Post by DarkAngel5745 on 2007-04-29
I would like a program that i talk on msn or yahoo and webcam. Do you know of any?

~*_*~

---

### Post by loell on 2007-04-29
it has already been suggested in the first page on this thread,

gyachi - yahoo client with webcam and voice chat -- [http://gyachi.sourceforge.net]("http://gyachi.sourceforge.net")

amsn - msn client with webcam -- to install   in the terminal ```
sudo apt-get install amsn
```
 or in applications menu --> add/remove programs --> search for amsn--> check it--> then apply to install

for yahoo voice calls,you can use ekiga with these instructions [Ekiga call to yahoo messenger]("http://ubuntuforums.org/showthread.php?t=414121&highlight=gtalk2voip")

---

### Post by penno on 2007-05-25
Hi guys

ANyone been able to get the Express's resolution up to 640x480? Mine will only go to 352x288, but the box says it should do 640x480? Any clues? Or is the box lying? ^_^

---

