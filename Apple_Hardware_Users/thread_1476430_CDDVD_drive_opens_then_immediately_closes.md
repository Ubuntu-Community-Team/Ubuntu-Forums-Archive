---
title: "CD/DVD drive opens then immediately closes"
date: 2010-05-07
forum: Apple Hardware Users
---

### Post by JoeMac42 on 2010-05-07
I have a dual-G4 Mac with a recent clean install of Lucid.  When I hit the keyboard eject key or try to open the drive door from the command line with "eject /dev/cdrom" to try inserting a CD, the drive door opens then immediately closes before I can insert a CD.  I didn't have this issue in Jaunty.  Any ideas?

---

### Post by B_Free on 2010-05-07
Mine too. Just another something to fix. Glad it is just not me.

---

### Post by JoeMac42 on 2010-05-08
Could anyone recommend tests to narrow down the issue?

---

### Post by linuxopjemac on 2010-05-08
what happens with :
```
eject
```
and ```

eject -t
```

[http://ubuntuforums.org/showthread.php?t=1456481&highlight=cd+eject](http://ubuntuforums.org/showthread.php?t=1456481&highlight=cd+eject)

---

### Post by JoeMac42 on 2010-05-08
```
eject
```
causes the drive to open and immediately close

```

eject -t
```
does nothing

```

eject -T
```
causes the drive to open and immediately close

---

### Post by linuxopjemac on 2010-05-08
There is something wrong with this, I have no idea how to solve this. It has to come from upstream (udev).
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/546373](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/546373)

---

### Post by JoeMac42 on 2010-05-08
I posted to the launchpad bug, but I'm not sure it is the same issue.  The problem there appears to be difficulty ejecting a disk.


> **linuxopjemac said:**
> There is something wrong with this, I have no idea how to solve this. It has to come from upstream (udev).
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/546373](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/546373)

---

### Post by linuxopjemac on 2010-05-08
can you give the link to the bug report you posted ?

---

### Post by JoeMac42 on 2010-05-08
It's in the thread that you provided the link for:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/546373/comments/17]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/546373/comments/17")


> **linuxopjemac said:**
> can you give the link to the bug report you posted ?

---

### Post by linuxopjemac on 2010-05-08
It's all with Pioneer drives....

---

### Post by JoeMac42 on 2010-05-08
If so, that might be good news for me. There are lots of Pioneer "Superdrives" out there, especially among Macs.  Perhaps this might draw some attention for a fix upstream.


> **linuxopjemac said:**
> It's all with Pioneer drives....

---

### Post by Frobber on 2010-05-08
I'm running a dual boot on an Imac G5. I have a similar problem where the cdrom/dvd cannot be mounted. I have found that is the disk is installed from OSX side then reboot into linux the disk will be recognized and can be mounted. 
Unfortunatly, if the cd or dvd is ejected and replaced with another the disk displayed onscreen will contain the name of the disk that was in during boot. When mounted the files will reflect what is on the 'new' disk.

---

### Post by linuxopjemac on 2010-05-08
the problem existed before (also Pioneer, but many other types too):
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/280931](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/280931)

---

### Post by linuxopjemac on 2010-05-08
people are working on it:
[https://bugzilla.redhat.com/show_bug.cgi?id=453095#c26](https://bugzilla.redhat.com/show_bug.cgi?id=453095#c26)

---

### Post by JoeMac42 on 2010-05-09
I followed instructions there to edit sysctl.conf and add
ev.cdrom.autoclose = 0
to the end.  I can now successfully load a cd into the drive, but it does not mount.  What should I try next?

---

### Post by linuxopjemac on 2010-05-09
I go to bed now. Maybe I can help you tomorrow. I would ask an2ne. He knows how to do this.
[http://ubuntuforums.org/member.php?u=250019](http://ubuntuforums.org/member.php?u=250019)

---

### Post by JoeMac42 on 2010-05-09
Thanks for the help.  I will check back tomorrow.

---

### Post by linuxopjemac on 2010-05-11
I have Lucid Lynx myself now on a spare partition on my PowerBook. When I have the time, I will dive into this.

---

