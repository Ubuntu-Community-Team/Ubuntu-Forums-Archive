---
title: "Here's a new one regarding cd-rom's....I think..."
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by dpzektor on 2007-05-28
I noticed for the first time tonight that I have two "ghost" cd-rom drives in Nautilus. One labeled "CD-Rom 1" and one labeled "CD-Rom 2". They are not physical drives, and give a mount error of course when doubloe clicked. Why are these all of a sudden here? How can I get rid of them?

---

### Post by dpzektor on 2007-05-28
Nevermind. Two new entries in the fstab for some reason. Removed them and all is well again. Guess I'm kind of getting the hang of Ubuntu :)

---

### Post by irish_flu on 2007-05-28
Nice going!  I wonder what made that happen?

---

### Post by dpzektor on 2007-05-28
I *think* I know what happened...

I used Automatix way back when I started, and it has some sort of automount ability (writes to fstab)

Earlier today I was messing with a Sega CD emulator, and actually got Sonic CD (the actual game disc) running in Ubuntu. I think that whatever Automatix is doing to help mount drives saw the emulated sega cd drive(s) as physical ones and created mount points for them. Or, at least that is my uneducated guess :)

---

### Post by dpzektor on 2007-05-31
Weird! I performed a completely fresh install of Ubuntu today, and these two "ghost cd-rom drives" were there again! Why in the world would this be happening???

---

### Post by pappapump on 2007-05-31
You wouldn't happen to have a DVD-Ram installed would you?
Those can ghost fictional drives on all sorts of systems especially the older ones.
Another thing to consider is that you may have made virtual Cdroms and left the images in a mountable extra partition or external/internal Hard Drive and forgot to delete them.
Try searching all of your partitions/drives for iso or mountable CDrom images.

---

### Post by dpzektor on 2007-05-31
No, just have two drives (One DVD, One DVD+/-RW). Very odd. I checked the removable HD I have to see if anything was hidden there, but nothing. It might be worth something to say that this does NOT happen when I install Xubuntu. Either way, Ubuntu sees something, and ends up writing it to the fstab. Kind of annoying actually. When I originally posted this, it did not occur upon install, but rather after some time running Ubuntu. I attributed it to Automatix, and then maybe the emulator I ran...but now I am completely baffled.

---

### Post by Barry Cent on 2007-06-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/77990](https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/77990) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the two drives in Nautilus. However, I did sudo gedit /etc/fstab and could only see the drives that were meant to be there :-(. Any one any ideas how I can get rid of them? BTW its on a fresh install of 7.04. Properties show that they were modified this morning, around the same time that I installed all the updates.

---

### Post by rfurman24 on 2007-06-04
I had this problem too.  I had to "ghost" or "phantom" drives in places>computer. I deleted the /dev/cdrom entries in my /etc/fstab. My understanding is that cd/dvd as well as floppy drives are handled/mounted automatically and do not need /etc/fstab entries. I also understand this to be caused by the latest kernel update. There are a few people on the forum having the same problem. You can find those threads by searching for "phantom" or "fake"

---

### Post by Barry Cent on 2007-06-04
I was just settling down for a nice few hours of reinstalling Ubuntu (again). But to my pleasant surprise, I fixed it!!!
Just in case anyone was in the same position as I was:
I edited the fstab file by running the ```
sudo gedit /etc/fstab
``` command in the terminal. I then thought, I will be reinstalling anyway, so I just went ahead and deleted what I presumed to be my proper DVD drives, which showed as:
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
```
Clicked save, and looked for the drives in Computer, and they were gone. :D
So thanks everyone for your help, I appreciate it very much! I'm sure you'll be hearing from me in the next few days as I have some little problems I would like to share with you, but I don't want to hijack this thread, on such a great forum!
Thanks again!
Barry

---

