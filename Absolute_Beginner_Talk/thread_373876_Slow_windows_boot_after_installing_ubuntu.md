---
title: "Slow windows boot after installing ubuntu"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-03-01
After I installed ubuntu, my windows loads up much slower.  Is there a way to fix this?  After I installed, windows ran CHKDSK.  Would that cause anything?

---

### Post by ComplexNumber on 2007-03-01
it shouldn't do because ubuntu doesn't affect how fast(or slow) windows loads. after you have selected windows at the boot prompt, windows takes full control.

if run chkdsk perhaps because the lst time you were in windows it wasn't shutdown/rebooted cleanly.

---

### Post by STREETURCHINE on 2007-03-01
how much space did you leave windows on its partition.?

---

### Post by Matt1632 on 2007-03-01
I left it about 25gb.

---

### Post by ComplexNumber on 2007-03-01
25GB is more than enough.

---

### Post by STREETURCHINE on 2007-03-01
yep plenty of space ,so that rules that out.

---

### Post by Matt1632 on 2007-03-01
I timed it.  It takes 2 minutes and 25 second to load from the time I press enter at the GRUB to the time when windows fully loads(including startup apps).  I tested a different computer and it only took about a minute.

---

### Post by steven8 on 2007-03-01
After you resize your partition, windows will automatically run a scandisk.  it's normal.

As far as slow booting, I'm not sure.  Did you do a defrag before partitioning?

---

### Post by Matt1632 on 2007-03-01
Yes, I did several defrags.

---

### Post by kikushima on 2007-03-09
The same happened to me. I did 2 defrags.
The windows startup is definitely slower, Theres even a pause before loading the user password prompt, and the screen goes blank for a couple seconds, and that didnt occurred before.

---

### Post by Invictious on 2007-03-20
GAH, this is alsohappening to me too..
I am also sometimes suffering from Boot Disk Failure
and sometimes even Grub Error 5!


Damn.

---

### Post by etherman on 2007-03-23
Hello. The same thing happened to me, after installing ubuntu. I installed it on a separate hd (10 gb, 5400rpm, ide1 slave), and I use the ntldr boot manager. When I choose windows, it boots much slower than before. And it's not running the disk scanner (or it's hidden somehow). So, does anyone have any ideas about what could be wrong ?

---

### Post by djimmmy on 2007-03-28
Same thing happened to me.
It seems Windows is slow because it tries to analyse the drive that includes Linux.

e.g. : for me:  
C:\ => Windows
D:\ => Windows
E:\ => Ubuntu

When opening a Windows explorer or scrolling into it , it always blocks a few minutes while detecting the e:\.

Also I have the very slow login window apparition problem.

I can not figure out why.:(

---

### Post by djimmmy on 2007-03-30
Nobody has an idea yet ?  :(

---

### Post by oddgoo on 2007-04-05
Happening the same to me!!

---

### Post by oddgoo on 2007-04-10
Might as well detail my situation, any help would be greatly appreciated.

I had Windows Vista, and made a partition for Ubuntu 6.10.
Ive been very happy with it but I still need to access some windows 
applications.

Im using an Acer Aspire 5610Z (80gb, 1gb RAM)

May help to say that when i turn off the computer on Vista, it just hangs on the "shutting down" screen.

---

### Post by djimmmy on 2007-04-11
Oddgoo : I think your problem is not related to the current thread.

---

### Post by IndyBob on 2007-04-11
This may or may not help, but I was having the same problem and searched on CNet XP forums and found this and it helped my system.  I was ready to do a repair of XP and not looking forward to it.

Go into your devise manager and double click on IDE ATA/ATAPI Controllers.  Right click the icon for the channel to which the devise (hard drive) is connected, select properties and then click the Advanced Settings tab.  In the Current Transfer Mode drop-down box, select DMA if Available if the current setting is "PIO Only"  If the drop-down box already shows "DMA if Available" but the current transfer mode is PIO, then the user must toggle the settings.  That is: (1) Change the selection from "DMA if available" to "PIO Only", and click OK (2) Reboot (3) Then repeat the steps above to change the selection to "DMA if Available" and reboot.

I have XP on one drive and Edgy on another so I changed both primary and secondary controls and it helped tremendously.  I have Edgy as the primary drive and XP as the secondary.  My XP drive was showing as PIO and was really slow and locking up all the time.

Hope this helps!

---

### Post by oddgoo on 2007-04-11
Gonna try that right away, thank you, why is it not related? i installed Ubuntu and windows is booting way slower.

---

### Post by IndyBob on 2007-04-11
I don't really know about why, but for some reason when I made the XP hard drive the slave, Windoz made it PIO, so I just changed everything to the opposite that it was, rebooted and then changed everything to DMA and rebooted and all is working much better.  I changed both controllers within the IDE ATA/ATAPI.  The post in the CNet XP forums was about someone's laptop being so very slow and one of the moderators suggested looking at the controllers.  It seems Windoz kicks everything back to PIO if there are more than 4 or 6 errors at boot, or something like that.

---

### Post by Sporkmaster on 2007-04-11
I noticed this too, but when I timed it it turned out that Windows was booting as slow as it always did.... You just get used to it when you only ever use windows

---

