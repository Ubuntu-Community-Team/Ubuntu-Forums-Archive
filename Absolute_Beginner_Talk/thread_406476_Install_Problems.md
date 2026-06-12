---
title: "Install Problems"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Dtree on 2007-04-10
****Hi,

I installed Ubuntu Edgy Eft for the first time last night. (My first forray with Linux)
 Burned the Iso image to disk and booted from that. Ran the live version for a while and then installed it to its own IDE hardrive (nothing else on the drive) Played around with that for an hour or so and then re -booted and logged back into win XP. Everything worked great.

Tonight I went to log back into Ubuntu and I got the error 22 msg. 
I did some reading on the forums and decided that booting into the xp cd, running recovery and running fixmbr and fixboot might help. Fixmbr was no prob, fixboot gave error no valid drive recognized? 
At that point I logged back into xp and re-formatted the drive I had installed Ubuntu on and then tried to re-install from the CD I had burned the ISO image to.
All menu options I try from the disk result in blinking cursor and nothing else.

I then read some more and decided to try the SuperGrub To fix the Grub installation, that was confusing and I hope I didnt make things worse.

As it sits I can Log into XP just fine but am unable to do anything with Ubuntu.

My system drives I have XP installed on are SATA drives in Raid 0 on the ICHR6

I also Have two IDE drives in raid 0 on the Promise contoller

Plus the one single IDE drive that has nothing on it but the faild Ubuntu install, that has been re formatted with windows and the NTFS file system.

Any help would be greatly apreciated.

Dennis

---

### Post by aysiu on 2007-04-11
There are some older guides about reinstalling Grub, but I think the **Rescue a broken system** option off the Alternate CD might do it now.

---

### Post by Dtree on 2007-04-11
Ok, thanks. Ill search for that,
 I did try the system rescue off the SuperGrub/Gparted CD with no luck

---

### Post by aysiu on 2007-04-11
If not, you can try [one of the older guides](http://ubuntuforums.org/showthread.php?t=24113).

---

### Post by Dtree on 2007-04-11
Ok, Ive been reading through the older guides while Im dl'ing the alt CD.
Looks Like there is a ton of stuff I can try )
Im a little confused still about where to put Grub. I guess it should go on th MBR as I have windows on the system as well. Even though they are on seperate drives?

hehe, I feel very much like a little fish in a great big fish bowl, and now theres at cat staring at me )

Thanks again

---

