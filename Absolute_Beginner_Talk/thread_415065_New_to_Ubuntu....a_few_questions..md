---
title: "New to Ubuntu....a few questions."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by uthscsa19 on 2007-04-20
I am considering installing Ubuntu on my new computer.  I currently have Windows XP installed on it, and will probably keep it because of certain programs (3ds Max, Photoshop, WoW).  I have read many great reviews of the new version of Ubuntu, and would like to give it a try.  Before I go and install it, I have a few questions.

1.  I am currently running a Raid0 setup on my computer.  Do I need to do anything special to get Ubuntu to recognize this?  In Windows I needed a floppy disk with the drivers at the installation phase for it to even recognize my array.

2.  I currently don't have my hard drive partitioned to install Ubuntu.  Do I have to do this prior to the installation, or is this possible during the installation.  Also, if I decide not to continue using Ubuntu, how hard is it to remove this partition.

3.  My main use for my computer is photo editing.  Is Canon Raw Files supported by F-stop?  Is it possible to run Photoshop in Ubuntu?  Will Ubuntu recognize my Rebel XTi camera when plugged in?

4.  How hard is it to find drivers for all my computer components?

Thank you for you time.  Any help would be greatly appreciated.

---

### Post by Happy_Man on 2007-04-20
1. I think it will...

2. Yes, there is a step in the installer itself that will ask how you want to partition. 

3. Maybe. If it isn't, you can always convert the files using the GIMP.

4. Heh. Drivers? Nah, if Ubuntu doesn't recognize everything (which it definitely should), come back here. We'll help you out. ;)

---

### Post by jvc26 on 2007-04-20
I'd pop onto the livecd and test it out there - things which dont work in the livecd will give you an idea of what you may have trouble with after a full install, after all - try before you go the whole way eh?
Il

---

### Post by uthscsa19 on 2007-04-20
Also, I run a Core2Duo.  Is it better to run the 64 or 32bit version?

---

### Post by fruitsofherwomb on 2007-04-20
You might want to check out gimpshop 
[http://gimpshopdotnet.blogspot.com/](http://gimpshopdotnet.blogspot.com/)

---

### Post by Sef on 2007-04-20
> Also, I run a Core2Duo. Is it better to run the 64 or 32bit version?

32 is better since there are more applications for it.

---

### Post by uthscsa19 on 2007-04-20
Thank you for the quick replies.  Is 50gb partition a good enough amount to give it a 1-2 week trial?  After that I will decide whether to buy an extra hard drive (not apart of the Raid array) and install Ubuntu, replace Windows with Ubuntu or stay with windows.  

Again, thank you for the quick replies.  This is one of the most active and helpful forums I have ever visited.

---

### Post by velkrohed on 2007-04-20
> **uthscsa19 said:**
> Also, I run a Core2Duo.  Is it better to run the 64 or 32bit version?

Use 32 as most likely your Core 2 Duo is not a 64-bit processor. I have a Core 2 Duo 2.4 and I installed the 32-bit version of Ubuntu. Even though there are 2 cores, they are both still 32-bit cores.

*EDIT* Man im a dummy... haha here it is I'm a hardware guy, bought a core 2 duo and never realised it has 2 64-bit cores... ROFL! jfinkels is right =P

---

### Post by jfinkels on 2007-04-20
> **velkrohed said:**
> Use 32 as most likely your Core 2 Duo is not a 64-bit processor. I have a Core 2 Duo 2.4 and I installed the 32-bit version of Ubuntu. Even though there are 2 cores, they are both still 32-bit cores.

I thought **Core 2 Duo** was 64-bit, and **Core Duo** was 32-bit

---

### Post by Drunner611 on 2007-04-20
> **jfinkels said:**
> I thought **Core 2 Duo** was 64-bit, and **Core Duo** was 32-bit

That is correct, be aware of those stupid names.

---

### Post by uthscsa19 on 2007-04-20
From doing a bit more reading about ubuntu I have found some issues on installing it on computers with a Raid0 array.  Is this true?  Is there an easy workaround?  Also, if I decide not to keep ubuntu, how can I go about merging the partition I made for ubuntu back to the windows partition?

Thanks.

---

### Post by rillip on 2007-04-20
50 gigs is much more than enough.  I had it dual booting on this computer when I only had a 40 gig, and it only had 18 gigs with no problems.  It doesn't really need too much space -hence why it can run off a CD.

I could not get Dapper to recognize my camera (Kodak Easyshare) right off the bat, but when I googled it I got a helpful how-to that worked within 20 minutes.  Hardware support is generally very good.

I've not tried installing it on a raid0, so I can't say.

To get rid of the partition, just boot from the live CD again, go through the installation, delete the partition and resize the ones you want to keep.

---

