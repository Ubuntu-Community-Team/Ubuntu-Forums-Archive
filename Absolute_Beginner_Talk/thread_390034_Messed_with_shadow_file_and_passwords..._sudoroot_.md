---
title: "Messed with shadow file and passwords... sudo/root now broken"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Huntz23 on 2007-03-21
OK, this may seem really odd and me fiddling with things I ought not too, but it was there like the big red do not push button.

I was fiddling around in the password and shadow password file and disturbed the password somewhere along the line for root.

now when I try anything sudo I get this error

mybox@home:~$ sudo -i
sudo: no passwd entry for root!

recovery console is rendered unusable also do to the fact that it cant run as root.

any ideas I can fix this?

anything would be great and if I come up with a solution I will post.

---

### Post by aysiu on 2007-03-21
> **Huntz23 said:**
> OK, this may seem really odd and me fiddling with things I ought not too, but it was there like the big red do not push button.

I was fiddling around in the password and shadow password file and disturbed the password somewhere along the line for root.

now when I try anything sudo I get this error

mybox@home:~$ sudo -i
sudo: no passwd entry for root!

recovery console is rendered unusable also do to the fact that it cant run as root.

any ideas I can fix this?

anything would be great and if I come up with a solution I will post.
Have you tried this? ```
sudo passwd root
```

---

### Post by Huntz23 on 2007-03-21
yes I tried that and I still come up with the same response no passwd for root.

---

### Post by aysiu on 2007-03-21
Can you explain in more detail exactly what you did with passwords and the shadow file?

---

### Post by Huntz23 on 2007-03-21
well i hadn't read the rootsudo page yet and had looked at altered the password for root and tracked it to shadow.  so if I altered the md5 then thats prolly why its boogered. so maybe both files are shot. and with out su or root or sudo there is no way to alter the file.

---

### Post by aysiu on 2007-03-21
I'm not sure how to fix that.

I've moved your posts to their own thread and tried to give it an appropriate title in the hopes that someone more knowledgeable can help you restore your shadow file.

---

### Post by toorima on 2007-03-21
Did you use sudo vipw for passwd and vipw -s for shadow to edit the files or did you usa a regular texteditor?
If you used the vipw there are backups that you can restore. 

If not what does 
cat /etc/passwd | grep root 
give ya? Do you have a root entry in the passwd file?

can you still do normal sudo, like 
sudo cat /etc/shadow | grep root
?

if you can still do normal sudo what does 
sudo diff /etc/passwd /etc/passwd-
and 
sudo diff /etc/shadow /etc/shadow-
give you?

If normal sudo works and u get something out from the diff commands then you should be able to fix it with the following commands, but make backups first
sudo cp /etc/passwd- /etc/passwd
and 
sudo cp /etc/shadow- /etc/shadow

If regular sudo won't work, boot up a live-cd, mount the disk, then you can do the changes.

In the future when editing files I recommend making  backups and don't log out from the root account your editing from, start up another shell and try root from there or use ssh and try so you don't look yourself out

Hope its any help

good luck.

---

### Post by Huntz23 on 2007-03-21
> what does
cat /etc/passwd | grep root
give ya? Do you have a root entry in the passwd file?
mybox@home:~$ cat /etc/passwd | grep root
#root:x:0:0:root:/root:/bin/bash

> can you still do normal sudo, like
sudo cat /etc/shadow | grep root
?
mybox@home:~$ sudo cat /etc/shadow | grep root
sudo: no passwd entry for root!

looking for my live cd now.

And thanks for moving me to a more appropriate spot aysiu.

---

### Post by Huntz23 on 2007-03-21
ok, now this might sound a bit thick of me, but how do I mount my linux drive?


heres what I get...

root@ubuntu:~# mount /dev/hdb1
mount: can't find /dev/hdb2 in /etc/fstab or /etc/mtab

okay so I nano into fstab and input..

Linux /dev/hdb1 Linux

and I get....

root@ubuntu:~# mount /dev/hdb1
mount: unknown filesystem type 'Linux'

so I guess linux sneaks one past me again, how do I mount my drives to my livecd kubuntu

---

### Post by X-626 on 2007-03-21
For that, you would probably want to try this (I left out sudo since you seem to already be running the commands as root): ```
mkdir /media/hdb1
mount -t ext3 /dev/hdb1 /media/hdb1
``` (You could change the /media/hdb1 to whatever you want)

That would work if you kept your filesystem as ext3 (which is default).

---

### Post by Huntz23 on 2007-03-21
Uereka

With help from X-626 I mounted my linux part and examined my passwd and shadow file and found that at some point I must have deleted root line comepletely from the passwd file.  Entered one and viola, it works.  So thank you all for the patience and time.  At least with my carelessness I learned some things.  One of them being that this forums does indeed rock..

so thanks again toorima, asyiu, and X-626 for the help

---

