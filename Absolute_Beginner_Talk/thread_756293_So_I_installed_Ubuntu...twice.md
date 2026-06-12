---
title: "So I installed Ubuntu...twice"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by nasvemos671 on 2008-04-15
Hey all
This is my absolutely first time trying ubuntu, and I installed it last night. Its dual booting with Windows XP X64. I installed it once and it kept having display problems. I'm running dual 8800 gt's with 8 gigs of ddr2 800. I understand that it takes some tweaking with to run at my monitors native resolution which is 1680 x 1050, so what ended up happening was that I installed a whole other partition of Ubuntu again just to see my monitor . That second version is running great now got most of the initial issues resolved;  my question : is there a way that I can 1. Just get rid of the version that had the display problem? 2. How can I distinguish the 2 different partitions so that I delete the right one? 3. Would I still be able to use that  hard drive space? If my questions seem vague I sincerely apologize. :)

Thanks in advance. (Cant wait to start messing with this stuff)

---

### Post by ethoxyethaan on 2008-04-15
try to install Gparted

```
sudo apt-get install gparted
```

Start it up typing 

```
sudo gparted
```

now try to dismount one of the 2 partitions, the one that can get dismounted is the not working version.


im sure thereare better ways than this but its just my 2 cents

---

### Post by Moop on 2008-04-15
You can delete the first partition by using the live cd. Gparted is on there under System-Administration-Partition Editor. You will need to make sure the partition is unmounted to delete it. 

Depending on how you partitioned it, the partition next to the XP partition should be your first install and the partition at the end of the disk would be your second install. The easiest way to tell the difference is move a large file into your home directory on the install you want to keep. Then you will know that the smaller partition is your old install. 

You can then create a new partition from the free space or grow an existing partition.

---

### Post by crjackson on 2008-04-15
> **ethoxyethaan said:**
> try to install Gparted

```
sudo apt-get install gparted
```

Start it up typing 

```
sudo gparted
```

now try to dismount one of the 2 partitions, the one that can get dismounted is the not working version.


im sure thereare better ways than this but its just my 2 cents

+1

---

### Post by nasvemos671 on 2008-04-15
Thanks, gonna try this when I get home after work today.  Hopefully it works.

---

### Post by nasvemos671 on 2008-04-16
getting this message when I enter the commands in the terminal is it supposed to happen?
Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.

---

### Post by nasvemos671 on 2008-04-16
Good news, I got rid of that partition, BUT it still shows up as another OS on the boot loader when I restart/ turn on computer, how do I get rid of that??

---

### Post by cchester on 2008-04-16
You will have to edit grub and delete the entry. I think it as simple as that. If I am wrong everyone please correct me.

---

### Post by nasvemos671 on 2008-04-16
Excuse my nubness, but how exactly do I do that??

---

### Post by kaptengu on 2008-04-16
Edit /boot/grub/menu.lst
Just delete the entries you don't want in the menu. I am sure you will recognize the titles from the boot menu. root (hd0,1)=first harddrive, second partition.

---

### Post by nasvemos671 on 2008-04-16
ah thanks i'm gonna try that. :)

---

### Post by nasvemos671 on 2008-04-16
thanks alot guys. I've now just gotten rid of windows xp completely, gonna delve into this. Probably gonna end up putting xp back on though for other reasons :/
thanks again

---

### Post by kaptengu on 2008-04-16
How is this possible?
Did you remove the partition or just the entry in grub menu?
If it was the later alternative, you probably took away lines similar to these from menu.lst:

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by nasvemos671 on 2008-04-17
Well, either way, I just ran the Windows Live CD and then just deleted every partition and started from scratch. I plan on messing with Vista 64 here this weekend. Wish me luck:)

---

