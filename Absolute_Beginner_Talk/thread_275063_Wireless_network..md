---
title: "Wireless network."
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by bourne- on 2006-10-10
Completely new to wireless on linux. I have a Linksys WMP54GS Wireless- G adapter and I have NO idea how to get it running with linux. I have been tearing through pages upon pages of info on how to do this but I can't make heads nor tails of. 
[http://forums.windrivers.com/archive/index.php/t-67640.html]("http://forums.windrivers.com/archive/index.php/t-67640.html")
[http://www.linuxresource.co.uk/index.php?module=forums&act=viewtopic&id=11]("http://www.linuxresource.co.uk/index.php?module=forums&act=viewtopic&id=11")

What is Ndiswrapper? Now I do have internet access through another computer running XP home. But I have NO access whatsoever on the linux machine so I can't link to get files from that machine. But I am just totally stuck and have no idea even where to start.

any help would greatly be appreciated!!

---

### Post by jd65pl on 2006-10-10
see this on [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") it is on the ubuntu wiki

---

### Post by bourne- on 2006-10-10
ignorant me sorry i forgot to mention that i just finished installing a dual boot system. I am running ubuntu and windows XP. Xp is easy to configure, its the ubuntu i am having problems with!!

---

### Post by jd65pl on 2006-10-10
> Even if your wireless network card does not have a native Linux driver, you may still be able to get it working with ndiswrapper. Ndiswrapper is a Linux module which allows Ubuntu to use the Windows driver for wireless cards (in most cases).

See the ndiswrapper wiki posted above or alternative try searching for your card.

---

### Post by bourne- on 2006-10-10
What is the command I need to use or what do I type in in the blacklist file to disable the bcm43xx drivers?

---

### Post by jd65pl on 2006-10-10
Add the driver to the file below to blacklist it

```
sudo nano /etc/modprobe.d/blacklist
```

---

### Post by bourne- on 2006-10-10
> **jd65pl said:**
> Add the driver to the file below to blacklist it

```
sudo nano /etc/modprobe.d/blacklist
```

Sorry man this is probably going to sound like a really stupid question but do I fire that command through the terminal? or do I navigate to that file and type it manually right into the file?
And what do I type to add the driver? Do I just type the driver name at the bottom of the file?

---

### Post by jd65pl on 2006-10-10
Whack the command off in terminal if you are not into editing files in teminal excahnge "nano" for "gedit".

---

### Post by jd65pl on 2006-10-10
Note just add the lines below for your own info etc...

> #Blacklist my wireless driver incase I ever need to go back to it
blacklist bcm43xx

---

### Post by bourne- on 2006-10-10
> **jd65pl said:**
> Note just add the lines below for your own info etc...

Oh perfect man sorry for the stupid question. I figured that the top line was just for your own info. I just put disabled it because it causes conflict with other drivers

i used sudo vi /etc/modprobe.d/blacklist ( I know vi a little)
added blacklist bcm43xx

and it looked like it worked. It says I have to restart so that I am on my way to do that. Thanks for your help thus far man I appreciate it!!

---

### Post by jd65pl on 2006-10-10
vim is still a text file editor with more capabilities for a more capable user but more on that another day!!!!

---

### Post by bourne- on 2006-10-10
> **jd65pl said:**
> vim is still a text file editor with more capabilities for a more capable user but more on that another day!!!!

without a doubt man, I am just learning vi in school right now so I just know the basics of it. But yeah I just restarted the computer and I am about to continue on with the tutorial you gave me. I already burned the proper linksys files to a CD and I am shipping them over the my ubuntu computer as we speak

---

### Post by bourne- on 2006-10-10
I am currently stuck deciding what driver to use
i used the lspci to find out what exact chipset my network card is using (BCM4318 ). I used number to search the ndiswrapper list site and found my card, however I am not sure which driver to take because there are two
[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/")
[ftp://ftp.linksys.com/international/drivers/WPC54G_driver_utility_v3.1.zip]("ftp://ftp.linksys.com/international/drivers/WPC54G_driver_utility_v3.1.zip")
I choose the drivers from the second link first but after reading further into the tutorial about the files I might be to use to install the drivers I think I made the wrong choice and I have now downloaded the first links drivers ( to be exact I downloaded the second .zip in that list). However I am not sure exactly which driver to use. Does anything think they might be able to shed some light on which driver I should use?

thanks
todd

---

