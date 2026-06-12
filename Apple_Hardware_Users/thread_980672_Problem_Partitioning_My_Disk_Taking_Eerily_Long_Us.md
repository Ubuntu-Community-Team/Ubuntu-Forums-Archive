---
title: "Problem: Partitioning My Disk Taking Eerily Long Using Boot Camp"
date: 2008-11-13
forum: Apple Hardware Users
---

### Post by bsonk on 2008-11-13
*Note: I am a Linux n00b, the despised script kiddie who pastes commands into the terminal. I've only had VMs of Linux distros, and I want to run at native speeds, partly for WINE gaming. I have XP, but want to break free of Microshaft. I'm just getting into the GNU/Linux world, and my more knowledgeable friend doesn't want to teach me teh 1337 haxxor terminal skillz, so I can't exactly compile my own code and I ask you to bear with me:

My MacBook Pro Penryn (low end 2.4ghz) has a 200GB HDD in it. Previously, 32GB of this was an XP partition created using Boot Camp. It worked fine. I decided to ditch XP (cloning it to an external should I ever change my mind) and go with Intrepid Ibex for my dual boot. I used Boot Camp to delete the XP part and reformat it HFS+. Then I tried to repartition it, giving Ubuntu 61GB, leaving 41GB free (Leopard's files on the rest). I got a "Files could not be moved" error. Apple wanted me to format my drive and try again. This annoyed me, so I booted from the LiveCD and tried to manually partition by splitting the OS X part. I assumed the partitioner (is it GRUB?) would leave the OS X data alone. Instead it left the partition completely alone, saying that "scanning HFS+ volumes has not been implemented." 

I ended up booting from the Leopard CD and restoring from my Time Machine backup. I had to repair permissions, but otherwise everything was fine. Then I went to school and took notes and everything was rosy. When I came back, I tried to partition for Ubuntu once more. It's now almost midnight, and the evil Apple striped progress bar that doesn't ever actually move is displayed, along with "Partitioning Disk..." This is normal, but is usually supposed to last 30 minutes or less (according to MacRumors forums).

Now I'm writing this on my machine, in a quandary. I don't want to kill the process, for fear of screwing my Leopard install (This wouldn't be a problem if I didn't have to take notes tomorrow in class). I also don't want to leave it going, for fear of having to write a bunch of data to the HDD while it's partitioning. I also want to find out what causes this, fix it, repartition, and install Intrepid on a 61GB partition. This is my ultimate goal. I don't really want to have to reinstall Leopard, but I will if I have to in order to get a Ubuntu part. (For instance if I were to partition using GRUB or Disk Utility and lose my OS X). 

I'm not too worried, but I would love an answer. I have good backups and the worst case scenario is that I take paper notes tomorrow with a (gasp) pencil. For now, I'm leaving the process running.

To recap:
1. Partitioning my disk is taking too long.
2. I'm kinda scared about that.
3. What should I do?
4. How do I fix it if it's wrong?
5. What's the best way for me to install Ubuntu? 

NOTES: I am trying to dual boot using the Dual Boot, no rEFIT method outlined here [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Also, I'm getting many Firefox crashes trying to use Gmail while the partition process is running. Javascript cache/cookie problems?

EDIT: I just saved a text file in Pages and nothing died. Perhaps the error is less grievous than I think? Also, what I previously refer to as GRUB= Gparted.

I have looked on other forums, and the problem could be disk fragmentation, as I have heard that Boot Camp looks for the largest block of free space on the drive and uses that. Should I run a program like iDefrag [http://www.coriolis-systems.com/iDefrag.php](http://www.coriolis-systems.com/iDefrag.php) and then try again?

---

### Post by macghsot on 2008-11-13
Hi,
First i should say "Never partition using boot camp", second if you have a back up of your Leopard then boot from the Mac OS X cd, go to the disk utility and repartition your main hard drive but for the Ubuntu partition don't formated it and make it free space then restore your backup to the mac partition then download rEFIt from [www.macupdate.com](www.macupdate.com) and installed and reboot the system after inserting the Ubuntu cd.

Choose the Ubuntu cd from the boot menu and in Ubuntu let it install in the largest free disk space.

I hope that does the job.

---

### Post by cyberdork33 on 2008-11-13
> **macghsot said:**
> "Never partition using boot camp"
partitioning with bootcamp uses the same tools that OS X uses when you use Disk Utility. There is essentially no difference in using one or the other. (Other than the limitations of bootcamp).

You need to install rEFIt, at least temporarily as it will fix an issue you will have after installation.
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by macghsot on 2008-11-13
hi,cyberdork33

I have a question if i may ask? I've installed ubuntu on an imac 24 and everything is almost ok,but when I open a video file it flickers, and in firefox it plays just fine, what could be the problem?

thanks.

---

### Post by bsonk on 2008-11-13
Thanks. I was hoping I wouldn't have to do this, as my restore process is time-consuming (I have Time Machine backups, which= a very very slow restore). I'll use Disk Utility and install rEFIT. The only reason I didn't install rEFIT is the assertion by other forum members that it's unnecessary if you use boot camp. I'll give it a go.

Update: I killed the partitioning process and it seems to have worked, but Disk Utility (within OS X) only sees its own partition. This is logical due to lack of another OS on the other one, but should it say that I have free space? I think I'll boot from the Ibex LiveCD and get libparted's opinion on the subject.

---

### Post by bsonk on 2008-11-14
I'm now posting this from my 63 GB Ubuntu partition. Thanks for your help.

---

### Post by macghsot on 2008-11-14
congrats.

---

### Post by Zhukov on 2008-11-14
You got it already, but nevertheless...

The problem is caused by lock (or whathever you want to call it) that Leopard (and some applications) do within the HFS+ drive (at least in my case).

iDefrag solved my issue for good.

And helps with performance.

Best regards!

---

### Post by cyberdork33 on 2008-11-16
> **macghsot said:**
> hi,cyberdork33

I have a question if i may ask? I've installed ubuntu on an imac 24 and everything is almost ok,but when I open a video file it flickers, and in firefox it plays just fine, what could be the problem?

thanks.

I really do not know. Likely something to do with the buggy ATI drivers. I would open a new thread for this though.

---

