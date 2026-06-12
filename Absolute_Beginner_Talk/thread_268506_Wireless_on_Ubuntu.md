---
title: "Wireless on Ubuntu"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by ade_1 on 2006-09-30
Hi, 

I am new to Ubuntu and have checked out a Live CD version of it. I have liked what I have seen however I would like to install it. Before I install it I would like to know how I can use Wireless on it... I have seen you can connect via Modem or Ethernet however like I say, I am on Wireless at the moment.

If there is a way to use wireless it would be great to hear about it :) 

Thanks in advance


Aidan

---

### Post by Transmit on 2006-09-30
Yes there is, I just installed a program called ndiswrapper and my wireless just popped on like it would in windows. For the beginners (like me) it's a bit hard to setup the install because you need to put in a weird command in something called the terminal (=command window in windows) but you'll find all the help you need on these forums, just like I did!

---

### Post by ade_1 on 2006-09-30
Thanks :) Ill take a look around for that, and information on how to install :).

---

### Post by orb9220 on 2006-09-30
I advise if you have xp installed keep it and dual boot with ubuntu install then you will have access to the forums even tho you have troubles at the beginning.

I destroyed my ubuntu a couple of times doing things while I was learning. And dual boot with xp saved me plus linux is not great with games.

So keep xp for awhile anyway.

---

### Post by ade_1 on 2006-09-30
Yeah, I had planned on doing that. I have never used a Linux OS before and I have recently purchased a larger hard drive therefore giving me access to trying out new stuff. I thought id give Ubuntu a go as I have heard and read about how good it is.

---

### Post by orb9220 on 2006-09-30
Yep and the new edgy with beryl (new xgl/compwiz) eye candy works well and wow's my xp friends.

---

### Post by blx_286 on 2006-09-30
> **ade_1 said:**
> Yeah, I had planned on doing that. I have never used a Linux OS before and I have recently purchased a larger hard drive therefore giving me access to trying out new stuff. I thought id give Ubuntu a go as I have heard and read about how good it is.

I would also recommend the dual-boot for starting out. If you do a forum search, there are some good threads on it.

You might also do a quick search for your wireless card. That will give you an idea of what steps you will need to take to set it up.

---

### Post by Nut on 2006-09-30
> **Transmit said:**
> Yes there is, I just installed a program called ndiswrapper and my wireless just popped on like it would in windows. For the beginners (like me) it's a bit hard to setup the install because you need to put in a weird command in something called the terminal (=command window in windows) but you'll find all the help you need on these forums, just like I did!

How did you get the program if your internet doesn't work? Did you use a different computer and save the files to a disc or what?

---

### Post by ade_1 on 2006-10-01
I am currently Dual Booting with XP. I then transfered ndiswrapper using a USB Memory stick

---

### Post by blx_286 on 2006-10-01
> **ade_1 said:**
> I am currently Dual Booting with XP. I then transfered ndiswrapper using a USB Memory stick

Those flash drives rock, don't they. That's exactly how I started out, trasnferring files back and forth. Now my flash drive has a folder called UbuntuDocs and UbuntuSoftware. In the UbuntuDocs folders I keep local copies of the threads that I have had to make use of (i.e. wireless setup, dual-boot, samba, etc.). That way, if I ever need them again, I have easy access to them. Same with the UbuntuSoftware folder, but there are so many things in the repositories that this folder doesn't have much in it.

So, did you you get your wireless set up?

---

### Post by ade_1 on 2006-10-01
No, im completely stuck... 
I did start another thread regarding help on setting up ndiswrapper   but I didnt get much of a response. However I wondered if there was any other alternative to setting up Wireless on Ubuntu.
I have a small problem though... my wireless adaptor does not have a Linux driver...

If anyone could offer any help that would be great thanks :)

Aidan

---

### Post by blx_286 on 2006-10-01
> **ade_1 said:**
> No, im completely stuck... 
I did start another thread regarding help on setting up ndiswrapper   but I didnt get much of a response. However I wondered if there was any other alternative to setting up Wireless on Ubuntu.
I have a small problem though... my wireless adaptor does not have a Linux driver...

If anyone could offer any help that would be great thanks :)

Aidan

Sometimes, you can find a lot by searching this forum. What I have done is search first and if I can't find the answer, I will post. If I find the answer after I post, I will then update my original post to help the next person.

All of that being said, let's see if we can figure out your wireless problem. What type of card do you have?

---

### Post by ade_1 on 2006-10-01
I have a BT Voyager 1055 USB Wireless Adaptor... which I personally believe will be the problem.

(In Network Manager all that shows up is Ethernet Connection and Modem) Thought id pop that bit in :)

---

### Post by blx_286 on 2006-10-01
> **ade_1 said:**
> I have a BT Voyager 1055 USB Wireless Adaptor... which I personally believe will be the problem.

(In Network Manager all that shows up is Ethernet Connection and Modem) Thought id pop that bit in :)

Well just a warning, I am still stumbling my way through Linux too, but I think we need to determine the chipset first. It may be a Broadcom chipset and maybe you can use ndiswrapper along with the Windows drivers, to get it going. What do you get when you go into Terminal and type

```
lsusb
```

---

### Post by ade_1 on 2006-10-01
When I type lsusb into terminal I get the following :

Bus 005 Device 006: ID 1690:0715 Askey Computer Corp. [hex]
Bus 005 Device 005: ID 04b8:081a Seiko Epson Corp.
Bus 005 Device 002: ID 14aa:0221 AVerMedia (again) or C&E
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 002: ID 413c:2005 Dell Computer Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000


Thanks

Aidan

---

### Post by blx_286 on 2006-10-02
> **ade_1 said:**
> When I type lsusb into terminal I get the following :

Bus 005 Device 006: ID 1690:0715 Askey Computer Corp. [hex]
Bus 005 Device 005: ID 04b8:081a Seiko Epson Corp.
Bus 005 Device 002: ID 14aa:0221 AVerMedia (again) or C&E
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 002: ID 413c:2005 Dell Computer Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000


Thanks

Aidan


I think the one listed as Askey Computer Corp is your card. I also think if you type this in Terminal, it will give us more info. I can't check right now, I am at work on my Windows box (I know :rolleyes:  )

```
lsusb -v
```

If I remember right, I have also went into >System >Administration >Device Manager and found the chipset before.

I searched the forum for Voyager and found several threads. Maybe one of these will help -

[http://ubuntuforums.org/showthread.php?t=262638&highlight=voyager](http://ubuntuforums.org/showthread.php?t=262638&highlight=voyager)
[http://ubuntuforums.org/showthread.php?t=25683&highlight=voyager](http://ubuntuforums.org/showthread.php?t=25683&highlight=voyager)

If not try and search for "voyager" (without the quotes), I found 3 pages of threads to look through. If you are still having trouble, post back here and maybe someone more knowledgable will jump in.

---

### Post by ade_1 on 2006-10-02
I have the information from the lsusb -v command however its pretty long, also I have a screenshot of the device manager which does display my Wireless Adaptor however... I am having trouble getting the screenshot and the USB information from Ubuntu onto XP. I apparently dont have the permission to move the stuff onto my USB pen. I have tried changing permissions but this unfortunately hasnt worked. How can I go about getting the info onto XP so that I can display it here?

Thanks 

Aidan

---

### Post by blx_286 on 2006-10-02
> **ade_1 said:**
> I have the information from the lsusb -v command however its pretty long, also I have a screenshot of the device manager which does display my Wireless Adaptor however... I am having trouble getting the screenshot and the USB information from Ubuntu onto XP. I apparently dont have the permission to move the stuff onto my USB pen. I have tried changing permissions but this unfortunately hasnt worked. How can I go about getting the info onto XP so that I can display it here?

Thanks 

Aidan

I haven't read the part of the manual about permissions yet :rolleyes:  but try this...

My thumbdrive is mounted as /media/TRAVELDRIVE/ and I have a Temp directory under my home directory /home/tim/Temp. So, you might try something like this -

```
cd /home/tim/Temp
sudo lsusb -v > lsusb.txt
sudo cp lsusb.txt /media/TRAVELDRIVE/.
sudo cp screenshot.jpg /media/TRAVELDRIVE/.

```

The first line changes to the temp directory.
The second line creates a text file with the output of your lsusb command.
The other lines are just copying that file, and your screenshot file to the thumb drive. Of course you will need to change file names or directories where needed.

---

### Post by ade_1 on 2006-10-03
Thanks for that :), Ill get it done tonight and will post up all findings.

I should probably get a book about Ubuntu / Linux in order to progress on my own as I wont always be able to rely on this forum...

Thanks

Aidan

---

### Post by blx_286 on 2006-10-03
> **ade_1 said:**
> Thanks for that :), Ill get it done tonight and will post up all findings.

I should probably get a book about Ubuntu / Linux in order to progress on my own as I wont always be able to rely on this forum...

Thanks

Aidan

That permissions comment really wasn't directed at you, I am still learning also :)

---

