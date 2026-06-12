---
title: "Just a quick question before install"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by cincinnatus13 on 2008-02-08
Alright, I just want to dual boot XP and Ubuntu and maybe add the KDE and Xubuntu environments later. I'm looking at step 5 of this page- [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) - and I'm wondering which partition this is for. Is this my partition that XP will be on since it is resizing it? Or is this the amount of space I want to use for Ubuntu? I want to set Ubuntu for 10GB while the rest of my 80 gig harddrive will be used for XP.
Any help here is appreciated.
Thanks. :)

Edit: Also, when I run defrag I notice that there is only ~74GB showing. This only means that there is still one partition but that XP has locked the other 6GB right? So I don't already have a 2nd partition or anything right?

---

### Post by Moop on 2008-02-08
Step 5 is showing 2 hard drives of 40gb and 60 gb. If you only have one hard drive then only one will show up in step five. Choose your windows partition and it will give you the option of how much free space you want. 

Defrag your hard drive in XP first for best results. And it's always a good idea to have your important data backed up when messing around with partitions. :guitar:

---

### Post by cincinnatus13 on 2008-02-08
Ahhh, I meant the screen below that, my fault. It has a sliding bar and asks how much you want free for the new partition. My question is: is this for XP or for the NEW partition that I will be using for Ubuntu?

Also, I did backup all of my files to DVD+RWs and thanks for the friendly reminder. :)

---

### Post by Moop on 2008-02-08
Ok, that would be space for the new partition. So 10gigs. :popcorn:

---

### Post by cincinnatus13 on 2008-02-08
Ahh, thank you. Just wanted to make sure before I shrunk my partition of XP to 10gigs. :D

Hopefully I'll be back in a little bit to tell you everything went fine.

---

### Post by ispy on 2008-02-08
if you had more than 10 gigs on XP, it would have prompted you. and if you accidentally did resize your windows to 10 gigs, you could easily bring it back with gparted. it's a very easy to use partition editor.

:) welcome. :)

---

### Post by cincinnatus13 on 2008-02-08
Of course, because nothing can go right the first time...

Alright, got it all going and it was installing and said there was an error. It had to abort the install and I just shut it down. It had already done the partitioning and I know that it was right. I checked the CD and it found 1 error so I assume that was it. I figure I'll just go and erase and reburn the iso to the CD but now I can't get into XP. I go to boot from the hard drive and all I get is a black screen with a "j" and a blinking cursor (quotes only to emphasize what I'm seeing.) So what do I do now to get back to Xp and fix all this?

---

### Post by Moop on 2008-02-08
If you have a XP cd you can boot from that, choose repair and run fixmbr. That should get you back into XP. 

Live CD's with errors can cause all kinds of problems.

---

### Post by cincinnatus13 on 2008-02-09
Wow, definately a brief scare with that one. I just didn't want to have to repair/reinstall XP and all.
Well, the CD I was using didn't even work after I shut it off and tried to restarted so I went to my parents', downloaded a new iso, burnt it, and installed Ubuntu. I figured out how to use the partition manager (since I had already partitioned with the bad CD) and got it to work. Luckily, it recognized the other OS (XP) and now I have both available on boot. My question is, is it normal to have 3 versions of Ubuntu? I've got three options that say 1- something 2- something (recovery) and 3- mem test. Is this correct? Just wanted to make sure the install went well.

---

### Post by happysmileman on 2008-02-09
> **cincinnatus13 said:**
> My question is, is it normal to have 3 versions of Ubuntu? I've got three options that say 1- something 2- something (recovery) and 3- mem test. Is this correct? Just wanted to make sure the install went well.

Yeah we all have that, The first one is regular boot, second one is like Windows "safe mode" to fix serious errors, third one AFAIK checks your RAM for errors, usually you'll only ever need the first one,

---

### Post by cincinnatus13 on 2008-02-09
> **happysmileman said:**
> Yeah we all have that, The first one is regular boot, second one is like Windows "safe mode" to fix serious errors, third one AFAIK checks your RAM for errors, usually you'll only ever need the first one,
Good to know. I figured it was alright, but with all the hassle I had getting it on, it doesn't hurt to be safe.

Thank you to all of you guys/girls for helping me. Had me a bit angry when I couldn't get into XP, but now that all of it is good, I'm off to boot Ubuntu so I can play around with it a little bit. Thanks again. :)

Edit: Moop, they actually changed the setup for Gutsy and now the partitioning is a bit different. For anybody who is reading this, the screen that asks you to select your partition size is for your OLD partition with your original OS on it. Pick however big you want to keep your OLD OS (like XP, etc.) and the rest will be allocated to Ubuntu/Kubuntu, etc. Just a heads up for anybody that might have a question regarding it. Thanks again though Moop.

---

