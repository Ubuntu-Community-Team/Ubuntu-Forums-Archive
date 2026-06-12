---
title: "Harddrive Help"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by KIFIKA on 2007-02-03
when i first installed ubuntu, i only had 1 harddrive (40 gb). A couple of days ago, i took my old 80gb drive out and put it into my ubuntu computer.

I am using ubuntu 6.10, and i would like to be able to read/write from both hds, but i have no idea how, can any one help? 

also: i have no internet atm, keep in mind

oh. and i also booted from my 5.10 live disk, and used the disk manager to put a shortcut on the desktop so i could veiw files

/dev/hda - 40gb
/dev/hdb -80gb 


thx in adv,

KIFIKA

*typed on a wii :)

---

### Post by taurus on 2007-02-03
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
-or-
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by KIFIKA on 2007-02-03
i get an error after i edit the fstab file & try to mount

'unable to load nls charset utf8.umask=0222

ntfs-fs error (device hdba): parse_options(): nls character set utf8.umask=0222 not found

---

### Post by taurus on 2007-02-03
Can you paste the outputs of these two commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by KIFIKA on 2007-02-03
sry,  i am not using a computer to type this, and my comp doent have internet.

the /etc/fstub, i just put exactly what was in the first tutor but using hdb1 instead of hda

---

### Post by taurus on 2007-02-03
If you look at the error message again, you have a period instead of a comma in there.

```
utf8**[COLOR="Red"],[/COLOR]**umask=0222
```

---

### Post by KIFIKA on 2007-02-03
woo! 

sry, i was using my tv and it looked like a period.

anyway it all works now thanks so much for you time, help, and fast replies.

best regards,
KIFIKA

---

### Post by KIFIKA on 2007-02-03
sorry for the double post, but right  now, its read only, how would i get full access?

---

### Post by taurus on 2007-02-03
> **KIFIKA said:**
> sorry for the double post, but right  now, its read only, how would i chmod it to 777?

It's read-only because you are using ntfs driver.  If you want to write to it, then you need to install ntfs-3g driver.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by KIFIKA on 2007-02-03
kk thanks again!

---

