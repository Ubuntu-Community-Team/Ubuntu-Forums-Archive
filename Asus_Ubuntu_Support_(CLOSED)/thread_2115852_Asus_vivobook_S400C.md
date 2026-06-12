---
title: "Asus vivobook S400C"
date: 2013-02-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ZefQ on 2013-02-14
So i bougth a S400C a couple of month ago and replaced windows with ubuntu, but there are some problems so i thougt i would start a thread and see if there are any other vivobook user out there that have solved some of the issues i have or help others.

Brightness
Ubuntu 12.10: fixed by installing a newer kernel and adding "acpi_osi=" as boot parameter
Ubuntu 13.04: works out-of-the-box

Mouse
Mouse kind of works out-of-the-box bout not all the multitouch features
i used the work-around from [zenbook]("https://help.ubuntu.com/community/AsusZenbook#Touchpad") and added entry for palm detection as a "autostart" script

```
#Palm detection
synclient PalmDetect=1
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Palm Dimensions" 4 1        

# higher sensitivity   
synclient FingerLow=1 FingerHigh=12 # so it wont complain about the next line
synclient FingerLow=9 FingerHigh=12

# faster speed and acceleration
synclient MinSpeed=1.5 MaxSpeed=3.5 AccelFactor=0.1

# 2 fingers scroll (can be also enabled in System Settings)
synclient VertTwoFingerScroll=1 HorizTwoFingerScroll=1

# faster coasting
synclient CoastingSpeed=10

# enable tap to click (2 fingers for middle click, 3 fingers for right click)
synclient TapButton1=1 TapButton2=3 TapButton3=2

# continue dragging movement when reaching the edge of the touchpad
synclient EdgeMotionMinZ=30 EdgeMotionMaxZ=40 EdgeMotionMinSpeed=100 EdgeMotionMaxSpeed=400 
```

Wifi
It works but not realy... terroble speed and range, if someone has a solution for this i would be mutch obliged as it is now i have to use a usb adapter

Bluetooth
Cant get it to work at all

Thouse are the things I can remember, so if someone has a sulotion for bluetooth and wifi please let me know

---

### Post by ehijon on 2013-04-01
Hi ZefQ, I bought a similar ultrabook (Vivobook s300ca) and I'm waiting it. The hw is the same so I'm in your same conditions. 
My idea is to install ubuntu on that but I can work without wifi :(
I'm new with linux and I don't know how to solve this, but I hope to find the same answers!

---

### Post by ZefQ on 2013-04-03
Hello ehijon!

So far i have tried every new kernel and every workaround i can find with out any success, but i will make sure to post an update if and when i find something that works

---

### Post by Omizuk on 2013-05-12
Hello,

I have also recently purchased an ASUS S400C and I would like to install Ubuntu on it. Would you recommend me to install the Ubuntu 12 or 13 on it? 

I have some experience in Ubuntu but not enough to tackle by myself too many problems and I need Linux on it in for study purposes..

---

### Post by cdoebbler on 2013-05-25
I also tried installing 12.04, 12.10, 13.04, and 13.10 (which is beta) and nothing worked. I am trying a dual boot install--so keeping Windows 8--but can't seem to get the computer to boot from a USB or DVD to do s clean install and using Wubi it installs but does not run from the dual boot (I think windows not Grub) screen. 

Note that we have another tread going about is here: [http://ubuntuforums.org/showthread.php?t=2146936&page=3]("http://ubuntuforums.org/showthread.php?t=2146936&page=3")

---

### Post by davibarreira on 2013-06-24
I'm having the exact same problem. Did anyone figure how to fix the wifi range?

---

### Post by ZefQ on 2013-07-18
No sorry I havent been able to get this to work. I have also stoped trying to find a sulotion and my asus has been transformed from a laptop to a desktop...

---

### Post by herrwinkler on 2013-07-20
> **ZefQ said:**
> No sorry I havent been able to get this to work. I have also stoped trying to find a sulotion and my asus has been transformed from a laptop to a desktop...


The latest mainline kernel fixed the Wifi issue.

---

### Post by ZefQ on 2013-07-20
really? have to check when i get home in a couple of days. can you give me version so things havent changed when i get home?

---

### Post by ARDPCLD on 2013-08-02
Hi,
I´m new in this forum and just bought a Asus vivobook S300ca. I have already installed dual boot with windows 8 and ubuntu 13.04. Every thing was working fine but I found the same problem with the wi-fi range. [COLOR=#000000]Did anyone figure how to fix this? The newest kernel really fixed it? 
Thank you[/COLOR]

---

### Post by l-f-kempe on 2013-08-10
Yes i can confirm that the latest kernal solves the issue, kernels that i have tried and know to work is, [3.10.5]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.5-saucy/") and [3.11-rc4]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc4-saucy/")

---

### Post by ARDPCLD on 2013-08-12
Great! Thanks!! 
I installed the 3.10.5 version and the wi-fi interface is working fine now!

---

