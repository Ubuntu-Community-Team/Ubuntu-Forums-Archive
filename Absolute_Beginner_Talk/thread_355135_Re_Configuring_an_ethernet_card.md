---
title: "Re: Configuring an ethernet card"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by icyblue on 2007-02-06
Hello!!!

I'm just a newbie in ubuntu. I've done my ubuntu installation through live cd. Now, I can't connect to my internet. No ethernet card has been configured automatically. In networking tools, I can find only 'Modem configuration' and no ethernet configuration. I used 'sudo pppoeconf'. It's of no use.. Can anyone get me an answer?

Thanks in advance!!!

---

### Post by Maxtorm on 2007-02-06
A few questions: (1) Do you know what kind of network card you have? (2) Are you directly connected to the Internet or is there a router between your computer and your modem? (3) Were you able to connect to the Internet when you booted from your Live CD?

---

### Post by icyblue on 2007-02-06
It's a sc92031 NIC card(silan).. It's workin because I'm using the same in Windows..Yeah, I've a ADSL router connected. I was not able to connect in the live cd as well...

---

### Post by Daiver on 2007-02-06
I'm having this exact same problem on another machine with a fresh install of 6.10. :S

---

### Post by Maxtorm on 2007-02-06
Yikes.  Looks like there is a known issue with the driver.  See: [http://www.uwsg.iu.edu/hypermail/linux/kernel/0612.1/0521.html](http://www.uwsg.iu.edu/hypermail/linux/kernel/0612.1/0521.html) .  Perhaps someone more knowledgeable than I can tell you how to find and compile the older driver.

---

### Post by icyblue on 2007-02-06
I've sc92031.c(through the cd got along with NIC).. but when I compiled it getting a lot of errors... Guess, I don't have the compilers installed by default..

---

### Post by icyblue on 2007-02-06
Or Can you tell me how to use internet through USB?

---

### Post by Maxtorm on 2007-02-06
To compile, you will need to install the build-essential package.  To do so:
```
sudo apt-get install build-essential
```
As for a network connection over USB, go to your favourite retailer web site and do a search for "Ethernet USB".  You should find lots of options.

---

### Post by icyblue on 2007-02-06
But in my synaptic manager, I can't find build-essential package. I had it in my live cd. When I installed, It disappeared...

---

### Post by Maxtorm on 2007-02-07
That's a little odd.  Build-essential should automatically appear once you have installed from CD-ROM.  Try the following.  I know it works with the Alternate installer ISO; not sure about the Live CD.  
[LIST=1]
[*]Open a terminal window and type: ```
sudo apt-cdrom add
```
[*]Put the CD you installed Ubuntu from in the drive.  Wait for it to spin up and then press Enter.
[/LIST]
This should add the CD-ROM to the synaptic repositories and you should now be able to install build-essential, either through Synaptic Package Manager or as above using apt-get.

---

