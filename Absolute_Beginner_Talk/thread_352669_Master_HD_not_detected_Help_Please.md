---
title: "Master HD not detected Help Please"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by lakelovers on 2007-02-03
I don't think this is serious but I'm baffled. I installed a second drive for back ups. When I turned on the computer I got the password screen then next I got "BUUT devide dected. Insert system disk and press F1 to continue." I don't have a system disk. This is a Ubuntu, only computer. So, I went to the bios and got this: 
IDE Primary [none],
IDE Primary Slave [none], 
IDE Secondary Master [ HL-DT-ST GCE-8400S],
 IDE Secondary slave [none].

So, I disconnected the second drive and restored the ribbon cable as it was, direct from the primary drive to the mother board.

I still got the message to insert system disk and press F1 to continue.

I looked at the bios, and now the IDE primary is detected as originally. No primary slave,
IDE slave master is detected [HL-DF-ST-8400S]. I didn't expect that because the second drive is totally disconnected.

How do I straighten this out and get the second drive install correctly?

---

### Post by lakelovers on 2007-02-03
I found a system disk I didn't know I had, so I'm back up. I have a Dell Dimension 2300. Anyway, I still need help getting the second drive installed correctly. I've read many of the posts regarding this but if you have advice for me I would really appreciate your help.

---

### Post by rccharles on 2007-02-03
> **lakelovers said:**
> I don't think this is serious but I'm baffled. I installed a second drive for back ups. When I turned on the computer I got the password screen then next I got "BUUT devide dected. Insert system disk and press F1 to continue." I don't have a system disk. This is a Ubuntu, only computer. So, I went to the bios and got this: 
IDE Primary [none],
IDE Primary Slave [none], 
IDE Secondary Master [ HL-DT-ST GCE-8400S],
 IDE Secondary slave [none].

So, I disconnected the second drive and restored the ribbon cable as it was, direct from the primary drive to the mother board.


There are jumpers on the HD which indicate how the HD is to operate.  Jumper settings indicate:
master
slave
or cable select.

I suspect your hd was shipped as master.  

Newer machines will support cable select.  This means the computer will configure which drive is master & slave.  

Look in your documentation or on the disk to see what jumper means what. 

You can look on your manufactures web site too.


Configure.  I'd suggest trying slave first.


> 

I still got the message to insert system disk and press F1 to continue.



This means that BIOS could not boot your computer. BIOS is suggesting you reinstall your OS.

Robert

---

### Post by rccharles on 2007-02-03
> **lakelovers said:**
> I don't think this is serious but I'm baffled. I installed a second drive for back ups. When I turned on the computer I got the password screen then next I got "BUUT devide dected. Insert system disk and press F1 to continue." I don't have a system disk. This is a Ubuntu, only computer. So, I went to the bios and got this: 
IDE Primary [none],
IDE Primary Slave [none], 
IDE Secondary Master [ HL-DT-ST GCE-8400S],
 IDE Secondary slave [none].

So, I disconnected the second drive and restored the ribbon cable as it was, direct from the primary drive to the mother board.


There are jumpers on the HD which indicate how the HD is to operate.  Jumper settings indicate:
master
slave
or cable select.

I suspect your hd was shipped as master.  

Newer machines will support cable select.  This means the computer will configure which drive is master & slave.  

Look in your documentation or on the disk to see what jumper means what. 

You can look on your manufactures web site too.


Configure.  I'd suggest trying slave first.


> 

I still got the message to insert system disk and press F1 to continue.



This means that BIOS could not boot your computer. BIOS is suggesting you reinstall your OS.

Robert

---

### Post by lakelovers on 2007-02-03
Thanks for your response. I did jumper for slave on the second drive but it didn't change the response I got. Also, the system disk I used turned out to be for Windows which I do not have on the computer. When I have the second drive connected the system disk doesn't work to boot the os. When I disconnect the second drive the same system disk boots ubuntu through the master drive. One reference says that Dell recommens cable select but that hasn't worked or I don't know how to set the jumpers for cable select. The drive I'm installing is a Western Digital and following their jumper directions. I have no idea where I go from here.

---

### Post by lakelovers on 2007-02-04
Thanks, again, Robert. . . 
I blundered into making it work. I jumpered the new disk the same as the master which I believe set up the two drives by "cable-select." Now, all I have to do is partition it and mount it? Don't know about the later since the disk is recognized as /dev/hdb. I'm going to set up one partition. I'll use the second disk for back up. It's only 6.1 g which I think will be enough because I don't have mountains of photo or music files.
Jerry

---

### Post by rccharles on 2007-02-05
> **lakelovers said:**
>  Now, all I have to do is partition it and mount it? Don't know about the later since the disk is recognized as /dev/hdb. I'm going to set up one partition. 

Glad you sorted things out.

:) 

For partitioning and formatting, see:

system > administration > disks

The system will want you to enter your logon password.

disk manager is a little simplistic.

some people like gparted

applications > accessories > terminal

sudo aptitude install gparted

enter your logon password

gksudo gparted

enter your logon password

Robert

---

