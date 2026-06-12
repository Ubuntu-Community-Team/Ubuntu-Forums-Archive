---
title: "Live CD problems"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by osxdude on 2007-04-24
Hello all! Jus' wanted to let you know I am a new Lunix user. This is my first Lunix experience. Now to the problem...

So I burned the latest Ubuntu ISO onto a Memorex Lightscribe CD-R. (I don't have a LS drive; I got the disc from a friend who did.) I then booted into the Live CD. I expected a slow startup, because of the Live CD. It takes 20 minutes to load Lunix. I can load a few prefrence panels, and such. Now it's time to install. It takes about, hmmm, maybe 13 hours. At least longer than I sleep. I clicked it at about 9:00 PM and the drive is still going at 7:00 AM the next day. I come home, it's entierly messed with. The language is diffrent, oh my gosh...

I once got to the map screen, but then Ubuntu rebooted. :mad:

I can give a recording of the CD drive when it's going, which sounds like a printer. It's like the ISO is majorly fragmented.

So what's wrong here? My specs:

IBM ThinkPad R40 (Laptop)
20GB Fujitsu HDD
1024x768 LCD
ATi Mobility Radeon 7500 (?)
Unknown CD drive manufacturer
Intel Celeron?

I have been loading into the Safe Graphics Mode lately.

Also: I would like to keep WXP. Where can I find GRUB? Or will it install or something when I install Ubuntu?

Thanks for your help! :)  :KS

---

### Post by Imgonna on 2007-04-24
Hey - cant help with technical but...

It sound like the CD is chewed.  Downloaded the CD, burnt the ISO and booted on my IBM Celly (not sure - from school) - from power on to use takes 5mins max. ;-)

Luck

Glen
x

---

### Post by osxdude on 2007-04-24
The CD was actually brand new, unless you mean something else.

Should I use my SD card (silly idea) instead? Idk if my laptop has USB boot...

Oh! I could use my iPod...but then I'd have to load into windows. Dang.

I actually have windows hibernated...is that affecting it?

---

### Post by Sef on 2007-04-24
1) How much ram do you have?

2) [Dual boot]("http://www.psychocats.net/ubuntu/installing") from the Live CD

3) [Dual boot]("http://users.bigpond.net.au/hermanzone/") from the alternate CD.

4) Did you md5sum the download?

5) Did you burn it at 4x or less?

6) Did you check the disk for errors?

---

### Post by osxdude on 2007-04-24
Let's answer your questions...

[list=1]
[*]256MB. Did I make the right choice?
[*]I did.
[*]I don't have any CD-R/Ws wth me.
[*]What's that? (That is, md5sum.)
[*]I burnt it at 10x.
[*]I actually verified the disc after the the burning (I have Nero). Is that OK?
[/list]

Edit: Should I just not change the time zone on Step 2? Can I change it later?

---

### Post by Sef on 2007-04-24
> Let's answer your questions...

   1. 256MB. Did I make the right choice?
   2. I did.
   3. I don't have any CD-R/Ws wth me.
   4. What's that? (That is, md5sum.)
   5. I burnt it at 10x.
   6. I actually verified the disc after the the burning (I have Nero). Is that OK?

1) That's the minimum ram for Ubuntu.  Will run, but better if you upgrade to at least 512 mb ram.

2) Great

3) Just need a cd-R.   Just uses text-based install (alternate cd) instead of a GUI install (Live CD.)  Easy to follow tutorial.

4) [How to md5sum]("https://help.ubuntu.com/community/HowToMD5SUM").

5) Burn the iso at 4x or less.  Higher speeds may cause a bad burn.

6) It's ok.

> Edit: Should I just not change the time zone on Step 2? Can I change it later?

Yes, you can change it.   Just right click on the date and time on the top task bar > choose adjust date and time > click on Time Zone.

---

### Post by silverglade00 on 2007-04-24
> **osxdude said:**
> 

I actually have windows hibernated...is that affecting it?

Very possibly. Shut down Windows all the way before attempting something like this. You could end up blasting it all. You are messing with the basic structure of the hard drive.

---

### Post by osxdude on 2007-04-25
Ok, so I have completly shut down Windows, and I actually did not load into Graphics Safe Mode; everything is actually faster. I got past the time zone question (which I did not change to "Chicago"), then went to school. I came home with a broken spacebar and the laptop turned off. :(   (I fixed both.)

The installer is loading now. However, the top and bottom bars (whatever they are called) did not appear. I do not have access to the internet in Ubuntu (yet), so GNOME may be the problem.

The only troubles so far are the time zone screen.

---

### Post by osxdude on 2007-04-26
OK Here's what happened last night...

I got past Step 3! The partitioner tried to load for Step 4, but...then the installer closed itself (kernel panic maybe?) I'm going to download the alternate installer right now.

---

### Post by osxdude on 2007-04-27
I have to bump this.

Edit: I actually found that the problem is my CD drive. It works like a charm on my desktop comp, so I will have to burn the alternate for my laptop. On my desktop I am also having partitioning problems. I says it  can't resize the partition. Help before I put in a 20GB Western Digital HDD into my desktop?

---

