---
title: "dual boot...big mess"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by daniz70 on 2008-03-03
Hi everybody 
i think i made a big mess with my wife brand new notebook   hp 530 intel centrino duo with Windows Vista basic home edition preinstalled...my purpose was to install ubuntu 7.10 and choose for every boot if run vista or ubuntu.. But something went wrong don't really know what but at the boot i lost WIN Vista...
Hoping to fix everything I enclose some screenshots that could be useful for the solution.

THANKS IN ADVANCE TO YOU ALL UBUNTU FANS

---

### Post by glennric on 2008-03-03
Your second screenshot doesn't help.  Type
```
sudo fdisk -l
```
Note: That is a lower case L, and not a 1 after the dash.

---

### Post by Stang94 on 2008-03-03
I also had that same problem I even added the lines into Grub and directed it to my vista but still was a no go my only option was to wipe it all and start over but again it happened ubuntu was the only option in grub . I then wanted to test something out I installed XP and then ubuntu no problem grub found XP and added it to the options . My set-up is Dell 5150 and my boot order is I have XP on the first harddrive and ubuntu on the 2nd harddrive . I know not much help but wanted you to know your not alone in the problem .

---

### Post by jken146 on 2008-03-03
Could you post menu.lst in its entirety please?  Just type **cat /boot/grub/menu.lst** and copy-paste the output here.

Also please post the output of ```
sudo fdisk -l
```
That is a lower case letter L, by the way.

---

### Post by Stang94 on 2008-03-03
I am just curious if it has something to do with the way vista has its lousy boot manager and seems to play havok with grub

---

### Post by daniz70 on 2008-03-03
i give you the    sudo fdisk -l

Thank U all

---

### Post by zerhacke on 2008-03-03
It's a known bug that you cannot resize a Vista NTFS partition.  Microsoft has changed something in the filesystem between Server 2003 and Vista.  If you resize a Vista partition you destroy it.

The easy workaround is to install Vista, not using the whole disk for the Vista partition, and then install Linux in the unused space.

---

### Post by daniz70 on 2008-03-03
Nooo...so i have to FORMAT the entire hard disk?
but how couuld i insall vista if i had no cd...it was already installed

---

### Post by Miljet on 2008-03-03
Quote
It's a known bug that you cannot resize a Vista NTFS partition.

I beg to differ. I am working now on a Toshiba P205 laptop with Vista and Ubuntu sharing the same drive. The Vista was pre-installed and I simply shrunk the NTFS partition and used the empty space to install Ubuntu and a swap partition.

---

### Post by glennric on 2008-03-03
You don't have an NTFS partition on your system.  You only have an extended partition.  If I had to guess, I would say you installed Ubuntu over Vista's primary partition.

---

### Post by daniz70 on 2008-03-03
ok my english is not that good and i'm pretty ignorant on NTFS partition...SO THIS IS THE QUESTION...
what am i supposed to do?
please speak easy as u can

---

### Post by glennric on 2008-03-03
I am not sure if there is anything you can do.  What I am trying to say is that I believe your windows vista installation is gone for good.

---

### Post by zerhacke on 2008-03-03
> **Miljet said:**
> I beg to differ. I am working now on a Toshiba P205 laptop with Vista and Ubuntu sharing the same drive. The Vista was pre-installed and I simply shrunk the NTFS partition and used the empty space to install Ubuntu and a swap partition.

What version of Ubuntu are you using?

Did you shrink it with Ubiquity or another application?

---

### Post by glennric on 2008-03-03
> **zerhacke said:**
> What version of Ubuntu are you using?

Did you shrink it with Ubiquity or another application?

Did you even look at the output of "sudo fdisk -l" he gave?  There is no NTFS partition.  No Windows Vista.  Even vista can't run from purely an extended partition.

---

### Post by Stang94 on 2008-03-03
I agree you will have to reinstall vista which is hard if you dont have the install disks all you need is a copy of vista weather its a upgrade dvd or whatever then type in your key and you will be fine . As for ubuntu dual boot i wish I knew how to dual boot vista with ubuntu to I have tried 3 different ways to go about it and to no success . XP and ubuntu on dual boot easy ...Vista and Ubuntu on dual boot not so much fun .. P.S I didnt do the shrinking of drives I used two clean harddrives

---

### Post by daniz70 on 2008-03-03
Ok i got it but before re install i need to format..
Do u have any special advice before formatting? thanx

---

### Post by glennric on 2008-03-03
Are you going to reinstall both Vista and Ubuntu, or what do you want to do?  Your harddrive is kind of a mess by the way.  Why do you have to swap partitions right next to each other?

---

### Post by daniz70 on 2008-03-03
maybe this time i gotta think twice before acting
i'm sure that i want ubuntu and maybe i'm goinng ti install win xp...but don't know 4 sure
I NEED SOME TIME

---

### Post by zerhacke on 2008-03-03
> **glennric said:**
> Did you even look at the output of "sudo fdisk -l" he gave?  There is no NTFS partition.  No Windows Vista.  Even vista can't run from purely an extended partition.

Wonderful, Glennric.  Look at the post I  quoted.  I was not talking to the OP.

---

### Post by Arthur Archnix on 2008-03-03
Hi, I have the same laptop. It's really great with Ubuntu on it. I used to dual-boot with Vista before I kicked the habit completely. 
 
It does look like you've deleted the windows partition. That means Vista is gone. If you didn't create the rescue discs you might still have a recovery partition? It would be something like F10 when starting up, to start a recovery session. It doesn't look like you do, but maybe.

So maybe HP will send you the discs for a small fee?

Of course, Gutsy runs great on this machine, we have a support thread dedicated to it [here]("http://ubuntuforums.org/showthread.php?t=502833").

Lastly, if you do get Vista back on your machine it's relatively easy to resize, it's just a major pain. This is the process:

1. Use Vista to Defragment.
2. Use Vista Partition manager to resize as small as possible.
3. Defragment again.
3. Reboot with a Gparted live cd.
4. Shrink the NTFS partition to desired size OR 75% of current size (which ever is** larger**). For example, If gparted told me my vista partition was 100GB, and I wanted it to be 50GB, I would resize it to 75GB.
5. Create an ext2 partition in the free space.
6. Reboot into Vista

Now go back up to step 1. Keep doing this until you achieve the desired size, except step 5, where you will simply resize the ext2 partition to take up the space freed by shrinking the ntfs.

Remember: Moving, shrinking and editing partitions is dangerous. **Back up important data** because you might lose it!

These steps are slow, but they worked for me the three times I needed to do it. 

Good luck with getting your Vista back!

---

### Post by zerhacke on 2008-03-03
I'll be damned, AA.  See, the last time I tried to resize a Vista partition was with Ubuntu 6.06.  With the LTS version of Ubuntu if you resized a Vista partition you hosed it.  They must have figured out the change to the NTFS filesystem since then.

---

