---
title: "Total rookie question about hard drive permissions"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by adamkelt on 2006-01-13
Hiya!  First post.  I'm a TOTAL ROOKIE WRT Linux, so I need myself some help.

I just managed to install Ubuntu on my XP box as a dual-boot (loves me some gaming), and can get it working.  Don't even ask me about my USB WiFi adapter..  Grr

But, I digress.

I can get into the Gnome environment, and can see the three other partitions that I had in the XP world.  They're named things like hda1, hdb1, etc. I understand that, but I can't open them as the default user.  It tells me I don't have the proper level of permissions.  I can open a terminal and do a **sudo nautilus**, and THAT works, but there's got to be a way to open them up so, for instance, my wife (who knows Linux even less than I do) doesn't have to mess with command line stuff.  But, **sudo chmod 777 /dev/hda1** does 'nt seem to do anything.

Any ideas?  I'm going to be at work until about 5 EST, so I won't be able to try anything out until this evening, but I'd still appreciate some discussion - I'll be checking this off and on today.

Thanks in advance!

---

### Post by frodon on 2006-01-13
NTFS don't support unix rights so the chmod commands will never work with NTFS (or FAT32). Also you have to know that there's no write support for NTFS under linux therefore you will get only read access to your NTFS partitions.

If you wish to access your NTFS partition as a simple user follow this link : [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by kont.raen on 2006-01-13
[QUOTE=adamkelt]Hiya!  First post.  I'm a TOTAL ROOKIE WRT Linux, so I need myself some help.

I just managed to install Ubuntu on my XP box as a dual-boot (loves me some gaming), and can get it working.  Don't even ask me about my USB WiFi adapter..  Grr

But, I digress.

I can get into the Gnome environment, and can see the three other partitions that I had in the XP world.  They're named things like hda1, hdb1, etc. I understand that, but I can't open them as the default user.  It tells me I don't have the proper level of permissions.  I can open a terminal and do a **sudo nautilus**, and THAT works, but there's got to be a way to open them up so, for instance, my wife (who knows Linux even less than I do) doesn't have to mess with command line stuff.  But, **sudo chmod 777 /dev/hda1** does 'nt seem to do anything.

Any ideas?  I'm going to be at work until about 5 EST, so I won't be able to try anything out until this evening, but I'd still appreciate some discussion - I'll be checking this off and on today.

Thanks in advance![/QUOTE]

Hi adamkelt,

if those partitions you are talking about are NTFS, then try the following :

1. open up a terminal and change the directory to /etc

cd /etc

2. create a backup of your fstab, i. e. the file in which partitions, mountpoints etc. are listed

sudo cp fstab fstab-2006-01-13

3. edit the fstab with an editor of your choice (vim, nano or whatever, although gedit might be the best choice, if you're not used to any of the others)

sudo gedit fstab

4. Once you see the file in the editor find the lines that say "ntfs" in the type-section of the entries - just like here :

```

/dev/hda1            /media/win2k           ntfs        defaults     0       0
                                                           ^^^

```


When you have found the line, replace the "default" in the options-section with
"ro,user,exec,umask=000" so that the line(s) look like this :

```

/dev/hda1            /media/win2k           ntfs        ro,user,exec,umask=000     0       0
                                                           ^^^

```

5. Save the changes to the fstab, exit your editor and remount your filesystems

sudo mount -a -o remount

If you are afraid to do this, you can either simply reboot your machine or just unmount and mount the partitions you have changed with an

sudo umount /dev/hdx1
sudo mount /dev/hdx1

for each partition - whereas you have to replace hdx1 the names of your respective ones.

Okay, that should do the trick :)

---

### Post by adamkelt on 2006-01-13
Wow - this looks like it might be a little more painful than I thought.  Grrr.

I'll have to investigate the best way to migrate all my important data over to the Linux install (picture archive, etc), and minimize how many NTFS partitions I have.  Basically, the goal will be to have a Linux box that can boot into XP for pretty much only gaming.

It actually sounds like I might want to back EVERYTHING up that I want to save, then wipe and start from absolute zero....  I'd rather not do that, though.

I'll try this stuff this evening.  Thanks!

---

### Post by frodon on 2006-01-13
If you format one of your partition as FAT32 you will get write/read support with both OS on it this the advantage of FAT32. Disadvantages are that FAT32 like NTFS don't support unix rights and you can't write file > 4Go on FAT32 partitions.

---

### Post by adamkelt on 2006-01-13
[QUOTE=frodon]If you format one of your partition as FAT32 you will get write/read support with both OS on it this the advantage of FAT32. Disadvantages are that FAT32 like NTFS don't support unix rights and you can't write file > 4Go on FAT32 partitions.[/QUOTE]
4Go?  Do I just not understand something, or is this just a typo for GB?

FAT32 can't handle file sizes larger than 4Gig?  I don't think I have much call for that....  I'll have to look into it.

---

### Post by frodon on 2006-01-13
Yes i mean that FAT32 can't handle file which are larger than 4GB, you could have a file larger than 4Go when you rip a dvd, that's one of the disadvantage of FAT32.
But except that FAT32 is a good way to use a partition with both linux and windows.

However if you think that you will use more linux than windows, ext3 could be also a good solution but you will have read access only in windows, there's a write support but it's not enough reliable intensive use..

PS : 1 octet = 1 Byte, maybe only french people use the word octet ... sorry

---

### Post by aysiu on 2006-01-13
[QUOTE=adamkelt]
I can get into the Gnome environment, and can see the three other partitions that I had in the XP world.  They're named things like hda1, hdb1, etc. I understand that, but I can't open them as the default user.  It tells me I don't have the proper level of permissions.  I can open a terminal and do a **sudo nautilus**, and THAT works, but there's got to be a way to open them up so, for instance, my wife (who knows Linux even less than I do) doesn't have to mess with command line stuff.  But, **sudo chmod 777 /dev/hda1** does 'nt seem to do anything.[/QUOTE] See the fourth link of my sig. You'll have to mess with command-line stuff to get it set up, but after that it'll be all point-and-click and accessible to users.

---

### Post by adamkelt on 2006-01-13
[QUOTE=frodon]
PS : 1 octet = 1 Byte, maybe only french people use the word octet ... sorry[/QUOTE]
Ahhhh!!  Thanks!  Makes perfect sense.  :)

---

### Post by adamkelt on 2006-01-13
[QUOTE=aysiu]See the fourth link of my sig. You'll have to mess with command-line stuff to get it set up, but after that it'll be all point-and-click and accessible to users.[/QUOTE]
That looks really good!  Thanks!  That looks like the first thing I'll try this evening.

---

### Post by adamkelt on 2006-01-13
Well, that all seems to have worked.  I can now read all my NTFS partitions just fine.

Thanks!  I've got more questions, but that probably deserve their own thread...

---

### Post by AMD64_N_Linux on 2006-01-13
Linux NTFS support is coming along at a pretty good pace. 

Take a look at 

[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

---

