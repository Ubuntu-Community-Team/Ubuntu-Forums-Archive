---
title: "i lost my x server"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by fwar on 2007-12-01
i need ur help coz this problem may stop me from transporting from windows 

when i use this (sudo dpkg-reconfigure xserver-xorg)

it says (package 'x-server' is not installed)

i used this (startx > startx.log 2>&1)

it says (fatal server error:
no screen found
XIO : fatal error 104(connection rest by peer) on x server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.)


plzzzzzzzzzzzz help me up

---

### Post by fwar on 2007-12-01
i need ur help but no one has looked to my post yet

---

### Post by overdrank on 2007-12-01
> **fwar said:**
> i need ur help but no one has looked to my post yet

Hi and welcome, can you give us some specifications on the system and what version you are installing, Feisty, gutsy?

---

### Post by fwar on 2007-12-01
gusty 

7.10

---

### Post by overdrank on 2007-12-01
> **fwar said:**
> gusty 

7.10

Ok could you tell us some specs on your system like video card and memory? Have you installed or are you trying the live cd?

---

### Post by fwar on 2007-12-01
my video card is mobility radeon x700

---

### Post by superyounan1 on 2007-12-01
interesting.

do you have internet access? try installing it```
sudo apt-get install xserver-xorg
```

---

### Post by overdrank on 2007-12-01
> **fwar said:**
> my video card is mobility radeon x700

Ok I am trying to help but I have asked several questions and you only respond to one of the questions. Have you installed Ubuntu, are you receiving any errors other that xserver not installed? Have you tried to boot to recovery mode and reconfigure xorg?

---

### Post by fwar on 2007-12-01
> **superyounan1 said:**
> interesting.

do you have internet access? try installing it```
sudo apt-get install xserver-xorg
```

the problem is i do not have  internet access by the cable what i have is internet by my mobile (am from Saudi Arabia) i am using USB to access the net (sorry for my bad English) 


i have the live CD is there any way to restore my x server with out internet or if i can access the net by my mobile i am using windows now

---

### Post by overdrank on 2007-12-01
> **fwar said:**
> the problem is i do not have  internet access by the cable what i have is internet by my mobile (am from Saudi Arabia) i am using USB to access the net (sorry for my bad English) 


i have the live CD is there any way to restore my x server with out internet or if i can access the net by my mobile i am using windows now

HI and if you have no internet connection then all you can do is reconfigure you xorg with the aforementioned command and choose vesa as the driver. ```
sudo dpkg-reconfigure xserver-xorg
``` If you get the same error from that command then I suggest that you check the cd for errors, and Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by fwar on 2007-12-01
> **fwar said:**
> i need ur help coz this problem may stop me from transporting from windows 

[I][U]when i use this (sudo dpkg-reconfigure xserver-xorg)

it says (package 'x-server' is not installed)[/U][/I]

i used this (startx > startx.log 2>&1)

it says (fatal server error:
no screen found
XIO : fatal error 104(connection rest by peer) on x server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.)


plzzzzzzzzzzzz help me up

i did this before

---

### Post by overdrank on 2007-12-01
> **fwar said:**
> i did this before

 Did you read the rest of my post!  then I suggest that you check the cd for errors, and Then you may want to do a checksum on the cd
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
__________________

---

### Post by fwar on 2007-12-01
ok i will but not now coz it is 1:52 AM i  am going to sleep i have work in the morning....

i will try these things tomorrow thanx for ur help 


i will come back

---

### Post by fwar on 2007-12-02
i am back as i said 

i have tried the solutions i could restore my x-server but i did not work well so, i formatted it (ubuntu) and i have reinstalled it again.

now i want the best way to install my ATI card drive with out losing my x-server

plz give me the best shortcuts to do that...

---

