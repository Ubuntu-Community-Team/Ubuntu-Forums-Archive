---
title: "formatting external drive from windows"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by short3000y on 2007-12-05
hi, i installed ubuntu on an external drive of mine, but now want to remove it because i put ubuntu onto another external with more HDspace on it. but in my Windows XP, when i go to mycomputer, the external drive is not there. is there a way to do a boot and wipe? like boot onto a cd and use a bootable program to wipe the drive so it is usuable again? thank you!

~Nate

---

### Post by BradwJensen on 2007-12-05
> **short3000y said:**
> hi, i installed ubuntu on an external drive of mine, but now want to remove it because i put ubuntu onto another external with more HDspace on it. but in my Windows XP, when i go to mycomputer, the external drive is not there. is there a way to do a boot and wipe? like boot onto a cd and use a bootable program to wipe the drive so it is usuable again? thank you!

~Nate



Get Deluge from  [www.deluge-torrent.org]("http://www.deluge-torrent.org")  then download this 'Portable Partition Magic' with deluge: [http://www.mininova.org/get/790528](http://www.mininova.org/get/790528)

This portable version doesn't require a key to work and doesn't need to be installed, so if there are more files in the torrent; don't open them - Just run the main app in the download on Windows to help you partition that drive then delete the download - it worked for me.. Good luck

---

### Post by ArtInvent on 2007-12-05
Just about any Linux LiveCD like Ubuntu these days comes with a partition editor, GParted. You can boot using this CD, access the HD's and delete/edit partitions etc from that.

---

### Post by quandary on 2007-12-05
You can do it from windows. 

If you use XP:
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

With Vista:
[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

Then install the programs, restart.
Then you give your linux drive a windows driveletter

And you can then format the drive normally from windows explorer...

If your USB drive just doesn't show up, you have to associate a driveletter with your drive.
You can then format it with NTFS from Administrative Tools->Computermanagement

---

### Post by BradwJensen on 2007-12-05
> **quandary said:**
> You can do it from windows. 

If you use XP:
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

With Vista:
[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

Then install the programs, restart.
Then you give your linux drive a windows driveletter

And you can then format the drive normally from windows explorer...

If your USB drive just doesn't show up, you have to associate a driveletter with your drive.
You can then format it with NTFS from Administrative Tools->Computermanagement

Nice, I like your suggestions!

---

