---
title: "removing windows help."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-22
hey all im trying to remove windows from my  hard drive so i leave linux the entire hard drive.  i changed the windows parition to ex3 (i found several tutorials and not sure if i turn the windows parition to ex3 or delete it entirely and resize the linux partition. i also tried editing the boot/grub/menu.lst. thing is, i have no idea what to remove from the menu.lst. i managed to find this.....

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

do i remove all of that and is there anything else i have to remove or is there anything else i must edit to remove windows?

---

### Post by zvacet on 2007-03-22
Download Gparted Live CD.Whit that tool you can do whatever you need.In your case you will click on windows partition and choose delete.After that you can resize your Ubuntu partition with click on it and choose resize.

---

### Post by noob_saioke45601 on 2007-03-22
well deleted my windows parition and resized the ex3 parition and got an error.

 "Error While Reading Block At Sector 112591639"

i tried resizing 4 times and did the same thing same error. i tried saving the log but it wouldnt let me save.

any ideas whats wrong?

---

### Post by euler_fan on 2007-03-22
Don't try to extend the partition, just make it another regular partition on your HD and (if you are running regular ubuntu) the next time you boot you should get an icon on your desktop that will take you to that part of the HD. Then you can use it for things like backing up files, etc.

Not perhaps the most elegant, but if you want to avoid a complete re-install that is the way to go.

Or you can just back-up what you want to keep and do a clean re-install of Ubuntu on the HD, which will reformat it and start over. Of course, as easy as it is to do that (compared to windows) it will still take a weekend to get everything back on it how you like it.

---

### Post by noob_saioke45601 on 2007-03-22
i see. but i made the empty parition ex3 and restarted... it didnt show up on my desktop or in computer.

---

### Post by euler_fan on 2007-03-22
In that case your situation is more advanced than I am :( I have read the theory but am not confident enough to help do it in practice.

If you don't need the hard-drive space, ignore it. If you do, I know there are other threads (sorry for not being able to provide one) on fstab (I believe that is it) and mounting partitions manually. Alternatively, backup your files and re-install.

---

### Post by Josey on 2007-03-22
Unless I missed something why not just run the install program and select "format the entire disk?"

---

### Post by euler_fan on 2007-03-22
> **Josey said:**
> Unless I missed something why not just run the install program and select "format the entire disk?"

My understanding is that to do so would wipe Ubuntu and their files off the HD during the process of reformatting. Not a bad thing if you are planning a re-install, but not great if you want to avoid that process.

---

### Post by noob_saioke45601 on 2007-03-23
i guess i can wait until v7.14 gets released then ill reinstall everything... thanks anyway.

---

### Post by euler_fan on 2007-03-23
Sorry for not being able to be more help.

---

### Post by mikesignguy on 2007-03-23
in a terminal type

sudo fdisk -l

if see the the old win partiton shows up you can then mount it

us this tutorial

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

