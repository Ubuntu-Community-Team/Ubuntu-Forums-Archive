---
title: "How do I find my other HDD in Kubuntu"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by johnthemong on 2007-10-27
I have installed kubuntu onto my main computer because i was thinking of putting LMCE on to. Previously I've used Ubuntu 6ish on an old laptop and had few problems finding my way onto various partitions. But now I'm really stuck.

My machine is running two SATA hdds. One was fitted at the time I installed kubuntu7.10 and also has an XPmce installations on it. I later put in the second and have formatted it using Gparted as fat32. Only problem is, I can't figure out how you find it in the files system so put stuff onto it.

Also, if i'm not going to bother putting LMCE on, should i just put the standard Ubuntu on instead of this Kubuntu? Advice greatfully received.

---

### Post by taurus on 2007-10-27
Open a terminal and run

```
sudo fdisk -l
```
That is a lower case letter l, not number 1.

---

### Post by kyphi on 2007-10-27
You will have to mount the drive in order to use it.

"sudo fdisk -l" will find it but is only the first step in making it usable for you.

Have a look at [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) for a very good walkthrough.

---

### Post by johnthemong on 2007-10-27
I hate to say it but I'm no further along. I can see it using the fdisk -l command and I've created a directory like that website told me to but there I ran into trouble. Basically I just don't know how to mount it into that directory or how to change the permissions.

All that fstab stuff didn't mean anything to me to be honest and I take it that's where I change the permissions but surely I need to mount it before I can even do that.

Am i right in thinking that my next step has to be to mount the drive? if so, will I then be able to access it via it's mount point whenever i want though the file browser or will I have to mount it every time I boot up?

thanks for your help.

---

### Post by taurus on 2007-10-27
If you just post the output that I have asked, I could walk you thru it.  Otherwise, you just have to do it yourself then.

---

### Post by johnthemong on 2007-10-27
Sorry. Didn't realise you that was what you meant. Here is the response i got. The disk I'm trying to use is the sdb1. I'm hoping to mount it in a /dump (I think). Cheers. 

john@linux-beast:~$ fdisk -l

Disk /dev/sdc: 2063 MB, 2063597056 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         251     2015200    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(249, 254, 63) logical=(250, 225, 38)

Disk /dev/sdd: 2063 MB, 2063597568 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         250     2008093+   b  W95 FAT32
john@linux-beast:~$

---

### Post by johnthemong on 2007-10-27
just realised it's sdd1 not sdb1. May need glasses. That's what you get for using your TV as a monitor.

---

### Post by taurus on 2007-10-27
Open a terminal and edit /etc/fstab

```
kdesu kwrite /etc/fstab
```
and add this line to the end of it.

```
/dev/sdd1   /dump   vfat   iocharset=utf8,umask=000   0   0
```
Save it and exit kwrite.  Now, create a new mount point if you haven't done so and mount it.

```
sudo mkdir /dump
sudo mount -a
df -h
(You should see /dev/sdd1 is now mounted to /dump.)
```

---

### Post by johnthemong on 2007-10-27
I think I may have made a mistake there. I copied your code to the bottom of the file your comand opened and then saved it. The rest is included below.

Thanks again by the way.

john@linux-beast:~$ sudo mount -a
[mntent]: warning: no final newline at the end of /etc/fstab
john@linux-beast:~$

---

### Post by taurus on 2007-10-27
You need to put an empty line at the end of /etc/fstab.  So, go back and edit /etc/fstab and put a new line to the end, after the line that you just added in.

---

### Post by johnthemong on 2007-10-27
the only thing is now i can't seem to get in to edit it. 

john@linux-beast:~$ kdesu kwrite /etc/fstab
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by taurus on 2007-10-27
Try using a text editor like nano.

```
sudo nano -Bw /etc/fstab
```
Move the cursor to the right of the last 0 and hit Return to create a new line.  Then, save it with <Ctrl>o and exit with <Ctrl>x.  

Then, reboot.

---

### Post by johnthemong on 2007-11-03
Just wanted to say thank you Taurus. I finally managed it today. I think I may have given myself problems by having some removable disks plugged in. However I went back into that Nano and changed sdd1 to sdb1 and added that line and now all seems to be fine. You've been a massive help. I can't thank you enough. 

Just one more question, how do I go about learning to do things like that? I don't really know what it was i did except that we edited a file that controls permissions for something in a directory. I really want to know because I want to convince my school to dual boot our ICT suite with Edubuntu but it will turn into a nightmare if we can't administer simple things like that. If you know of a good book or website that has down to earth tutorials to take someone like me from clueless to competent, please let me know. I've convinced my self we can rebel against Bill and most of my class are on side but the staff will be a much harder nut to crack. They still call me out for problems like starting the computer before the projector so the graphics card doesn't mount. 

Enough from me. Cheers again.

---

### Post by taurus on 2007-11-03
You can go to your local bookstores and check out their Linux book section or grab the one you like from amazon.com.

[http://www.amazon.com/s/ref=nb_ss_gw/002-6876280-4381638?url=search-alias%3Dstripbooks&field-keywords=ubuntu+linux&x=18&y=21](http://www.amazon.com/s/ref=nb_ss_gw/002-6876280-4381638?url=search-alias%3Dstripbooks&field-keywords=ubuntu+linux&x=18&y=21)

---

