---
title: "Mounting NTFS drive problem"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Visti on 2007-03-30
Hi! I recently tried mounting my secondary NTFS drive using NTFS-3g and everything worked peachy - I added what was needed in fstab and so on, but I just noticed (I don't use the drive that much) that when I opened up the drive at the mounted folder it showed nothing, meaning that it wasn't mounted. Fine, I thought, I'll just mount it again - So, I do a sudo mount hdb5 /media/Media and it seems to go smoothly. 

However, when I try to open the folder Nautilus tells me that I don't have permission to see it. I figured it was because I had to do the ntfs-config again, so I did, but it only showed the lower option (external devices) and the option for read/write on internal devices was blurred out! 

What should I do now? Any suggestions? Here's my output from sudo fdisk -l for good measure:
```
Disk /dev/hda: 163.9 Gb, 163928604672 byte
255 hoveder, 63 sektorer/spor, 19929 cylindre
Enheder = cylindre af 16065 * 512 = 8225280 byte

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/hda1   *           1       19576   157244188+  83  Linux
/dev/hda2           19577       19929     2835472+   5  Udvidet
/dev/hda5           19577       19929     2835441   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 Gb, 122942324736 byte
255 hoveder, 63 sektorer/spor, 14946 cylindre
Enheder = cylindre af 16065 * 512 = 8225280 byte

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/hdb1               2       14946   120045712+   f  w95 udvidet (LBA)
/dev/hdb5               2       14946   120045681    7  HPFS/NTFS
```

---

### Post by MEW on 2007-03-30
Check the permissions on /media/Media

---

### Post by bodhi.zazen on 2007-03-30
If the drive was working, and suddenly is not, most likely is a disk error.

If you run windows, boot to windows and check the drive for errors with your windows utilities.

If not:

```
sudo umount /dev/hdb5
ntfsfix /dev/hdb5
```

man ntfsfix :> ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.

---

### Post by Visti on 2007-03-31
The thing is:: I don't even have Windows anymore, I was just saving it for a possible later Win install. In fact, the reason I was gonna get it working was to remove what I needed to make a clean win install, so I'm probably a bit screwed now..

---

### Post by GSF1200S on 2007-03-31
> **Visti said:**
> The thing is:: I don't even have Windows anymore, I was just saving it for a possible later Win install. In fact, the reason I was gonna get it working was to remove what I needed to make a clean win install, so I'm probably a bit screwed now..

How do you not have windows now? If you dont have windows, than how could you have files on the NTFS partition? To my knowledge there isnt a way to uninstall windows unless you cleaned the partition, in which case all files would be wiped in the process.

NTFS3g sounds like its working fine... its showing you nothing on the drive because there IS NOTHING on the drive. On the bright side you have a clean partition and doing a clean install of windows should be cake.

---

### Post by bodhi.zazen on 2007-03-31
I am not so sure the drive is empty.

Try this :

```
sudo mount /dev/hdb5 /media/Media
gksudo nautilus /media/Media
```

Post any error messages and let's see what you have ...

Again, if you see you data, but have read only access, you have a permissions problem.

If you did not change the permissions, you likely have some disk errors and it is being mounted read only or some such.

If you no longer have windows, take a look at test disk : 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Visti on 2007-03-31
GSF1200S - I have to HDs (Hda and hdb) in Win. The Windows installation was on hda and I used hdb for files and such. So when I switched to Ubuntu I first moved all of the stuff I would like to save to hdb and then installed Ubuntu on hda, wiping it clean. And there you go, a NTFS-partioned drive, but no windows. And now I'd like to basically do the same thing before I install Win on hdb again, but alas it's acting up. Anyway, here goes:

sudo mount /dev/hdb5 /media/Media gives me no output (As expected, I assume)

gksudo nautilus /media/Media gives.. My files! (Odd, since I ran Nautilus as su before and got nothing)

Okay, so I try editing a text file and gedit tells me the file is read only and booting up ntfs-config again only gives me the external devices. So somehow it's being boot as a read only drive. Therefore I can't just change the permissions on the files. But Now I'm getting somewhere I think. Now I just need write permissions..

---

### Post by theninthdimension on 2007-03-31
Visti,

     I don't know if this helps you or not, but here's a link to a reply I put in another thread regarding mounting problems. [http://ubuntuforums.org/showthread.php?t=395947](http://ubuntuforums.org/showthread.php?t=395947)

Jeff.

---

### Post by bodhi.zazen on 2007-03-31
> **Visti said:**
> GSF1200S - I have to HDs (Hda and hdb) in Win. The Windows installation was on hda and I used hdb for files and such. So when I switched to Ubuntu I first moved all of the stuff I would like to save to hdb and then installed Ubuntu on hda, wiping it clean. And there you go, a NTFS-partioned drive, but no windows. And now I'd like to basically do the same thing before I install Win on hdb again, but alas it's acting up. Anyway, here goes:

sudo mount /dev/hdb5 /media/Media gives me no output (As expected, I assume)

gksudo nautilus /media/Media gives.. My files! (Odd, since I ran Nautilus as su before and got nothing)

Okay, so I try editing a text file and gedit tells me the file is read only and booting up ntfs-config again only gives me the external devices. So somehow it's being boot as a read only drive. Therefore I can't just change the permissions on the files. But Now I'm getting somewhere I think. Now I just need write permissions..

The most common cause of this problem, IMO, is, as I have said, errors on the ntfs partition. That is why it being mounted as read only any also why you can not configure the drive with ntfs-config.

If you can not repair it with the tools I gave you in my previous posts, your best bet may be to recover what data you can and convert the partition to a Linux native file system.

---

### Post by dannyboy79 on 2007-03-31
i am trying to compile ntfs-config and I am getting this error:

checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.6 libglade-2.0 hal >= 0.5.2 hal-storage >= 0.5.2) were not met:

No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'hal' found
No package 'hal-storage' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


can anyone help??? and before you tell me to use the repo's shown here: [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-config](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-config), I don't want to because I don't use repo's that aren't trusted by ubuntu.

---

