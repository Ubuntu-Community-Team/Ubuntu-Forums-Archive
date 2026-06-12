---
title: "Basic question about accessing hard drives"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by hokiewalrus on 2006-11-25
Ok, I just installed 6.10 and I'm very new to Linux, so please bear with me.

I got the system up and running but I can't seem to access any of the other hard drives. I erased, repartitioned, and reformatted the drives using the GNOME Partition Editor and all the file systems are ext3.

I mounted the partitions with the Storage Device Manager, and they are all listed as mounted, the first drive for instance is mounted at /media/hda1

As far as I know I should now be able to access the drives, however I don't seem to be able to. I can't see them under the "Computer" option in the Places menu, and I'm not sure how else to get to them.

If the drives are mounted I should be able to see them, no?

As I said, uber-newb here.

---

### Post by taurus on 2006-11-25
Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.

```
df -h
```
Otherwise, read this...

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by hokiewalrus on 2006-11-25
Here's what I get:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              33G  1.9G   30G   6% /
varrun                760M  132K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
procbususb             10M  128K  9.9M   2% /proc/bus/usb
udev                   10M  128K  9.9M   2% /dev
devshm                760M     0  760M   0% /dev/shm
tmpfs                 760M   18M  743M   3% /lib/modules/2.6.17-10-generic/volatile
/dev/hda1              76G  181M   72G   1% /media/hda1
/dev/hdb1             151G  189M  143G   1% /media/hdb1
/dev/sdb1              92G  189M   88G   1% /media/sdb1
```

I was going over the directions in the link that you provided. Nothing in there seemed to help though. Those entries were already in the /etc/fstab file and nothing help seemed to do much.

---

### Post by taurus on 2006-11-25
If you can't access /media/hda1, /media/hdb1, & /media/sdb1, you are talking about permissions here...  Do you plan to write stuff to those directories?

---

### Post by aysiu on 2006-11-25
The second part of the directions is, once they're in /etc/fstab to mount them and change ownership and permissions on the drive. Did you do that?

---

### Post by steve.horsley on 2006-11-25
I think maybe hokiewalrus doesn't realise there's only one directory tree in Linux. If I'm wrong, I apologise.

Open your home folder with the file explorer, then click up twice, which takes you to the top of the tree. then you can navigete down into the media folder.

When you mount drives in Linux, they get grafted on the the one and only directory tree. You don't get a fragmented collection of different trees like you do in Windows.

---

### Post by hokiewalrus on 2006-11-25
Well, I run

```
sudo chown -R hokiewalrus:hokiewalrus /media
```

but when I try to run

```
sudo chmod -R 755 /media
```

I get the error

```
sudo: must be setuid root
```

I appreciate all the help so far!

---

### Post by aysiu on 2006-11-25
What's the output of this command? ```
groups
```

---

### Post by taurus on 2006-11-25
I would have done something like

```

sudo chown -R hokiewalrus:hokiewalrus /media/hda1 /media/hdb1 /media/sdb1
sudo chmod -R 755 /media/hda1 /media/hdb1 /media/sdb1
ls -la /media

```

---

### Post by hokiewalrus on 2006-11-25
> **steve.horsley said:**
> I think maybe hokiewalrus doesn't realise there's only one directory tree in Linux. If I'm wrong, I apologise.

Open your home folder with the file explorer, then click up twice, which takes you to the top of the tree. then you can navigete down into the media folder.

When you mount drives in Linux, they get grafted on the the one and only directory tree. You don't get a fragmented collection of different trees like you do in Windows.


<<

>>

Ok, so I'm an idiot ](*,) 

Yup, that's indeed what I failed to realize. All I had to do was go to the media folder under the root directory. Doh! 2 weeks of Linux class 6 years ago, I guess most of it didn't stick, although I remember it now, for what that's worth.

I just seemed counterintuitive since the removable drives are located at the top level, seemed like the hard drives should as well. Heh.

Isn't there a saying about the simplest explanation usually being the right one?

---

### Post by steve.horsley on 2006-11-25
Hah! Not an idiot at all. It's one of the most peculair differences between the two, and it's not obvious - it's one of those things that you **have** to be told.

---

