---
title: "The dreaded Suspend Failure.  Can anything be done?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2007-11-06
Hi,

My Dell M1210 laptop seems to suspend just fine in XP or Vista.  I know the laptop can suspend just fine in Windows.

In Ubuntu 7.10, I cant seem to suspend properly.  The system goes down, but it doesnt come back (black screen upon return).  

Any ideas on how to fix it?

Thanks,
Rich

---

### Post by NonPapa on 2007-11-07
As far as I'm aware, none of the following work in Ubuntu:
- suspend
- hibernate

Don't know whether there is a fix for these though. :-(

NP

---

### Post by RichTJ99 on 2007-11-18
Its strange, the suspend feature works perfectly on my Dell notebook (the one i am using) in a dual XP/Vista + Ubuntu Gutsy environment.  Everytime I close the lid in XP it goes into standby, everytime I open it up, I am back!  

I wish it worked for 7.10...

---

### Post by nick_h on 2007-11-18
Does it actually resume but just the screen is blank?

What video card do you have?  Have you got Desktop Effects enabled?

---

### Post by RichTJ99 on 2007-11-18
Hi,

I think it comes back to a blank screen but its tough to tell whats happening.  I have a Nvidia Geforce Go 7400 card & I have desktop effects enabled.  

Thanks,
Rich

---

### Post by justsomedude on 2007-11-18
[This wiki entry]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend") helped me to fix similar problems with an Nvidia GeForce Go 6100, maybe it helps you, too...

---

### Post by RichTJ99 on 2007-11-19
Thanks for the advice but that didnt fix it for me.  

Any other suggestions?

Thanks,
Rich

---

### Post by houstonbofh on 2007-11-20
Does it work properly with desktop effects disabled?

---

### Post by tristan on 2007-11-20
> **RichTJ99 said:**
> Hi,
In Ubuntu 7.10, I cant seem to suspend properly.  The system goes down, but it doesnt come back (black screen upon return).  


Mine does exactly the same, xfce/gnome/compositing effects. 

If I hit ctrl-alt-F7 after resume, I eventually get back to my desktop, but can't actually do anything as none of my partitions are functioning.

I've yet to see a fix for the loss of drives, but maybe someone has one? Pretty please?

---

### Post by anaconda on 2007-11-20
have you got enough swap?

are you supposed to have it the amount of 2xRAM for suspend to work? 
(I dont remember)

---

### Post by GrumpyBob on 2007-11-20
I have two laptops.  I use suspend, but not hibernate.
On the IBM Thinkpad R52, I have a clean install of Gutsy, with Compiz Fusion effects enabled.  Suspend seems to be fine - I close the lid, the laptop suspends.  I open, it and it resumes.
On the Sony Vaio TX5XN, I have Gutsy (upgrade from Feisty), using Beryl.  Suspend/resume does work, but sometimes needs a bit of "persuasion" by stroking the touchpad!

Robert

---

### Post by RichTJ99 on 2007-11-21
Bob,

What is the type of video card in your two systems?

Thanks,
Rich

---

### Post by RichTJ99 on 2008-01-30
Just curious if anyone has figured out this issue?  I admit I have not used Ubuntu as much due to it.

---

