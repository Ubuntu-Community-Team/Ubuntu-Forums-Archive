---
title: "Problem with Booting"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by The Omani on 2007-09-07
Hi all,

I am having some problems in launching Linux. I am a new to Linux, never used it before. I have a problem in Launching the live CD on my Laptop, a friend of my suggested that it was due to my ATI Readon Graphics Card. Are there any solutions to do???

My Laptop Specs are:

100 GB hard disk
256MB ATI Readon Card
1.8 GHz Itel Pentium Duo
1GB Ram
Dell PC

ps: I have Windows and I am trying to Double Boot with Linux

---

### Post by The Omani on 2007-09-07
The Main problem:
The Ubuntu did not even start the live CD, which mean that booting was not successful...

After booting and starting the live CD, before the Desktop apears the screen turns black...

Tryed waiting long, but no use


TroubleShoot I tryed:

1- Check the CD of defects and its normal
2- Tryed the memory check and seems that no problem is there with it
3- Booting from graphics one did not help either

---

### Post by bone2006 on 2007-09-07
It seems that you are getting past the boot option and you are able to boot from the CD.  Do you have ubuntu 7.04?  There's generally two options on the top, the regular boot and the second option should be a graphics safe boot, which you should probably check since your having problems with your video.  

If that is still giving you problems and you can't get your video to work, I honestly would probably use a distro that already has the restricted video drivers already integrated, especially since your new to linux.  Something like Mepis might work out great for you, but playing around with liveCDs won't effect your HD, so you can try out a few distros if you'd like, but I think you should try the graphics safe mode first with ubuntu.

---

### Post by wpshooter on 2007-09-07
Unless I am missing his meaning, he has already tried the safe graphics boot and he said that it did not work.

---

### Post by The Omani on 2007-09-08
Thanks for the reply

Yes I did try the graphics modes but it was of no use, same result!

I did not really understand the Mepis, what is this?

---

### Post by overdrank on 2007-09-08
> **The Omani said:**
> Thanks for the reply

Yes I did try the graphics modes but it was of no use, same result!

I did not really understand the Mepis, what is this?

HI and welcome, Mepis is another linux distro. Can you be more specific on the model of ATI graphics card?

---

### Post by mcduck on 2007-09-08
If the graphics card is one of the new X series, you won't be able to install using the Desktop CD. You need to use the Alternate CD and then install Ati's fglrx driver for the graphics card before the desktop works.

See this sticky thread: [ Installing Ubuntu 7.04: ATI X**** Cards]("http://ubuntuforums.org/showthread.php?t=414194")

---

### Post by The Omani on 2007-09-08
Thanks but that solution comes after the life run, my computer refuses to life run the CD  even??

---

### Post by The Omani on 2007-09-08
The Graphics card is ATI Readon X1400

256 MB uses Catalyt to manage it

---

### Post by logos34 on 2007-09-08
> **The Omani said:**
> Thanks but that solution comes after the life run, my computer refuses to life run the CD  even??

You misunderstood...he meant you need to use the text-based Alternate install CD.

---

### Post by The Omani on 2007-09-08
tried the text installation but did not work either!

---

### Post by Pumm4 on 2007-09-08
Go into BIOS... and make shure your Boot sequence is set as: Floppy > CD-ROM > Hard Disk...

Report back...

---

### Post by The Omani on 2007-09-08
no use sorry...

thanks for ur help...

any new ideas??

---

### Post by The Omani on 2007-09-09
any help??

---

### Post by The Omani on 2007-09-12
???

---

### Post by mcduck on 2007-09-12
> **The Omani said:**
> tried the text installation but did not work either!

How did it not work? Could you tell a bit more about the actual problem you got? What errors did you get when installing the graphics driver as described in the sticky thread I linked for you?

---

