---
title: "Mounting a second Hard Drive"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Josephr on 2008-04-09
I had posted this at the end of another thread that dealt with the same subject but got no responses soooo am starting a new thread on the subject, My post in the other thread went like soo:

Not wanting to start another thread but I have the same problem as this other user, however the suggested method to resolve this does not work for me, I have played with linux on and off for many years and am still none the wiser, Im one of these many peeple that adore gui's and avoid like the plague cli's, soo in as graphical detail as possible Ill begin lol

Ok computer yesterday was running windows and was working a treat, installed linux and upgraded today to ubuntu 7.10. All OS installed in first drive, second drive was ignored. Ok installed Gparted a partition manager and converted second drive with the following details:

Partition: /dev/hdb1 (graphical image of a padlock) Filesystem: ext2 Mountpoint: /media/disk Size 37.27Gb Used 647.24Mb Unused: 36.64Gb Flags: boot

Ok now starting Disk file browser and as you would expect the home folder and file system tree is present, at the bottom is disk which is the newly formatted and partitioned drive. 

I can click on this and present in the drive is folder Lost+found with group:root owner: root and permissions drwx
I Try to copy or cut a file into the drive and with menu the paste function is disabled. In the tree where disk is located I right click on disk and click on properties, in the permissions tab the owner is root, the group is root and as far as folder accesses are concerned they are all greyed out.

Now this is where I get stupid, because root as far as I was concerned was never part of the user creation, I presume this is some sort of default setup, again I tried above and nothing happened.

Please please please can someone shed some light on this for me, as Im still getting to grips with the filesystem in linux

Thank you:)

---

### Post by aeiah on 2008-04-09
you need to set the drive permissions to your user account. right now root is the only allowed user. i dont know how to do this in the gui off the top of my head though ;)

---

### Post by milton1 on 2008-04-09
the drive is mounted to a folder owned by root. you can change it to your user with the chown command ```
sudo chown -r username:groupname <foldername>
```
that should do it, but you may want to double check the -r recursive flag by reading the output of "man chown"

---

### Post by Sidewinder1 on 2008-04-09
Try this, it can't hurt; open terninal:
```
sudo chown -R yourusername:yourusername /media/disk
```

---

### Post by Sidewinder1 on 2008-04-09
Wow, Milton1 obviously types faster than I; not that that's such a feat.  :-)

---

### Post by Josephr on 2008-04-09
Milton1 and Sidewinder1 ehhh ok followed your instruction and got the following responce in terminal

sudo chown -r username:username /media/disk   (replacing "username" with actual username)

Response

chown invalid option -- r 

Before giving me the response It did ask for password for sudo authority which I gave it then the response came.

---

### Post by smartboyathome on 2008-04-09
Push alt-f2, type gksudo nautilus, and then press enter. Go up 1 folder (to /, your root folder). Now go to /media. Right click on disk, and select options, change owner to your username, and group to your username.

---

### Post by john6six on 2008-04-09
I believe you need to use the -R option. The options are case sensitive.

---

### Post by Sidewinder1 on 2008-04-09
+1 john6, upper case R

---

### Post by Josephr on 2008-04-09
Thank you 

That has now worked, however I restarted the computer and found that although the permissions were correct for me, I still had to manualy mount the hard drive, is there a way of connecting that mounting process to the login ?

---

### Post by Sidewinder1 on 2008-04-09
Can't really help with login mounting process; perhaps someone more adept than I,,, However all of your drives, mounted or not should show up in Nautilus; just right click on it and then left click on mount. HTH

---

### Post by kushykush on 2008-04-09
I have two SATA hard drives. The first drive has Windows Vista installed (has three partitions).
On the second SATA drive I had Ubuntu installed.  With GRUB, Ubuntu worked fine as well as Vista.

Yestereday, I added a third SATA drive.  Now Ubuntu does not start after the user login and password window.  All I see is the orange/brown screen.

Vista, on the other hand, had no such problem.  It recognized the third SATA drive and installed it in a few seconds.

How do I get my Ubuntu back on track?  (BTW, I disconnected the third SATA hard drive. Unbuntu still not starting.)

I do not want to reinstall.  My 8.04 beta was working just fine until the hardware was added.  I do not understand why such a simple thing would throw Ubuntu of course? Should this be reported as bug?

---

