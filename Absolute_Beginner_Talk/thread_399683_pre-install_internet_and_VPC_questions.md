---
title: "pre-install internet and VPC questions"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by mystically on 2007-04-02
Hi, I am very new to Linux and I have some pre-install Linux questions. I installed once almost messed up computer but I decided to give it one more try.

I how to install Linux on Virtual PC, but is it true all I have to do to remove Linux is press the remove button the VPC console?

I use internet pro/wireless ( the latest one on the table for intel wireless cards), Now I know I have very slow internet but will it connect? I use WLAN router and it's under a WEP key that I have to enter. Which step of the installation do I have to enter the key or I do that after installation. (Last time I tried this it didn't go on internet)

Here be my IP details from WINXP

IP: 192.168.1.2
Subnet Mask : 255.255.255.0
default gateway: 192.168.1.254
DNS: 192.168.1.254

I know there's a step in installation which detects network settings, If I type this manually then will it work? Don't forget I'm under usename and password.

Also when it asks for your IP when installing network manually do I type in public or private IP?

I understand that there will be a scratching looking GUI when installing under VPC can it be fixed by typing this?
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backupNote
sudo nano /etc/X11/xorg.conf
```
Then type CTRL+W type in DefaultDepth and click enter then on the number beside it change from 24 to 16
then type CTRL+O then type CTRL+X then type 
```
sudo reboot
```
That fix it?


That's all for now

Thanks

Another question does NAT ( shared network ) work in ubuntu? because I know internet will work on host computer.

---

