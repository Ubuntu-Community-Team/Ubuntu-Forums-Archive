---
title: "mounting a new hard drive"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by guitarmaniac on 2007-02-23
Hey just added a new hard-drive to my computer.
How do I get ubuntu to mount it everytime i boot instead of having to type ```
sudo mount /dev/hdb1 '/home/luke/My Music' -t reiserfs -o notail
``` into a terminal everytime I reboot?

---

### Post by renzokuken on 2007-02-23
you need to add it to your /etc/fstab file.......i dont know the exact line to enter as it depends of filesystem and which access permissions you want.

search the forum for fstab and you'll get some ideas.

---

### Post by guitarmaniac on 2007-02-23
yeah, just need to know the exact command to use.
guess i should do a little of my own research though :P

---

### Post by renzokuken on 2007-02-23
the line could look something like

/dev/hdb1      /home/luke/My\ Music     reiserfs     defaults

but dont take my word for it, i never mounted reiser myself

---

### Post by guitarmaniac on 2007-02-23
yeah i think ```
/dev/hdb1 '/home/luke/My Music' reiserfs defaults 0 0
``` should do it.

---

### Post by DavinT on 2007-02-23
I'm not sure but it should be in fstab's manual.
Maybe check out 'man fstab'

---

### Post by mykalreborn on 2007-02-23
check this out:[http://www.ubuntuforums.org/showthread.php?t=283131](http://www.ubuntuforums.org/showthread.php?t=283131)
;)

---

### Post by xpod on 2007-02-23
And another couple on a great site for explaining many of the basics

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by guitarmaniac on 2007-02-23
ok ```
/dev/hdb1 '/home/luke/My Music' reiserfs defaults 0 0
``` didnt work. I THINK it doesnt like the space in My SPACE Music (could be wrong though).
 I don't really want to change the name if I can help it though.
How do I fix this.

---

### Post by tuhyk on 2007-02-23
I have similar problem. I've just managed to mount the drive and even write it down to fstab. But my problem is that I cannot write or read data unless I log in as root. Could not find a way how to give the permission to normal user

---

### Post by george29 on 2007-02-23
> **guitarmaniac said:**
> ok ```
/dev/hdb1 '/home/luke/My Music' reiserfs defaults 0 0
``` didnt work. I THINK it doesnt like the space in My SPACE Music (could be wrong though).
 I don't really want to change the name if I can help it though.
How do I fix this.

you just need to add a \ in between the My Music.. 

it should read /dev/hdb1 /home/luke/My\ Music reiserfs defaults 0 0

george

---

### Post by renzokuken on 2007-02-23
**guitarmaniac,**

try using /home/luke/'My Music'      or     /home/luke/My\ Music

**tuhyk**

post the exact line you used in the fstab file

---

### Post by george29 on 2007-02-23
> **tuhyk said:**
> I have similar problem. I've just managed to mount the drive and even write it down to fstab. But my problem is that I cannot write or read data unless I log in as root. Could not find a way how to give the permission to normal user

post your /etc/fstab file for people to look at... then they might spot what the problem is.

---

### Post by indytim on 2007-02-23
I'm on Win2k and not accessible to the man pages... I think it is

> $sudo chown /media/<mount point> <userid>:<usergroup>

<mount point> : insert the appropriate name from your /media folder for the partition
<userid> : the user id you log in to
<usergroup> : should be the same as your user id

Corrections from the collective if I'm wrong....

IndyTim

---

### Post by WorldTripping on 2007-02-23
I've been looking at how to mount a 2 partition external HDD.

Found this in the Ubuntu(6.06) help.

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/partitions-booting.html)

Apologies if it's not what you are looking for.

---

