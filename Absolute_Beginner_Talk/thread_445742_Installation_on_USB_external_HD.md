---
title: "Installation on USB external HD"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by ghosting0 on 2007-05-16
I'm somewhat bored and had some time on my hands so I decided to attempt an installation on a Seagate 80GB HD that I have mounted in an external USB drive bay. The installation started just fine but seemed to be slower than usual and eventually froze at about 80%. I'm just curious if anyone has successfully done this. I mean, is there an obvious reason why it shouldn't work? I'm not looking at the external USB drive as a viable installation option, I'm just curious.

---

### Post by laidback on 2007-05-16
At around 82%-84% 7.04 seems to be looking for an internet connection, if you have a splash screen with skip on it press it and see if the remainder of the installation goes OK. Updates through synaptic can happen later.

---

### Post by ghosting0 on 2007-05-16
Ok that makes sense. I don't recall a splash screen appearing but perhaps I just need to be patient. Will try again and post the results.

---

### Post by ghosting0 on 2007-05-16
Ok I tried again and still did not have any joy. At 15% done I get a "Failed to create a file system" error which reads "The ext3 file system creation in partition #1 of SCSI3 (0,0,0) (sdc) failed."

I did a little reading and found out that there is some sort of bug to do with USB hard drives (I'm trying to install 6.10 by the way). It was recommended that I use GNOME Partition Editor or GParted to first partition the drive. I tried using GNOME Partition Editor but I still received the same error. Very frustrating stuff.

---

### Post by laidback on 2007-05-16
frustrating I agree. Gparted is very good so there is something up here with the USB drive. I use a USB drive (just for data) and started with 6.06LTS then 6.10 and now 7.04, I'm sorry to tell you that I've never had a problem, I even have a partition for XP on it, NTFS. Gnome partition editor is Gparted. You could download the Gparted live CD (google search gets it) and burn iso to cd. This has a more up to date version of Gparted which I use in preference to the Ubuntu one. It'll format USB Memory sticks too. Then try to partition the drive, if you get errors here then something more fundamantal seems wrong, not a Ubuntu issue.
Could I encourage you to move to 7.04....I find it really good, better than 6.10 I would suggest.

---

### Post by ghosting0 on 2007-05-17
I think I'll go with your suggestion and just do a clean installation of Feisty. I was planning on installing 6.10 and then just upgrading to 7.04 but it seems as if the other way would be best.I would try the LiveCD of GParted but that seems like a lot of effort when I can rather just install 7.04. Thanks for all of your thoughts :)

---

### Post by laidback on 2007-05-17
Best wishes, let us know how you get on.

Laidback

---

