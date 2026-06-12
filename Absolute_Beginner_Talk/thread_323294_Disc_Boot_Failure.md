---
title: "Disc Boot Failure"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by KaelG on 2006-12-21
When I try to boot off the Live CD, I get "Disc Boot Failure" error. I've tried it with HDDs plugged in, when them unplugged, played around heaps on the bios settings, still does it.
I believe this is a problem unrelated to Ubuntu, as it does it when I try to boot off an XP disc too. :mad: 

What do I do? I've tried resetting the bios settings but it still does it. :confused: :confused: :(

---

### Post by rccharles on 2006-12-22
> **KaelG said:**
> When I try to boot off the Live CD, I get "Disc Boot Failure" error. I've tried it with HDDs plugged in, when them unplugged, played around heaps on the bios settings, still does it.
I believe this is a problem unrelated to Ubuntu, as it does it when I try to boot off an XP disc too. :mad: 

What do I do? I've tried resetting the bios settings but it still does it. :confused: :confused: :(

I had to look up what "Disc Boot Failure" error meant.  I found this thread fairly informative:

[http://au.answers.yahoo.com/question/index.php?qid=20061128111718AALAo42](http://au.answers.yahoo.com/question/index.php?qid=20061128111718AALAo42)

It's not about Ubuntu.

Your BIOS is not finding a properly formated MBR on your boot device.  You could have a bad CD or a bad CD-ROM drive.  Since you tried two CDs, I'd look at your CD-ROM drive.

Check cables and BIOS configuration.  Replug all cables.  Any chance of using a different CD-ROM drive or testing your CD-ROM drive in a different machine?

Robert

---

### Post by rccharles on 2006-12-22
Here is a long list of alternate ways of installing Ubuntu:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Robert
:cool:

---

### Post by KaelG on 2006-12-22
I've tried 3 different CD drives, a bunch of different cables, etc.
That yahoo answers link I've also tried already.
I'll look at the Ubuntu installation guide.

---

### Post by TheRingmaster on 2006-12-22
If you burned the cd, try burning another cd REAL SLOW (1x is best)

If you burn the cd too fast, it will have errors.

---

### Post by KaelG on 2006-12-22
The CD doesn't have errors. I've tried a 6.06 and 6.10 one, and they work on another persons computer.

---

### Post by david_kt on 2006-12-22
Disk boot failure means the CPU fail to read operating system. As you have check that the CD is ok, the problems lies in the computer. First of all is bios settings, should include your CD ROM. But I think you have set the bios properly.

So, it is possibly a defective CD ROM. If possible, try to interchange your CD ROM with your friend's CD ROM (which is in good condition).

But before you try to install Ubuntu, is this computer in working condition?

Regards,
DK

---

### Post by david_kt on 2006-12-22
Sorry, fail to read that you have tried 3 CD Rom (I supposed you have verified that all CD ROM in working condition). Then, most likely is the bios software. But I am not very sure about Bios software. You should check the manufacturer of the bios, and check the website if there is any upgrade available.

If that fails, may be you want to hack your bios, but do it on your own risk. Below link provide free utility to hack your bios:

[http://www.11a.nu/software/bios-pc-bios-security-and-maintanance-toolkit/](http://www.11a.nu/software/bios-pc-bios-security-and-maintanance-toolkit/)

Regards,
DK

---

### Post by KaelG on 2006-12-22
How am I meant to install drivers on the bios if it won't read the CDs?
I don't have a HDD, hence me booting off a live CD.
The CDs are FINE, they work for other people.

---

### Post by louieb on 2006-12-22
You have tried to boot with different CD 's that work on another computer.
You have  swapped out the CD drive and it still doesn't work.
If the machine has a floppy drive then the only other thing I can think to try is [Smart Boot Manager.]("http://louboldt.com/ilinuxsbm.htm")
The floppy disk is easy to make and it should take you less that half an hour to download the stuff you need and make the floppy. 
[  ]("http://louboldt.com/ilinuxsbm.htm")

---

### Post by david_kt on 2006-12-22
> **KaelG said:**
> How am I meant to install drivers on the bios if it won't read the CDs?
I don't have a HDD, hence me booting off a live CD.
The CDs are FINE, they work for other people.

DK:
You could try to borrow OS-preloaded harddisk from your friend to boot up your PC.

Regards,
DK

---

### Post by STREETURCHINE on 2006-12-23
> **KaelG said:**
> When I try to boot off the Live CD, I get "Disc Boot Failure" error. I've tried it with HDDs plugged in, when them unplugged, played around heaps on the bios settings, still does it.
I believe this is a problem unrelated to Ubuntu, as it does it when I try to boot off an XP disc too. :mad: 

What do I do? I've tried resetting the bios settings but it still does it. :confused: :confused: :(

hi kaelg,i burned the cd's for you at 8x .
i tested them on my optima lap top ,and my dell computer with windows on it ,and my main computer which is a custom built ,they loaded fine and run,
those diks were from a batch iburded and have given them to about 50 friends and so far no problems.
sorry i cant help you with why they are not working ,but they were checked .

---

### Post by kinematic on 2006-12-23
> **TheRingmaster said:**
> If you burned the cd, try burning another cd REAL SLOW (1x is best)

If you burn the cd too fast, it will have errors.

i wish people would stop saying that.
most cd's don't like that kind of extremely slow speeds....8x or 16x is just fine!

---

### Post by TheRingmaster on 2006-12-23
> **kinematic said:**
> i wish people would stop saying that.
most cd's don't like that kind of extremely slow speeds....8x or 16x is just fine!
link please

---

### Post by smoker on 2006-12-23
this could be the ide controller/ ide connector on the motherboard that is faulty, if your cd is connected to ide channel 2, try it on channel 1 and see if any different.

---

### Post by KaelG on 2006-12-25
> **STREETURCHINE said:**
> hi kaelg,i burned the cd's for you at 8x .
i tested them on my optima lap top ,and my dell computer with windows on it ,and my main computer which is a custom built ,they loaded fine and run,
those diks were from a batch iburded and have given them to about 50 friends and so far no problems.
sorry i cant help you with why they are not working ,but they were checked .
thank you
yes i know my motherboard just likes to be silly sometimes ](*,) 
new computer coming soon though :) 

> **smoker said:**
> this could be the ide controller/ ide connector on the motherboard that is faulty, if your cd is connected to ide channel 2, try it on channel 1 and see if any different.
i tried this :(

---

### Post by STREETURCHINE on 2006-12-25
:-D  hope you have better luck with your new computer ..[-o<

---

### Post by spockrock on 2006-12-25
ok what is your boot sequence in your bios.  Make sure, that cdrom is in the sequence or that a specific cdrom is picked.  Some motherboards either just say cdrom or let you pick a specific cdrom.  Even if it says cdrom sometimes a motherboard will let you boot of either cdrom, or the master drive.....better yet if you have multiple drives try both and see if they boot.  Hope that helps, good luck.

---

### Post by maniac_X on 2006-12-25
...also doublecheck jumpers on the hardware devices.

---

