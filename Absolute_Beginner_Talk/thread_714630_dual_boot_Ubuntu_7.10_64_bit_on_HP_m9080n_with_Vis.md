---
title: "dual boot Ubuntu 7.10 64 bit on HP m9080n with Vista 64?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by j_l_larson on 2008-03-04
Hello,

I have an HP m9080n with an Intel Core2 Quad CPU Q6600 with 8GB of ram with the 64 bit version of Vista Ultimate running.  I have been having trouble running applications under Cygwin, so I thought I would try dual booting with Ubuntu.  I created 40GB of free space for it using the Vista Partition shrinking tool under the disk management application.

I downloaded the ISO for the 64 bit Ubuntu 7.10 cd image and burned it to a CD.  I rebooted and got the Ubunto introductory screen.  I first tried the first option to install Ubuntu, the screen went black and then a very brief message appeared saying _d* something  out-of-memory.  It happened too quickly to catch the complete message.  Then the screen goes black and the cd churns for a while, then the machine starts beeping loudly like someone was leaning on the keyboard.

I also tried again the second option to boot into safe graphics mode, same thing.  Is there any hope?

Thank you
-Julie

---

### Post by logos34 on 2008-03-04
try the text-mode alternate install cd

---

### Post by j_l_larson on 2008-03-04
> **logos34 said:**
> try the text-mode alternate install cd

Thanks, I'm going to try this now, but one thing that worries me is how the iso file says it's for amd64 (ubuntu-7.10-alternate-amd64).  My machine is using an Intel chipset.  Why does the installer explicitly say it's for amd?  

Thanks
-Julie

---

### Post by NightwishFan on 2008-03-04
The AMD version is for both Intel and AMD.

---

### Post by Tatty on 2008-03-04
Just to leave an explanation... its called amd64 because AMD were the first to bring out the now-industry standard x64 chips.

---

### Post by j_l_larson on 2008-03-04
> **Tatty said:**
> Just to leave an explanation... its called amd64 because AMD were the first to bring out the now-industry standard x64 chips.

Thank you, well, I just tried the text mode version and got the same scary messages

dim_string: out-of-memory...
dmi_...something....oem....: out-of-memory ...
buffer .. something
buffer .. something
buffer .. something
buffer .. something

too fast again to read it, but anyway, this time I got into the text menus okay.  Everything was cool except it didn't seem to know that I had freed up 40 GB for it particularly.  When it got to the disk partitioning part, it seemed like my options were:  Stomp, stomp or stomp?.  This machine has two 500GB hard disks which on windows appears to be one big 1TB disk.  I freed up 40 GB for Linux using the disk partition shrinker, but I'm not sure how to tell the Ubuntu installer about that or even how to find it.

So I aborted the installation until I can figure this out.  Luckily Vista is still there.

Thanks for any thoughts or hints
-Julie

---

### Post by NightwishFan on 2008-03-04
The out of memory stuff. I get that as well on 64-bit Ubuntu, it is more like a declaration than a warning I believe. I remember I found an obscure post with why, however I forget the reason.

Edit: My system works fine.

---

### Post by logos34 on 2008-03-04
> **j_l_larson said:**
> Everything was cool except it didn't seem to know that I had freed up 40 GB for it particularly.  When it got to the disk partitioning part, it seemed like my options were:  Stomp, stomp or stomp?.  This machine has two 500GB hard disks which on windows appears to be one big 1TB disk. 

Sounds like you have a raid0 or dynamic disks setup

---

### Post by j_l_larson on 2008-03-04
> **logos34 said:**
> Sounds like you have a raid0 or dynamic disks setup

Could I do something like, plug in an external hard disk on USB and boot linux off of that?  That would be cool.  Is that possible?

Thanks for all this info
-Julie

---

### Post by j_l_larson on 2008-03-04
> **j_l_larson said:**
> Could I do something like, plug in an external hard disk on USB and boot linux off of that?  That would be cool.  Is that possible?

Thanks for all this info
-Julie

Looks like it is:  [http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/](http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/)

Maybe I'll give this a shot.

thanks everyone

---

### Post by j_l_larson on 2008-03-06
> **j_l_larson said:**
> Looks like it is:  [http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/](http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/)

Maybe I'll give this a shot.

thanks everyone


Looks like this approach doesn't work for 64 bit ubuntu.  I really want to get into 64 bit programming and don't want to spend $800 on visual studio .net.  :P

Thanks for any thoughts
-Julie

---

### Post by squidhm3 on 2008-07-13
Just an FYI, I got the same error too - really more informative as the other person said.  I didn't use the text installer, I just edited the boot parameters and removed "splash" from the options (right after "quiet").  Everything worked fine after that.

As for everything looking like a big 1TB drive, yep you've got RAID 0 setup it looks like.  Not sure what to tell you there, I've had other issues with this box.  I put XP MCE on it vs the Ultimate Vista.  Twice now (MCE and plain Pro) the HD started clicking.  Restoring it to Vista fixed the issue.  What's up with THAT?

---

