---
title: "Have Modem"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by bobanshirl on 2006-07-13
I have at long last installed an external modem which was seen by Ubuntu,trouble is I did what it said by typing in sudo nano /etc/wvdial.conf have now got a window with 
[Dialer Defaults]
Modem=/dev/ttyS1
Baud=115200
Init1=ATZ
Init2=ATQ0 V1 E1 S0=0 &C1 &D2+FCLASS=0
ISDN=0

Modem Type=Analogue Modem
Phone=<Target Phone Number>
User Name=Your Login Name
Password.
              I do not know what or how to do next if some one could help me by saying type this and type that verbatum I would be eternally greatful,I would rather not be given a page to go to ie Ubuntu wikie but easy directions to how to type in my ISP details etc etc.Thanks a lot

---

### Post by editrix on 2006-07-13
I don't use the program, but either of these should help:

[http://wiki.linuxquestions.org/wiki/Wvdial](http://wiki.linuxquestions.org/wiki/Wvdial)
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)

---

### Post by bobanshirl on 2006-07-13
> **editrix said:**
> I don't use the program, but either of these should help:

[http://wiki.linuxquestions.org/wiki/Wvdial](http://wiki.linuxquestions.org/wiki/Wvdial)
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)
I did what you said and tried the first one.I managed to get the modem initialised but when I managed to get to the part that let me put in Phone number user name and password when I tried wvdial it said the number username and password were not recognised.On the Setting Up page I am afraid that is for you programmers and Ubuntu wizards it is totally alien to me.Like for eg remember to add your ISP DNS servers in the   then a big space and1./etc/resolv.conf file.Insert the line
         2. nameserver 196.25.1.11
unfortunately I didnt want directing to a wiki as they are totally unreadable for me and I reckon if the majority of buntu wizkids just wondered what it is like to be completely out of sinc.well thats another story

---

