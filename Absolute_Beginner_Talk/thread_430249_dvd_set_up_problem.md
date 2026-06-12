---
title: "dvd set up problem"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by halligan46 on 2007-05-01
Hello all,
 I just completed a new build and have installed winXP home, as my OS.  I want to use UBUNTU as my dual boot OS.
When I run the DVD in my Plextor DVD-rom drive I get the following message after I choose to run or install Ubuntu:
     /bin/sb: can't access tty; job control turned off
    (initamfs)_

I don't know what these terms are, as you can see I am a total noobie to ubuntu and could use a little push in the right direction.
 If needed my system is intel dg965wh with intel 6400 cpu,  two hdd's 300 and 500 gig respectively, a plextor dvd-rom drive and a regular ole floppy drive.  As I said I have a new install of winXP home ed.

Thanks in advance for any advice

JimThomas

---

### Post by starcraft.man on 2007-05-01
Ya, I had this too when I was trying to install Feisty. I don't know if the bug has been fixed. I know that it has something to do with Feisty not recognizing multiple drives (HDD or CD/DVD) on IDE or optic. Only affects certain set ups. 

I believe the easy solution is to take out one of your drives and then boot into Feisty again. So, basically I guess assuming the 500 GB is your storage one, I'd unplug it and then install Feisty with your XP partition on the other. GRUB will autodetect your XP partition once your done installing long as its on the drive you left plugged in. Then you can put back the drive and mount it separately :).

That should do it. :)

If the problem has been fixed can someone let me know and correct me pls.

---

### Post by kyphi on 2007-05-02
Let me guess, your hard drives are SATA II and your DVD is PATA.  I also have a DG965WH board and that created several problems.

The method I used to work around this was to insert an IDE to SATA adapter into the back of the DVD drive and connect it to one of the SATA ports (there are 6 in all).  Your local computer shop will most likely have one of these.

Alternatively, you could install a second DVD like the ASUS SATA DVD.

---

### Post by halligan46 on 2007-05-02
Kyphi
Thanks for your response, this sounds like the easiest way to deal with my issue.  Hopefully I'll be sending you another message from my ubuntu OS soon!

Thanks again

Jimthomas

---

### Post by kyphi on 2007-05-03
Look forward to reading of your success, Jim.  Ubuntu is a great operating system and well worth the effort of getting it to work like it was intended.

---

