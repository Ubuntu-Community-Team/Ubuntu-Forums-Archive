---
title: "Changing the name of Partition"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by leftybob on 2007-01-21
During the Ubuntu install, I left the name of the mounting directory containing the Windows files as the default name /sda3.
I would like to change it to /Windows.  Is there a simple way to do this?  (I am a real newbie)
Thanks

---

### Post by ComplexNumber on 2007-01-21
do NOT go changing the names of partitions. as you say you are a newbie, i strongly suggest that you don't go down that avenue unless you know what you are doing. you could end up screwing up your partition table in the MBR and REALLY screw things up.

btw what is the reason why you want to change it to "windows"?

---

### Post by bodhi.zazen on 2007-01-21
To be clear, I think leftybob is asking about mount points and ComplexNumber is talking about labels ...

Although I could be confused as well :p

Assuming you (leftybob) want to change the mount point to /Windows ...

Well first the mount point is /media/sda3 and we want to change it to /media/Windows, right ...

right.

You will need to make a new mount point and update fstab:

Open a terminal

when you use sudo you will be asked for a password, enter you log-in password. You will not see text on the screen as you type...

```
sudo umount /media/sda3
sudo rm -r /media/sda3
sudo mkdir /media/Windows
gksudo gedit /etc/fstab
```

This last command opens fstab for your editing.

Look for the entry for /dev/sda3 (with /media/sda3 in the second column ;) )

Change this second column to /media/Windows

That's it, save and exit fstab ...

Now 

```
sudo mount /media/Windows
```

8) , unless I am confused in which case #-o

---

### Post by leftybob on 2007-01-22
That worked great - thanks bodi.zazen.
I apologize to the other responder - I'm sure I didn't express my problem clearly enough.
Thanks to you both.

---

