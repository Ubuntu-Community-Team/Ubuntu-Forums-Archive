---
title: "accessing home files on hdd from live cd  ***PLEASE HELP ***"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Jason Weiss on 2007-02-16
Please help me, 

I am haveing this problem? [http://ubuntuforums.org/showthread.php?t=318484&highlight=logon](http://ubuntuforums.org/showthread.php?t=318484&highlight=logon)

this is the 2nd time it has happened to me. 

Well anyway I hacve given up on trying fix the problem and I am happy to  reinstall ubuntu. 

But before I reinstall I need to back up my phots etc of me HDD. 

How can I mount the system files on my HDD on my live cd.

---

### Post by louis_nichols on 2007-02-16
If I remember correctly (I'm not at my ubuntu machine right now) it's pretty easy. You go to System>Administration and there you should find an option for Storage media or something like that. Once you open it, you will have information there about the available hard drives and partitions on the machine. For each partition, there is a simple button that makes it accessible. Sorry that I don't remember the exact paths and button captions. I haven't used it in a while.

---

### Post by Jason Weiss on 2007-02-16
Oh So close but so far......

Can anybody give me a little more detail?

---

### Post by konst88 on 2007-02-16
First check which partition it is:
sudo fdisk -l
Then mound it to an existing directory. Assume the partition  is /dev/hda1, and /media/myHome exists:
sudo mount /dev/hda1 /media/myHome
Good luck!

---

### Post by c00ch on 2007-02-16
Alternatively open terminal and enter

```
sudo fdisk -l
```

This will give you a list of all hard drives/partitions (they're listed as **/dev/hda**, **/dev/hdb** - two hard drives - or **/dev/hda1**, **/dev/hda2**, etc. - two or more paritions).

Create a new folder on the Desktop and mount the hard drive/partition your interested in with **mount**, e.g. you want to mount partition 1 on hardrive 1 the command looks like this

```
sudo mount /dev/hda1 /home/ubuntu/Desktop/THE_FOLDER_YOU_CREATED

```


After that you can access the drive's content in the folder on your desktop. Note: this'll give you read-only access, but I figure that's all you need to rescue your pics.

---

### Post by shareMenaPeace on 2007-02-16
Ok try this

start gparted

system -> administration -> GNOME partition Manager

Than see what the device is called where the /home resist
Also open /media/  and make a folder here for a mount point.
```

mount /dev/hdc1 /media/yourfoldername
```

---

### Post by shareMenaPeace on 2007-02-16
Ok try this

start gparted

system -> administration -> GNOME partition Manager

EDIT:
nevermind use fdisk -l :)

Than see what the device is called where the /home resist
Also open /media/  and make a folder here for a mount point.
```

mount /dev/hdc1 /media/yourfoldername
```

---

### Post by Jason Weiss on 2007-02-16
you guys are great this works perfectly 


thank you

---

