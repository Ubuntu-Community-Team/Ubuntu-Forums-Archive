---
title: "can't browse my windows partititions"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by topquarck on 2006-04-16
hi all;<br>
i installed ububntu 5.10 yesterday but i have a problem:
i can't browse my windows partitions, when i "ls -l" the "/media" folder; i see the partitions folders are like this "dr-x------"; so only the root can View the contents of my partitions...<br>
I need to solve that problem

thanx all

---

### Post by taurus on 2006-04-16
If you want to browse your Windows partiton, you first need to mount it before you can access it.  If you tell me what partition your Windows is on and I assume it's a NTFS filesystem, then I can show you exactly how to modify your /etc/fstab so it would be mounted automatically upon boot...  If you're not sure what partition it is, this simple command from a terminal (Applications -> Accessories -> Terminal) will show you
```

sudo fdisk -l

```

---

### Post by Mustard on 2006-04-16
Have a look over this general guide on Ubuntu Breezy Badger 5.10.  The section entitled 'Windows' has information relevant to your particular problem.

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

This link below has some instructions on automating the process using a script.

[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

Feel free to ask more questions in here though if you find these guides overwhelming.  Try showing the output from the command above suggested by Taurus, as he has offered to walk you through the process.

---

### Post by aysiu on 2006-04-16
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

