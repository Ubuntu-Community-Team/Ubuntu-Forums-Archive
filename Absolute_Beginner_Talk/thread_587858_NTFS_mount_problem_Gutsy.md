---
title: "NTFS mount problem Gutsy"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-10-23
hi. 
after installing Gutsy i noticed in Computer that the other hard disk (NTFS) labeled "Media" showed up (Yaaay) but trying to access it , i get an error that it could not be mounted, and seeing the details i read that i should go in windows and safely remove..etc.. i don't have windows anymore and how could i safely remove a HDD??????????
Anywho i figured i should manually mount it , i folllowed the instructions on [http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585) and after restarting , that "Media" showed up neither in Computer, nor in media/windows.

what to do?
thanks

---

### Post by panti19 on 2007-10-23
bump

---

### Post by louieb on 2007-10-23
That article is over a year old. Linux development moves fast. Kinda like your bump.  Look here [Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php") Theres a page on mounting windows.

Kind of surprised Gutsy didn't automatically add it.  Wat that fresh install or upgrade?

---

### Post by panti19 on 2007-10-23
thanks for the reply.

so. i had windows on this pc with 2 hard drives, one for windows and documents.. and the other for media : movies, music etc...  i backed up my important files on media and decided to do a fresh install of ubuntu on the first hard drive. and that's what i did.
i'm gonna try your advice and i'll tell you what happens :P

---

### Post by dimbulb1024 on 2007-10-23
I had the same problem and ended up have to go to a friends computer mount the hd and then eject it through the toolbar icon. Once I did that it mounted just fine in 7.10. 

I had tried forcing it and editing all sorts of files to to avail.

Good luck!

---

### Post by OhioYJ on 2007-10-23
I use AutoMatix, and it has a tool to automatically install NTFS and FAT32 drives, with read/write privileges.

---

### Post by panti19 on 2007-10-24
okay , so i tried [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

now , the volume appears in Computer but trying to access it , i get:

Cannot Mount Volume
You are not privileged to mount the volume 'Media'.
[OK]


what gives?:(

---

### Post by Qwerty_ on 2007-10-24
To read/write to NTFS drives you have to install some tools for Ubuntu to read NTFS drives.

```
sudo apt-get install ntfs-config
```

Then run

```
sudo ntfs-config
```

Then configure as you require.

---

### Post by panti19 on 2007-10-24
Mounting /windows failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hdb5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hdb5 /windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hdb5 /windows ntfs-3g defaults,force 0 0

should i force? i don't want to install windows just to safely remove the drive and then install ubuntu all over..

---

### Post by louieb on 2007-10-24
> **Qwerty_ said:**
> To read/write to NTFS drives you have to install some tools for Ubuntu to read NTFS drives...

Just check my laptop  Could not get to my XP install after Gutsy upgrade. Didn't check before no reason to.  

Did a Synaptic search on on **ntfs** found **ntfgs-config**. Now I have folder call /windows . I can open it with r/w privlages.  I bookmarked it in Nautilus and all is well. 

Qwerty's  advise should work too.  Look at something called **ntfs-tools** too. 
Can't comment on the force option. Never had to use it.

---

### Post by panti19 on 2007-10-24
ntfs config told me that i need to go in windows and safely remove or force... :(

---

### Post by realvz on 2007-10-24
WTF??

can you try this 
sudo /etc/init.d/dbus restart

---

### Post by Qwerty_ on 2007-10-24
I know the exact error he is talking about I occasionally get it and you have to boot into windows and safely remove your external drive. I don't know what would happen if you forced it.

---

### Post by realvz on 2007-10-24
rem0ve the drive and reinsert it and do 
sudo mount -a

---

### Post by Qwerty_ on 2007-10-24
Exactly what does the -a do?

---

### Post by realvz on 2007-10-24
mount -a [-t type] [-O optlist]

(usually given in a bootscript) causes all file systems mentioned in fstab (of the proper type and/or having or not having the proper options) to be mounted as indicated, except for those whose line contains the noauto keyword. Adding the -F option will make mount fork, so that the filesystems are mounted simultaneously.

(ii) When mounting a file system mentioned in fstab, it suffices to give only the device, or only the mount point.

(iii) Normally, only the superuser can mount file systems. However, when fstab contains the user option on a line, anybody can mount the corresponding system.

[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

---

### Post by sewmyheadon on 2007-10-24
> **panti19 said:**
> Mounting /windows failed.

should i force? i don't want to install windows just to safely remove the drive and then install ubuntu all over..

I had the* same exact problem*.  Strange thing is that this external Firewire drive was used on this machine before upgrading to Gutsy and this machine only runs Ubuntu, so the drive hasn't been used with Windows for months.

**Forcing it worked for me:**

*mount -t ntfs-3g /dev/sda1 media/mydrivename -o force*

Not sure why the upgrade 'broke' the automounting of these drives, but so far, after forcing, it's just fine.

---

### Post by JasonBourneLinux on 2007-10-24
I had the same problem as well- lol when I tried to save something on my drive through openoffice the drive mysteriously re-mounted.

best of wishes!!

---

### Post by Les Oeufs on 2007-10-24
weird. I got the same message, but it recommended that I boot back into windows and safely shut-down. (stupid me just turned my computer off when it was time to do the big format. A lot of stuff has been coming back to haunt me during this format session)

---

### Post by des4ij on 2007-10-28
Same error.... I upgraded and i think it might be the upgrade since it worked without doing anything when i installed feisty from CD... Please help none of the above methods worked for me...

Thank you

---

