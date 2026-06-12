---
title: "One step closer....."
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-05-28
Well I now have my wireless saying 99% signal strength in connection properities, but  no web-pages load. 

In activity in connection properities, the packets recieved are really low, specifically:
Revieved: 217 packets (77.3 Kb)
Sent: 21656 packets (1.0 Mb)

Help?

---

### Post by CitizenKane on 2006-05-28
I would suggest using network manager for wireless as it is very easy to use.  I believe that you need to have the universe repositories enabled to get it.  Then it is just

```

sudo apt-get update
sudo apt-get install network-manager

```

If something doesn't work just tell me.  I have been using dapper for awhile and I don't remember everything from breezy.

---

### Post by meng on 2006-05-28
Have you set the router as the default gateway for browsing?

---

### Post by tartarian on 2006-05-28
How do I set it as the default gateway. I might have done, but im not sure.

I've installed network-manager. What now? Nothing happens when I type network-manager into the terminal and there doesn't seem to be a launcher in any of the menus'

---

### Post by meng on 2006-05-28
I have no personal experience with using wireless for Linux, but I understand you should be able to configure your network by going to System > Administration > Networking.

---

### Post by skyshark88 on 2006-05-28
Laptop???? 
What card??? PCMCI????

---

### Post by tartarian on 2006-05-28
Ye, its a Packard Bell Easynote R4 laptop, [(here)]("http://support.packardbell.com/uk/item/index.php?pn=PB17C00101&g=1400")

The card is internal, built on the Rt2500 chip - which I know is meant to be problematic. Grrr....

---

### Post by skyshark88 on 2006-05-28
Have you tried the windows wireless rapper gui from the repository???

---

### Post by skyshark88 on 2006-05-28
Have you disabled you lan card????

---

### Post by tartarian on 2006-05-28
Yes and it still doesnt work. although I am using my lan at the moment because i need a connection, but i cant use it permenantly

---

### Post by skyshark88 on 2006-05-28
I have the same problem with my Sony it uses pmci card and all I have seen is the pmci will not work with the current kernel it needs special parameters....

---

### Post by skyshark88 on 2006-05-28
try disableing the etho first at that I am at dead end.

---

### Post by skyshark88 on 2006-05-28
[http://ubuntuforums.org/showthread.php?t=90450](http://ubuntuforums.org/showthread.php?t=90450)        maybe

---

### Post by tartarian on 2006-05-28
I'm running dapper :(

---

### Post by skyshark88 on 2006-05-28
Ya well I am using my wireless now and its a first...
I went to the add/remove program, and found the configure network card application and know I am sitting pretty... so give that a try....

Ps its in system tools...

---

