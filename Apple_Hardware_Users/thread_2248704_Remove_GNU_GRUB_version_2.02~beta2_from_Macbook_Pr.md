---
title: "Remove GNU GRUB version 2.02~beta2 from Macbook Pro"
date: 2014-10-16
forum: Apple Hardware Users
---

### Post by ares3 on 2014-10-16
Hi ,

I am a newbie here on the forum. I did search the forum for a solution to my problem and the closest one that I found was this post - [http://ubuntuforums.org/showthread.php?t=1653247&highlight=remove+GNU+GRUB+Mac](http://ubuntuforums.org/showthread.php?t=1653247&highlight=remove+GNU+GRUB+Mac), but the solution was a bit drastic and it was a very old post. 

I had dual booted Ubuntu 14.04 on my Macbook Pro running OS X 10.9.5. When I needed to remove it, I searched extensively for safe removal techniques online and all of them pointed that it would be sufficient to just delete the Ubuntu partition using Disk Utility. I was pretty certain that this wouldn't do the trick with the GRUB that I had installed. But, since I couldn't find any other post highlighting other techniques specific to my case, I went ahead and removed the Ubuntu partition and extended my Mac OS partition. Now, as expected, on booting I have the GRUB command prompt staring at me asking me what I would like to do. From the list of commands available, the "exit" command exits the GRUB and boots Mac OS X correctly (thank heavens for that!). But, I would like to get rid of GRUB and boot directly into OS X. Here is a link to the GRUB error screen on boot up - [https://www.dropbox.com/s/7az5qd83tgxbv7b/GRUB%20error.JPG?dl=0](https://www.dropbox.com/s/7az5qd83tgxbv7b/GRUB%20error.JPG?dl=0)

I would greatly appreciate it if someone could give me inputs to solve this problem. Thank you!

/Ares

---

### Post by rainwalker on 2014-10-19
I was hoping to find the same answer! I followed the instructions at [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy) to install 14.04 and boot via GRUB, but now I want to go back to OS X only. Good to know that I can just remove the Ubuntu partition, but I too would like to know how to (safely) get rid of GRUB.

---

### Post by ares3 on 2014-10-22
No inputs so far from the community. I guess this isn't a common issue? :( Anyway, I was on OS X 10.9 when I posted this thread and with the recent upgrade to 10.10, GRUB seems to be have been wiped clean on the upgrade. However, this is not a good solution to our problem (re-install OS?! :( ) but it seems to have worked just because I upgraded the OS. I hope we get a better solution though; it could help someone in the future.

---

### Post by rainwalker on 2014-10-22
I assume it's not a common issue because most of the dual-boot instructions tell you to use rEFIt/rEFInd rather than GRUB. Unfortunately there doesn't seem to be one canonical (pun intended) source for installation instructions, nor are the instructions kept up-to-date.

I guess I got really lucky because the reason I wanted to get rid of my dual-boot was to install the Yosemite update. So in my case it's two birds with one stone :P

If I ever set up a dual boot again, I'll probably try to set it up via Bootcamp to avoid all of this weirdness. [This StackExchange answer]("https://apple.stackexchange.com/questions/128141/bootcamp-with-ubuntu-linux/128145#128145") makes it sound pretty simple:

> Use Boot Camp Assistant normally to create the partition, then boot into your Linux install media and select the new BOOTCAMP partition as the destination for the install.
This will set the default boot disk as the Linux partition, forcing you to alt-boot to boot into OS X. To reverse this, change your startup disk in System Preferences.

---

### Post by rainwalker on 2014-11-08
ares3, would you mind sharing the steps you took to remove your Ubuntu installation? I have very little experience with partitions on OS X and using Disk Utility. I've attached a screenshot of my configuration; disk0s4 is listed as "Mac OS Extended (Journaled)" and disk0s5 is "Linux Swap". If I click on them, Disk Utility says that neither partition can be modified. However, the little minus sign is not disabled so does that mean I can simply delete those two partitions and extend the "Macintosh HD" one?

---

### Post by rainwalker on 2014-11-28
Well I accidentally got it sorted out.

After closing the laptop lid to put the computer to sleep a few hours ago (was booted into OS X), I came back and upon opening the lid was met with the Ubuntu login screen. Weird, but whatever, I tried rebooting. The computer rebooted, played the startup chime and...nothing. Black screen. I held the power button to force a shutdown and tried again. Same result, I couldn't boot into anything at all. Googling the issue led to many suggestions for resetting the PRAM by holding command + option + p + r while powering on until it chimes twice. I did so, and successfully booted into OS X. However, I was never kicked into GRUB. Apparently resetting the PRAM also resets startup disk preferences (or something like that), which inadvertently reset booting into GRUB at startup. Since the system didn't see my Linux install as a separate disk to boot into, I was essentially left with dead space on my drive that I couldn't access (not that I needed to). To delete the space, I deleted the main partition with Disk Utility just like anything else. However, the swap partition is apparently special. I had to select it, go to the "Erase" tab, select "Mac OS Extended (Journaled)" in the dropdown, and then click the "erase" button. That didn't actually erase it, but it allowed me to erase it from the overall "partition" tab by pressing the "-" button (pressing it before doing everything I just mentioned would have no effect). After deleting those partitions, I was able to expand the OS X partition to take up all of the disk.

Moral of the story: If you end up in this setup and want to get rid of GRUB, (I think) you can reset your PRAM and delete the partitions you don't want. I guess it's also important to note that if you have this setup (using GRUB and all that), you should NOT reset your PRAM.

---

