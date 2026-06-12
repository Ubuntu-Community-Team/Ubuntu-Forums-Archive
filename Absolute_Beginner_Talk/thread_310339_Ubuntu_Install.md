---
title: "Ubuntu Install"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by LORD_EC on 2006-12-01
This is my problem..

I have my windows XP on my root drive(C drive,9.30 GB).
And four more partitions D,E,F,G..
I tried installing ubuntu 5.04 in drive G (9GB)..Ubuntu got installed but at the same time i was not able to boot through my window XP..I guess its boot loader got overwritten.

Please help me what shud i do to install ubuntu with no problem.I have alreay tried installing it hundreds of times..
please help

Im a noob..please forgive me incase of mistakes..
reply fast

---

### Post by RMorris78 on 2006-12-01
So you mean that you cannot boot to windows xp, but you are booting to ubuntu fine through the GRUB Bootloader?

---

### Post by seshomaru samma on 2006-12-01
Do you mean that when you boot the computer , it went directly to Windows or directly to Ubuntu ?
If it went directly to to Ubuntu , you need to change your Grub menu - thats the menu that should appear when the computer boots which will allow you to chose which OS to boot into.
If it boots into Windows then it probably means that when you installed Ubuntu , you choose the wrong installation path for the Grub menu . It should be installed to the MBR which is in the begining of the disk.
Please tell us which one it is so we can help you further

---

### Post by ciscosurfer on 2006-12-01
> **LORD_EC said:**
> This is my problem..

I have my windows XP on my root drive(C drive,9.30 GB).
And four more partitions D,E,F,G..
I tried installing ubuntu 5.04 in drive G (9GB)..Ubuntu got installed but at the same time i was not able to boot through my window XP..I guess its boot loader got overwritten.

Please help me what shud i do to install ubuntu with no problem.I have alreay tried installing it hundreds of times..
please help

Im a noob..please forgive me incase of mistakes..
reply fast[This link should help you out]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") :D

---

### Post by LORD_EC on 2006-12-01
Ya..i cant boot through windows.but ubuntu is working..
Can you tell me what should be the location of ubuntu and windows in context to my drives..
I hve my XP on C drive and i tried install ubuntu on G..

Also can you tell me how can i install it from scrap..
thnks in advance.

---

### Post by ciscosurfer on 2006-12-01
> **LORD_EC said:**
> Ya..i cant boot through windows.but ubuntu is working..
Can you tell me what should be the location of ubuntu and windows in context to my drives..
I hve my XP on C drive and i tried install ubuntu on G..

Also can you tell me how can i install it from scrap..
thnks in advance.Check my post above. :D

---

### Post by Mimsy on 2006-12-01
> **LORD_EC said:**
> Also can you tell me how can i install it from scrap..

Put in the live CD and reboot. Choose Start/Install Ubuntu from the menu that comes up; once you are at the Ubuntu desktop, couble-click the install icon on the dekstop. during the install it reformats your harddrive, which leads to a clean installation, "from scrap".

Hope this helps. :)

/Mimsy

---

### Post by LORD_EC on 2006-12-01
I remember it asked me where to install MBR,then i gave it a path where i installed my ubuntu and that is "G drive"..

and after that i got two options in the beginging for OS selection and from there 
i was able to go into ubuntu but not in window..window was unable to boot..

---

### Post by LORD_EC on 2006-12-01
> **Mimsy said:**
> Put in the live CD and reboot. Choose Start/Install Ubuntu from the menu that comes up; once you are at the Ubuntu desktop, couble-click the install icon on the dekstop. during the install it reformats your harddrive, which leads to a clean installation, "from scrap".

Hope this helps. :)

/Mimsy


but after that how can i install my windwos ???
shud i install window on root or ubuntu on root ??

---

### Post by ciscosurfer on 2006-12-01
> **LORD_EC said:**
> but after that how can i install my windwos ???
shud i install window on root or ubuntu on root ??You should install Windows first, then Ubuntu.  Otherwise, Windows will eat your MBR with its bootloader (which you don't want -- but if you do it that way, then the link I provided before will help you out).

---

### Post by Mimsy on 2006-12-01
> **ciscosurfer said:**
> You should install Windows first, then Ubuntu.  Otherwise, Windows will eat your MBR with its bootloader (which you don't want -- but if you do it that way, then the link I provided before will help you out).

Absolutely. I thought you were talking only about ubuntu; my mistake. Listen to Ciscosurfer instead. :)

Windows does not play well with others.

/Mimsy

---

### Post by LORD_EC on 2006-12-01
I guess im doing mistake in mouting like
/boot
/swap


can anyone help me out abt the sequence.I wish i could meet all of professionals so that it wud be much easier..

---

### Post by LORD_EC on 2006-12-01
Does anyone kno the link where step by step installation procedure is given with Screeenshots.

---

### Post by seshomaru samma on 2006-12-02
if you reinstalling then when it asks you where to install Grub choose MBR
but you dont need to reinstall anything
post your grub.list here and we will help you
```
gedit /boot/grub/menu.lst
```
also post the output of this:
```
sudo fdisk -l
```

[this]("http://www.psychocats.net/ubuntu/installing") is an installation guide with screenshots

---

