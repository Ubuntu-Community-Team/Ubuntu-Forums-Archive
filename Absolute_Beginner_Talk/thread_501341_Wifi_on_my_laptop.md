---
title: "Wifi on my laptop"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by cellarmation on 2007-07-15
Hi real newbie question here. I have just installed Ubuntu 7.04 on a laptop i have just got off eBay.  I have a wireless card for it, but no wireless set up in the house yet. As i don't have wireless, i am not sure if the card works or is installed. How can i check to see if it works? Is installed?

Any suggestions would be good, i am talking real basics here :-P

---

### Post by Rovdjur on 2007-07-15
> **cellarmation said:**
> Hi real newbie question here. I have just installed Ubuntu 7.04 on a laptop i have just got off eBay.  I have a wireless card for it, but no wireless set up in the house yet. As i don't have wireless, i am not sure if the card works or is installed. How can i check to see if it works? Is installed?

Any suggestions would be good, i am talking real basics here :-P

Ubuntu does have a Hardware Profile built in! Simply go to it and check to see if it is registering the card or not!

Unfortunately, I do not know which menu it falls under, as my installation is currently MIA, but it shouldn't be too hard to find :)

---

### Post by overdrank on 2007-07-15
> **cellarmation said:**
> Hi real newbie question here. I have just installed Ubuntu 7.04 on a laptop i have just got off eBay.  I have a wireless card for it, but no wireless set up in the house yet. As i don't have wireless, i am not sure if the card works or is installed. How can i check to see if it works? Is installed?

Any suggestions would be good, i am talking real basics here :-P

Hi you can go to system, administration, network and see if the card is detected but as for working that is another issue that you need to have a  wireless network to verify. :o

---

### Post by cellarmation on 2007-07-15
On the list i have "Wireless Connection" - "Roaming mode enabled"

Im guessing thats a good thing :-)
Thank you.

Will be getting a wireless access point in a few days, so i will know for sure then.

---

### Post by MrMercutio on 2007-07-15
> **cellarmation said:**
> Hi real newbie question here. I have just installed Ubuntu 7.04 on a laptop i have just got off eBay.  I have a wireless card for it, but no wireless set up in the house yet. As i don't have wireless, i am not sure if the card works or is installed. How can i check to see if it works? Is installed?

Any suggestions would be good, i am talking real basics here :-P

You can go into the console, and enter the command:

> iwconfig

If you have a wireless card it should turn up there and give you lots of data, showing that it responds to management.

---

### Post by cellarmation on 2007-07-15
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


All good?

---

### Post by ugm6hr on 2007-07-15
> **cellarmation said:**
> eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


All good?

Sort of.  Yes the wifi card is detected. Unfortunately it's a Broadcom.

Keep this link on record - it will prove useful for when you get your access point:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by MrMercutio on 2007-07-15
Yes, all good. :) It shows up, which means it can be monitored by the system, which means it works. It's in managed mode, which is the normal mode. Access point is the network router you haven't accessed yet. When you can connect to the net, that will be filled.

---

### Post by cellarmation on 2007-07-17
Help!

Ok i have my wireless access point and i think i have set it up right. Things were very close to working at one point. and now i think they have gone from bad to worse. Orignially ubuntu wasnt detecting anything, and when i typed in the name to connect to, it would think about it for a bit then give up (using the little drop down menu in gnome) So i followed the link to 
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

and followed the first 2 steps and restarted (im using fiesty) it helped the situation, the bar was filled with a percentage signal of my wireless network. But i was still unable to connect to it, it would always fail.

Possibly quite stupidly i then went through the rest of the steps in the help thing, and now it doesnt even show up a wireless connections option. Help? What should i do?

---

### Post by cellarmation on 2007-07-17
oj i may have overreacted slightly and have gone for a fresh install. I will try again now :P

---

### Post by cellarmation on 2007-07-17
format and re-install seems to have done the trick. Just installed the open source package this time, and it has worked perfectly. Thanks everyone who has posted :)

---

