---
title: "iMac aluminum: Booting into Ubuntu by default?"
date: 2011-03-10
forum: Apple Hardware Users
---

### Post by mbaucco on 2011-03-10
I have searched for an answer but all I found were ways to force an Ubuntu machine to boot into Mac OS by default, and I wish to do the opposite. :)

I had OS X (10.5) on my mac, so I made a new partition and installed Ubuntu 10.10. I added Refit to see if that would help, but now it just waits for me to choose one. I just want it to automatically boot into Ubuntu unless I declare otherwise.

Thanks!
Matt

---

### Post by fabricator4 on 2011-03-11
> **mbaucco said:**
> I have searched for an answer but all I found were ways to force an Ubuntu machine to boot into Mac OS by default, and I wish to do the opposite. :)


I don't have an answer to your question (PC user) but I just wanted to say that after 1 day of not getting an answer to what would seem a simple question, you might like to try the [Apple Users Forum]("http://ubuntuforums.org/forumdisplay.php?f=328") and see if you have more luck over there.

The PC answer is to configure grub, but I don't think that applies here...


Chris

---

### Post by mbaucco on 2011-03-14
Thanks! Maybe I will give that a shot. It's not really a huge deal, I just wanted to save myself a step. :)

---

### Post by Joeb454 on 2011-03-14
*Thread moved to **Apple Users**.*

---

### Post by mbaucco on 2011-03-21
Is this not possible? Do I have to completely remove the Mac OS to get it to boot into Ubuntu?

Thanks,
Matt

---

### Post by Icovada on 2011-03-21
NO!
You have to go to System Preferences, Startup Disk and you should see various boot disks, corresponding to the partitions.
You just need to click on the Ubuntu one.

---

### Post by Icovada on 2011-03-21
If you see nothing, you can install rEFIt [http://refit.sourceforge.net/](http://refit.sourceforge.net/), a special GRUB for mac systems

---

### Post by mbaucco on 2011-03-21
Thanks for the replies! Unfortuantely, the Ubuntu partition does not show up in the startup disk control panel, and installing refit just made it so I don't have to hold down option to choose my boot OS. Do I have to do anything special to make the ubuntu partition appear in the startup disk control panel?

Thanks,
Matt

---

### Post by mbaucco on 2011-03-30
Still no luck here, do I have to wipe the hard drive so that Mac OS X is completely gone and then install Ubuntu? 

thanks,
Matt

---

### Post by Cpierce on 2011-03-30
I use grub customizer. You can install it here:

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

It allows you to "trick out" your startup, but also pick which OS you want to start as default. 

If you are having trouble getting Ubuntu to boot, you may need to re-install grub from the Ubuntu liveCD. Here is how you do that

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Hope this helps

---

### Post by mbaucco on 2011-03-30
Thanks! Will it help even though it goes through Refit first?

-Matt

---

### Post by entangled on 2011-03-30
You might try opening up refit.conf file and enabling 'legacyfirst'.

See [http://refit.sourceforge.net/doc/c3s3_config.html](http://refit.sourceforge.net/doc/c3s3_config.html)

Note it only means that you put legacy systems as default, instead of Mac OSX. If you can get Ubuntu first on the list of legacy systems then you'll get automatic login to Ubuntu.

---

### Post by mbaucco on 2011-03-30
editing refit.cnf did the job, many thanks! :)

---

