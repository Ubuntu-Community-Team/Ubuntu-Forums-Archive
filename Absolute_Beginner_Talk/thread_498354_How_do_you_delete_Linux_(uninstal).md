---
title: "How do you delete Linux (uninstal)"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Eddy Van Halen on 2007-07-11
Hello

How do you delete Ubuntu ? (linux)?

Cause now I've got it installed in both Hard Drive, i f**ed the previous one. So it stopped working and then I installed it again, I thought it would overwrite the previous files but somehow it didnt. (maybe because by accident i wrote it into different hard drive? )

:-) It fells now like both hard drives, (C And D ) are divided into two,

---

### Post by Bablefish on 2007-07-11
Actually the only way to really do this is find a HDD deleting program.

---

### Post by destructchaos on 2007-07-11
i'm not sure if this is what you're looking for, but you could just wipe booth drives clean and do a fresh install.

---

### Post by FuturePilot on 2007-07-11
Use Gparted and delete all of the ext3 partitions. Make sure you back anything up that you want.

---

### Post by Seisen on 2007-07-11
All you have to do repartition the hard drive that has the Ubuntu you don't want.You can use Gparted to do that. When you repartition the hard drive you can leave it unallocated free space or make it into whatever filesystem you want.

---

### Post by Eddy Van Halen on 2007-07-11
> **destructchaos said:**
> i'm not sure if this is what you're looking for, but you could just wipe booth drives clean and do a fresh install.

Well.... I've just installed windows freshly on sunday and linux yesterday. I'm not in a mood doing all that over again :-)) 

Anyone could help me with clear details how to get rid of it?

---

### Post by Eddy Van Halen on 2007-07-11
Im condused whats ext?

Is 

the progam
'gparted' for linux or windows?

---

### Post by FuturePilot on 2007-07-11
ext3 is the file system that Ubuntu uses. In Gparted you will see the partitions will be labeled by the file systems. Gparted is for Linux. It's on the Ubuntu live CD and it's also available as it's own live CD.[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

---

### Post by rickycodie on 2007-07-11
put your live cd in and go to system>admin> gparted(gnome partition editor) and then delete all the partitions that you want.

---

### Post by Inxsible on 2007-07-11
> **Eddy Van Halen said:**
> Im condused whats ext?
 
Is 
 
the progam
'gparted' for linux or windows?
EXT3 is the file system that Linux uses (there are others, but most use EXT3).
 
GParted is a partition program and is available on your LiveCD for Ubuntu
 
EDIT: Crap !! Too late :rolleyes:

---

### Post by Eddy Van Halen on 2007-07-11
right let me backup my stuff into a dvd data cd
cause im stupid and i allways **** up smth

---

### Post by Djinn Effer on 2007-07-11
My biggest advice is after you fix your MBR only delete/format the partitions with the same software you created them with to avoid issues. Unless it's too late for you to do that and you encounter problems, in which case... You can see what I did to fix it: [http://ubuntuforums.org/showthread.php?t=497205](http://ubuntuforums.org/showthread.php?t=497205)

---

### Post by Eddy Van Halen on 2007-07-11
Unable to delete /dev/sda6 (thats swap linux)

Please unmount any logical partitions having a number higher than 6

what do i  have to do?

---

### Post by Eddy Van Halen on 2007-07-11
I want to delete all the ones that are used by Linux, Keeping green ones (windows xp)

[http://img451.imageshack.us/img451/9352/screenshotjk0.png](http://img451.imageshack.us/img451/9352/screenshotjk0.png)

BUt im not allowed (look above) :/ i get some weird message.

And it says also that the one i just deleted is unnolocated. What do i have to do with it? :S

Ok, now ive got the 1st swap bit deleted and one of the EXT3 deleted. But there's still one of each left that says something bout 'higher than 5 or 6' :S

---

### Post by Seisen on 2007-07-11
Your probably using that swap file and that is why it won't let you delete it.

---

### Post by Bothered on 2007-07-11
Execute (in a terminal):

sudo umount -a
sudo swapoff

---

### Post by Eddy Van Halen on 2007-07-11
> **Seisen said:**
> Your probably using that swap file and that is why it won't let you delete it.
Thats unfair and mean! SO how the hell am i suspose to delete it ? 

At the moment im booting the CD. :S

---

### Post by Eddy Van Halen on 2007-07-11
Good, thank you the thingy with console helped.

I deleted everything that has smth to do with linux.

How am i going allocate em now

[http://img488.imageshack.us/img488/2633/screenshot1ad9.png](http://img488.imageshack.us/img488/2633/screenshot1ad9.png)

do i have to rpess add new, and 32 fat ?

---

### Post by Eddy Van Halen on 2007-07-11
> **Eddy Van Halen said:**
> Good, thank you the thingy with console helped.

I deleted everything that has smth to do with linux.

How am i going allocate em now

[http://img488.imageshack.us/img488/2633/screenshot1ad9.png](http://img488.imageshack.us/img488/2633/screenshot1ad9.png)

do i have to rpess add new, and 32 fat ?
Help me :-) Please. I'm not sure what to do. So I'm just waiting for someone to advice me

---

