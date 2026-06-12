---
title: "Trying to load 64bit 7.1 on NEW machine"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by gene5746 on 2008-02-13
I am going to try Linux,through Ubuntu, for the first time. Actually tried Mythbuntu 7.1. I have all new hardware; Gigabyte GA-M61P-S3, AMD 6400+ Dual Core,  XFX gForce 8600, 3x Deskstar 500GB (for Raid 5), 2x DVD Recorders, Hauppauge PVR500, Avermedia Combo PCIe, 4GB Ram.  I can run Live CD but want to install Ubuntu on Raid 5 but it keeps accessing each drive independantly. Is this how Ubuntu does it?  Where is source for good starter reading?  BTW - I am willing to put in a good amount of time learning so I get it right but if I make mistakes I won't mind starting again. I built this machine just for my "Linux" experience.:?:

---

### Post by BrentMlady on 2008-02-13
Are you sure that you set the drives up on a raid 5.  Normally the raid card will make the OS think that there is only one drive on the setup.

---

### Post by jrsutton on 2008-02-13
He doesn't seem to have a RAID card. I can only assume he has onboard RAID (fake RAID). My understanding also is that you would need to recompile the Ubuntu kernel to add a particular version of dmraid for RAID 5. I have been able to triple boot XP, Vista, Gutsy with RAID 0 on the EVGA 680i which also uses an onboard controller. It took me 2 day non stop reading a lot of posts and articles as I had never used Linux in my life.

---

### Post by gene5746 on 2008-02-15
You are correct about the onboard raid, but it is set up as R5 and Windows can see this during install (I only tried this to make sure Raid WAS setup.  If I can't use the onboard raid then I won't be able to have a raid configuration?

I'm also trying to find some good reading on Ubuntu (& Linux in general) command line syntax so I can get familiar with it without having to search for help on every topic I encounter.   I'm pretty good at reading & learning from books & manuals.  I memorize very quickly & I will be playing with the system at the same time to speed my learning curve.

Thanks for the help so far!:KS

---

### Post by simons-photography on 2008-02-16
so do I gather even my onboard gigabyte raid controller (DS3 mobo) won't work ? I want to set up a raid scratch disk

---

