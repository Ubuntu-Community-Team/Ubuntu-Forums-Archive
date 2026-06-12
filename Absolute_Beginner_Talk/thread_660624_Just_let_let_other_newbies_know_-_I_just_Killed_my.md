---
title: "Just let let other newbies know - I just Killed my fresh install of UBUNTU 7.10"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by nitemann on 2008-01-07
:lolflag:

Well I killed it , yep.. Careless .. More like Clumsy goof.. System is running on an OLD PII Clocked up,, beautifully I might had add..  .. Was  not looking and kick the power cord .. when It came back up, I had Permission denied errors 23'00s (03,4,5,6,7,8,9).. I then later found out after I deleted the partition is possible to remount the device as rw? If this is correct can someone please post a how to on this, so us new kids on the block.. Will KNOW BETTER.. Fortunatley, nothing Critical was on the image yet.. Just a Bruised Ego.. We need a Smiley kicking itself in the A## for these type of starter errors.. If I rebuild the Partition , this should correct everything , I hope... also can someone suggest a good HTML editor and WEB page developer for Apache Server?

](*,)

---

### Post by Hospadar on 2008-01-07
quanta plus and bluefish are good html editors/web authoring tools.  if you are looking for something simpler, gedit (the standard text editor) does a good job of highlighting and indenting and whatnot.

---

### Post by tgalati4 on 2008-01-07
I use a tie strap to keep the EIC power cord attached to the back of the power supply.  All it takes is a curious cat or something falling on the power cord (like a book) to pull it out.  Of course if you have a wonky power company then you will experience blackouts regardless.  Make sure you have a working UPS.

As a rule, if you had a power problem and suspect a disk problem, just boot off of the Live CD and run 

>sudo fsck /dev/sda

or 

>sudo fsck /dev/hda

and answer the prompts during the repair process.  

Then boot without the Live CD and you should be back in business.  The ext3 file system is more robust than you think.

---

### Post by nitemann on 2008-01-07
Thanks for the help, I installed MADRAKE 9.2 with all the bells and whistles and its running fine as an HTTPS/FTP and VPN Server. on another Machine I have an OLD DELL 2500 Power Edge Server... Running RAIDS SCSI Drives.. I hope to use it here at home to run and Learn...

---

### Post by oni5115 on 2008-01-07
There is also gPhPEdit which a nice and simple interface as well as Geany if you need to write a lot of perl or java applets/servlets as well as html.  I like both of them since they a bit more straight forward than things like Dreamweaver or Eclipse IDE's.

I think there is something similar to Dreamweaver as well called Nvu, though it might have been replace (or maybe is replacing) Konquerer or something.  (I can't remember very well, I saw in another post asking for ideas for web dev apps.)

And well, I've blown up my ubuntu somewhere around 3-4  times when I was first using it.  :lolflag:  That was back before I started learning how to manually mount my drives and copy over my xconfig.

---

### Post by antoz on 2008-01-07
It is now called Kompozer in the repositories.A
[http://ubuntuforums.org/showthread.php?t=657825](http://ubuntuforums.org/showthread.php?t=657825)

---

