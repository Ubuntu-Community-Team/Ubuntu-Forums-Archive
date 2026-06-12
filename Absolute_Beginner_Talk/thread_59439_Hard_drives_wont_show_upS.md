---
title: "Hard drives wont show up:S"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by rok4him on 2005-08-24
I have absolutely no idea how linux works...let alone ubuntu.....so im completely lost...so here is my problem.....i have windows xp on a sata hard drive in my pc.....then i put 2 15G quantum fireball hard drives in to put ubuntu on one.....when i get it installed successfully only the hard drive that i installed ubuntu on shows up in the computer....and im not even sure of that....i have looked through these forums and found nothing...someone please help me...i cant explore more into this os that seems amazing until i can get these hard drives to show up...all 3 hard drives are ntfs and one is sata...the other 2 are ide.....thanks in advance for the help...

---

### Post by Jussi Kukkonen on 2005-08-24
I'm pretty sure you couldn't have succeeded in installing Ubuntu on NTFS...

I'm not an expert on multiple bootable disks, but I can tell you that even the gurus (who'll respond in a while, I'm sure :) ) would find more information useful. Like: 
* can you now boot to Ubuntu?
* did/do you have the drives visible from XP? from Ubuntu?

---

### Post by evansa4 on 2005-08-24
thats been happing to me i installed linuxs on my 10 gig and then i have a speare 20 gig for storing data and its not showing and all so try and fomat ur pc in fat32 nfts you cant write to its read only

---

### Post by vruum on 2005-08-24
before formatting anything, which wil cause you to lose all your data have you looked at the ubuntuguide?

[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by rok4him on 2005-08-24
Well i guess the hard drive that i installed ubuntu onto was formatted to linux ext3 when it was installed.....so i can boot into ubuntu and everything....i found that in partition magic you can format a hard drive to linux ext3 in windows.....one of the hard drives i want to show up in ubuntu is my main one tho......and i cant just format it all.....i can get the two ide drives to show up in ubuntu but not the sata main one.....i will take a look at that guide....but last time i tried something similar to what it shows me to do there it didnt do anything....but ill give it another shot...

it says this before it tells me what to do on that page ''assumed that /dev/hda1 is the location of Windows partition (NTFS) Local mount folder: /media/windows''

how do i know where my hard drive is i.e. hda1 hda2 etc......???

here is a picture of my /dev folder...it appears to show my hard drives...idk if this is any good info....
[http://putfile.com/pic.php?pic=8/23510265146.png&s=x2](http://putfile.com/pic.php?pic=8/23510265146.png&s=x2)

---

### Post by TristanMike on 2005-08-24
Welcome to Ubuntu :)

Ok, before you continue any further, it's important you know that at this time, you should not try and write to an NTFS drive, partition or whatever. You are in very serious danger of corrupting any and everything that is contained on the drive you try and write to. 

The best way to manage files between XP and Ubuntu would be to have or create a FAT32 drive or partition (respectively) that both OS's can have no problems reading and writing to. The Ubuntu installer can do this.

Why don't you have a look at the wiki on this, [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28partition%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28partition%29) there is a script that should automatically mount your partitions. Or you could do it the manual way too.

Hope this helps a little.

---

### Post by rok4him on 2005-08-25
I went there and was going through the steps and when i got to the part about pasting text into the fstab file....it wont let me because its read only....so i go into the prefrences for that file...but i cant make it so i can edit it because apparently im not the ''owner''......i looked at my accounts permissions and everything is checked....so i should have no problem doing this....and there is only one account on this computer so i dont know what the deal is.....im becoming quite the situation here arent i.... :-?

---

### Post by Jussi Kukkonen on 2005-08-26
[QUOTE=rok4him]I went there and was going through the steps and when i got to the part about pasting text into the fstab file....it wont let me because its read only....so i go into the prefrences for that file...but i cant make it so i can edit it because apparently im not the ''owner''......i looked at my accounts permissions and everything is checked....so i should have no problem doing this....and there is only one account on this computer so i dont know what the deal is.....im becoming quite the situation here arent i.... :-?[/QUOTE]
 Did you try the command in the instructions:
```
sudo gedit /etc/fstab
```
from the command line? (*sudo* gives you root permissions for the editing)

---

