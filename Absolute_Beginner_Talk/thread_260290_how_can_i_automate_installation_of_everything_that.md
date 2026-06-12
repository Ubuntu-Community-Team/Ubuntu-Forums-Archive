---
title: "how can i automate installation of everything that i need?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by p.i.m.p on 2006-09-18
hi! i installed ubuntu to mess around with it and then ended up completely replacing windows.. would now consider myself as an intermediate user but i keep breaking up my system and have to reinstall every few days ](*,) i generally keep a backup of /var/cache/apt/archives and then copy it over to my new installation so that i dont have to download all the packages again.. now,i was wondering whether i could make a script and put in the commands for all the software that i need to install?

example: - 
```

#!/bin/bash
sudo apt-get install gftp --yes
sudo apt-get install nvidia-glx nvidia-kernel-common --yes
sudo nvidia-glx-config enable

```

would this work? thanks in advance!

---

### Post by Brunellus on 2006-09-18
you'll want EasyUbuntu or Automatix.

---

### Post by p.i.m.p on 2006-09-18
but automatix doesnt have everything i need..

---

### Post by bswilson on 2006-09-18
> **p.i.m.p said:**
> i was wondering whether i could make a script and put in the commands for all the software that i need to install?

example: - 
```

#!/bin/bash
sudo apt-get install gftp --yes
sudo apt-get install nvidia-glx nvidia-kernel-common --yes
sudo nvidia-glx-config enable

```

would this work? thanks in advance!

Sure, that'll work.  However, you'll be interrupted with Y/N prompts on some packages.  I bet there's a way around that but I can't remember it.  O:)

---

### Post by p.i.m.p on 2006-09-18
i tried looking at the apt-get manual.. it says that the --yes option will answer yes to all questions

---

### Post by f1sh3r on 2006-09-19
hey hey. i've been doing the same thing. i've installed ubuntu probably 4 times in the past week.

is there a way i can back up all the updates onto a cd so i dont have to go through the hour of updating every time? also, that would make it alot easier for installing on other machines.

---

### Post by p.i.m.p on 2006-09-19
backing up the updates is pretty easy.. all the updates that u get with apt-get, synaptic and the update utility are stored in /var/cache/apt/archives

you could burn this folder to a cdrom and then, after reinstall, paste the contents into ur archive folder..

---

### Post by rccharles on 2006-09-19
> **p.i.m.p said:**
> hi! i installed ubuntu to mess around with it and then ended up completely replacing windows.. would now consider myself as an intermediate user but i keep breaking up my system and have to reinstall every few days ](*,) 

You could backup you main partition and then restore it as needed.


I'll use the Unix dd command.   

Let's say that you have two partions.  hda1 and hda2.

Here is the general idea.  I give the generalized idea of the commands ... not the exact syntax.

1) Boot up a live cd
2) umount /dev/hda1  
3) I assume hda2 is mounted on /media/hda2
4) dd if=/dev/hda1 of=/media/hda2/partitioncopyhda1

the restore line would be:
dd if=/media/hda2/partitioncopyhda1 of=/dev/hda1 bs=16000b


Here is another example where I compressed the partition data (actual lines copied from my mac ):

# first off zero out the unused sectors.
cd to the disk0s9 partion

dd if=/dev/zero of=zeroeddata
rm zeroeddata

#
# you can start up another terminal session an watch how big 
# zeroeddata gets.  I didn't have any problem letting zeroeddata 
# file the partition space on MacOS.  You situation could be 
# different.
#
# The disk zeroing is optional.


dd if=/dev/disk0s9 | gzip >a-disk0s9macos10-4.gz

gunzip -c a-disk0s9macos10-4.gz | dd  of=/dev/disk0s9 bs=16000b

disk0s9 means disk zero with partion number 9. You'll have to cd over to the output partition and umount the input partion.

Robert

---

### Post by p.i.m.p on 2006-09-19
i did try the tar based backup method which was posted somewhere else in these forums, but after restoring my /home partition, i always faced the same problem.. i couldnt login using gdm.. some problem with permissions.. let's say i took a backup of the /home partition using this method and then restored it, would the ownership of my files be preserved? or would the user who gave the command to extract from the archive own the files?

---

### Post by rccharles on 2006-09-19
> **p.i.m.p said:**
> i did try the tar based backup method which was posted somewhere else in these forums, but after restoring my /home partition, i always faced the same problem.. i couldnt login using gdm.. some problem with permissions.. let's say i took a backup of the /home partition using this method and then restored it, would the ownership of my files be preserved? or would the user who gave the command to extract from the archive own the files?

There may be same hidden files.  See:
 ls -al



Each file has a uid and a gid.  You can see these via:
 ls -l

The actual uid and gid are numeric values.  Do:
 ls -ln


I read through the man pages.  See:
  man tar

Seems if you extract as a regular user, it will set your uid and gid.  If you are root it will set what is in the file.  Seems like tar will save either numeric value or character value for an input file depending on parameters.

Robert:rolleyes: ;)

---

### Post by tagra123 on 2006-09-19
partimage makes real nice backups

---

### Post by jISh on 2006-09-19
You do realize you can download the Point Release version (latest) which contains most of the recent updates. 

Also, instead of reinstalling every time you break your system, why not try and learn how to fix it? You'll gain a much better knowledge of Linux if you apply yourself to these situations.

---

### Post by p.i.m.p on 2006-09-20
i did try to fix it, the last time, i did something to my system because of which mplayer took about a minute to launch.. i couldnt find anything despite spending hours searching on the internet.. lol im going to try using dd based backup method as described by rccharles.. thanks a lot for all ur replies..  :D

---

### Post by bluefrog on 2006-09-20
As someone else suggested, you can use partimage to have an image of a working ubuntu you are pleased with.

have a look at apt-proxy for keeping all what you download accessible to other machines as well.

James

---

