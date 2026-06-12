---
title: "Dual Booting the RIGHT way"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by Fffan on 2006-04-04
So, I've dual booted Breezy and WinXP on a AMD64 system... and I managed to get mp3 codec working (although my PCI soundcard was never recognized) and apt-get'd some eye candy (dont remember which) fine, but I never learned how to compile or install ANYthing via a rpm.tz or whatever file, which, needless to say, as pretty well limited my uses for linux. 

Also, I never figured out how to mount partitions. That is, Windows is installed on C:\ (fat32), and I have media on F:\ (also FAT32, but next time I partition im switched to NTFS) and linus installed on another partition.

Anyway, I have this laptop here (P4) that I plan installing breezy on. I'll be using it for audio recording and editing. So, its a 40gig drive, and I have 20 gigs free. So, what would I have to do to make the linux drive 5gigs and a 15gig media drive, like, should the shared partition be NTFS or ext3 or what? 

I'm still pretty new to linux, but I like it well enough. 

Thanks for any help! links to tutorials will do fine :)

---

### Post by Jason_25 on 2006-04-04
I personally think it's best to create a shared ext3 drive and use an ext2/3 file system driver for windows if you need to access it.

---

### Post by catlett on 2006-04-04
This is a well known how to. [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by MacV on 2006-04-04
[QUOTE=Jason_25]I personally think it's best to create a shared ext3 drive and use an ext2/3 file system driver for windows if you need to access it.[/QUOTE]

Or make the mega drive fat32. You don't want to write to a NTFS drive while using Linux. The write feature to ntfs drives has not been totally figured out yet and you could end up borking the ntfs partition.

---

### Post by Anomaly on 2006-04-04
Im with macV, what I did is just make the partition fat32, you can do that via windows or linux. as for the mounting, you can use the mount command or you can go to "disks" in the menu where synaptic is in the gui. from there you just choose your partition browse for a folder and click mount.

hope this helps,
                          Anomaly

---

### Post by Jason_25 on 2006-04-05
[QUOTE=MacV]Or make the mega drive fat32. You don't want to write to a NTFS drive while using Linux. The write feature to ntfs drives has not been totally figured out yet and you could end up borking the ntfs partition.[/QUOTE]
Who said anything about NTFS?  Ext2/3 is alot better because of it's a "native" filesystem and you don't have to use a umask and make all the files executable if you want to view and edit the partition as a normal user.

---

### Post by jbmalone on 2006-04-05
The original poster did...

---

### Post by Fffan on 2006-04-05
Thanks for the responses.

I said something about NTFS because thats what the drive already is, I need it for the enormous uncompressed video files, does ext3 cooperate with >4gig files?

---

### Post by Jason_25 on 2006-04-05
Yes it does.

---

### Post by MetalMusicAddict on 2006-04-05
I have found that using the ext3 driver for windows was sketchy with writing large files. That is writing to the ext3 drive from windows.

---

