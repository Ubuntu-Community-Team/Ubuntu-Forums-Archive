---
title: "Installing"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Cannonball003 on 2007-08-03
Ok so I have my Live CD in right now and I'm loving it! I was shocked to see how fast the CD runs.... So I think I'm ready to install. I have to keep windows on this pc and I can't mess it up because I don't have restore cd. I also will have to delete ubuntu before I send it back. 

So I guess my questions are: 

1.I'm not going to mess up Windows by installing linux correct?

2.When I'm done with linux how would I delete it?

3.When I dl a file while running ubuntu off the live cd where does that save? Just kinda interested because I downloaded the Internet thing nbis thing lol for the wifi. I can't remember the name and I deleted it, but was just curious where did that save to when I'm running of a cd? 

4.I think I have an older version of ubuntu, 4a. How do I check that? 4b.Would it be easier to install the older version(if it is older)of the ubuntu live and then update? Or better to get the newest version than install?

5.I keep reading about partitions and such on the HDD. I understand the basic concept but don't really know how to do it in linux nor what size they should be etc etc.

So as you call tell I'm a total newbie, and would appreciate any help.

---

### Post by Tux Aubrey on 2007-08-03
Welcom Cannonball!

I think you will find all the answers to your questions here -  [http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")  Bookmark that site and read it.

The best advice I can offer is "Take your time".  Don't rush.

Installing Ubuntu is much easier than installing windows, but very few people have ever done that.

Setting up a dual boot is relatively easy and I have never lost my Windows installation - but there is always a risk, particularly if you just click your way through the installer without understanding which partition is which.  The psychocats site has some well written articles - including one on designing your partitioning and another on how to delete your Ubuntu partition when you have "finished" with it.

And after more than a year using, reinstalling, upgrading and generally modding Ubuntu, I still don't know where programs get installed to.  :confused:  It just doesn't seem to matter!

---

### Post by Cannonball003 on 2007-08-03
> **Tux Aubrey said:**
> Welcom Cannonball!

I think you will find all the answers to your questions here -  [http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")  Bookmark that site and read it.

The best advice I can offer is "Take your time".  Don't rush.

Installing Ubuntu is much easier than installing windows, but very few people have ever done that.

Setting up a dual boot is relatively easy and I have never lost my Windows installation - but there is always a risk, particularly if you just click your way through the installer without understanding which partition is which.  The psychocats site has some well written articles - including one on designing your partitioning and another on how to delete your Ubuntu partition when you have "finished" with it.

And after more than a year using, reinstalling, upgrading and generally modding Ubuntu, I still don't know where programs get installed to.  :confused:  It just doesn't seem to matter!

Ok so I figured out I'm running 6.10. So would it better to install of the 6.10 or dl the new 7.04? 

Also I didn't find the article about deleting the ubuntu partition? 

Thanks for the help that site has tons of the stuff I needed.

---

### Post by coolen on 2007-08-03
> **Cannoball said:**
> Ok so I have my Live CD in right now and I'm loving it! I was shocked to see how fast the CD runs.... So I think I'm ready to install. I have to keep windows on this pc and I can't mess it up because I don't have restore cd. I also will have to delete ubuntu before I send it back. 

So I guess my questions are: 

1.I'm not going to mess up Windows by installing linux correct?

2.When I'm done with linux how would I delete it?

3.When I dl a file while running ubuntu off the live cd where does that save? Just kinda interested because I downloaded the Internet thing nbis thing lol for the wifi. I can't remember the name and I deleted it, but was just curious where did that save to when I'm running of a cd? 

4.I think I have an older version of ubuntu, 4a. How do I check that? 4b.Would it be easier to install the older version(if it is older)of the ubuntu live and then update? Or better to get the newest version than install?

5.I keep reading about partitions and such on the HDD. I understand the basic concept but don't really know how to do it in linux nor what size they should be etc etc.

So as you call tell I'm a total newbie, and would appreciate any help.

1. Most likely not. Defrag first, to minimise the risk, and pray. I've never had troubles, but you're playing with fire here.

2. You'd need to restore your old MBR (in place of Grub) and then simply remove the partition. There are likely many tools to accomplish each of these goals.

3. It could go to RAM, or temporarily to your hard drive. Not sure how Ubuntu does it, but some Live CDs do, in fact, touch your hard drive.. I learned that when I accidentally turned off my computer one day while using the Knoppiz Live CD. All information from yuor session is lost when you turn the computer off.

4. I'd suggest install what you have and upgrade. You'd be no worse off for download size, time, or installation...

5. I'd say 10 Gb for Ubuntu, if you're going to use it seriously. If it's just a hobby, or a test run, go for 5. Ubuntu requires 2 Gb as a bare minimum. You'll find that your Ubuntu install will fill up far slower than Windows.

---

### Post by Cannonball003 on 2007-08-03
> **coolen said:**
> 1. Most likely not. Defrag first, to minimise the risk, and pray. I've never had troubles, but you're playing with fire here.

2. You'd need to restore your old MBR (in place of Grub) and then simply remove the partition. There are likely many tools to accomplish each of these goals.

3. It could go to RAM, or temporarily to your hard drive. Not sure how Ubuntu does it, but some Live CDs do, in fact, touch your hard drive.. I learned that when I accidentally turned off my computer one day while using the Knoppiz Live CD. All information from yuor session is lost when you turn the computer off.

4. I'd suggest install what you have and upgrade. You'd be no worse off for download size, time, or installation...

5. I'd say 10 Gb for Ubuntu, if you're going to use it seriously. If it's just a hobby, or a test run, go for 5. Ubuntu requires 2 Gb as a bare minimum. You'll find that your Ubuntu install will fill up far slower than Windows.
2. I don't understand MBR and grub I guess any good articles telling me what they are?

3. Yeah I was just wondering... 

4.Ok.

5. I have an 80 gig Hd so I could make it 10.

---

### Post by coolen on 2007-08-03
The MBR (Master Boot Record) is a small space at the beginning of your hard drives/partitions. It can contain a number of things, including (most commonly) the boot loader. This is a small program responsible for loading enough of an operating system to get things started.
The boot loader which ships with Windows is designed to boot Windows, and only Windows.
Linux ships usually with Grub, less commonly nowadays with LILO. Each of these allows you to choose your operating system from a list.
Unless you can instruct Grub to look for the configuration file from a partition you don't plan on deleting, I don't think it'd work past the death of Ubuntu. Thus, you'll need to get your Windows MBR back.

---

### Post by Cannonball003 on 2007-08-03
> **coolen said:**
> The MBR (Master Boot Record) is a small space at the beginning of your hard drives/partitions. It can contain a number of things, including (most commonly) the boot loader. This is a small program responsible for loading enough of an operating system to get things started.
The boot loader which ships with Windows is designed to boot Windows, and only Windows.
Linux ships usually with Grub, less commonly nowadays with LILO. Each of these allows you to choose your operating system from a list.
Unless you can instruct Grub to look for the configuration file from a partition you don't plan on deleting, I don't think it'd work past the death of Ubuntu. Thus, you'll need to get your Windows MBR back.

Ok so when I install linux it will change the MBR... How do I change it back to the one that I originally had?

---

### Post by Cannonball003 on 2007-08-03
> **Cannoball said:**
> Ok so when I install linux it will change the MBR... How do I change it back to the one that I originally had?

still wondering about this.

---

### Post by davidjmayo on 2007-08-03
> **Cannoball said:**
> still wondering about this.

after you finish with ubuntu to go back to win only follow this guide (see the second edited version further down the page)
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by Cannonball003 on 2007-08-03
> **davidjmayo said:**
> after you finish with ubuntu to go back to win only follow this guide (see the second edited version further down the page)
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Nice that is exactly what I was looking for! 

Thanks!

---

### Post by coolen on 2007-08-04
Another solution, if you know that Ubuntu isn't going to be around for long. I did this on my Mum's computer some time ago,
Grab the alternate install CD. From there, it's possible to install Ubuntu without installing Grub. You'll need a Grub disc (or, as I used, the Super Grub Disc) to boot up Ubuntu, but you should then be able to remove Ubuntu by simply deleting the partitions. No Grub = no problems. Your boot loader won't know anything has changed.

---

