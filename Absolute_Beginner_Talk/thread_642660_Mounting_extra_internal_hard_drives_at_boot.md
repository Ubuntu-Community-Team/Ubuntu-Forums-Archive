---
title: "Mounting extra internal hard drives at boot"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by AngryMallard on 2007-12-16
I have four hard drives connected to one of my computers, but the three that do not contain the operating system do not mount automatically. However, when I go to System->Computer, it shows "149 GB Volume" "60 GB Volume" and "80 GB Volume" but won't actually mount them until I click on those particular icons. Then the mount points, "/storage1" "/storage2" and "/storage3" show up on my desktop as I click on the volumes listed in "Computer". I need those three to mount at boot, rather than when I individually click on them.

I have been mounting them after I boot manually with 
```
sudo mount /dev/sdb /storage1
sudo mount /dev/sdc /storage2
sudo mount /dev/sdd /storage3
```

Another problem is that two of the drives don't have write access. How do I permanently change them so anyone can write to them?

By the way, this computer is an old Pentium 3 running Ubuntu Gusty.

---

### Post by nowshining on 2007-12-16
n/m

---

### Post by AngryMallard on 2007-12-17
Maybe someone can give me something other than n/m? I've been working on it and nothing seems to help. Although the one drive out of three that isn't restricted is FAT32 and the others are all NTFS. But it is not possible to change them to FAT32 because I have some files 10GB or larger.

---

### Post by jw5801 on 2007-12-17
You need to add a couple of lines to /etc/fstab. This is the file-system table that tells linux what to mount where on boot-up. If you add a few lines that look like this then you should be cooking:
```
/dev/sdb1    /storage1    vfat    defaults    0    2
```
The first entry is the device to mount, second is mountpoint, third is filesystem (vfat corresponds to FAT32), fourth is mount-options and the last two numbers I don't quite remember, but if you run "man fstab" you'll get alot of info about it.

As for getting write access to ntfs drives, Linux can't have this out-of-the-box. NTFS is a restricted format. However if you install the ntfs-3g drivers and then mount the drive with ntfs-3g as the filesystem type then you'll be able to write. The following will do this for you:
```
sudo apt-get install ntfs-3g
sudo mount -t ntfs-3g /dev/sdb1 /storage1
```

---

### Post by nowshining on 2007-12-17
actually gutsy by default should incl. ntfs-3g by default and already have the abiility to write to ntfs partitions via it. By the way the n/m was i said something and then re-read ur post and my suggestion became outdated :/ so i edited and changed it to n/m

---

### Post by A$h X on 2007-12-18
Not sure if I'm getting mixed up, but I have a shared data partition called SHARE, which I would like to automatically open when gutsy boots. ATM I have to goto to places -> computer, then click on the drive and enter my password. Anyway of automating this process?

---

### Post by A$h X on 2007-12-18
Anyone? Usually these awesome forums provide answers within minutes.

---

### Post by lswest on 2007-12-18
Yup, that would be the right command (the one about 4 posts up) which describes how to add entries to fstab would be what you're aiming to do.

---

### Post by Cypher on 2007-12-18
> **A$h X said:**
> Not sure if I'm getting mixed up, but I have a shared data partition called SHARE, which I would like to automatically open when gutsy boots. ATM I have to goto to places -> computer, then click on the drive and enter my password. Anyway of automating this process?
What type of partition in this "Share"?

---

### Post by A$h X on 2007-12-18
> **lswest said:**
> once again, you have to add that entry to /etc/fstab  there is a post about 4 up from the one you posted with instructions on how to do that.  please read before you post.Did you not see where I stated i'm not sure if I was getting mixed up. The reason I didn't make a new thread was I thought this might be a solution to my particular problem. You could have just said "Yes the command will do what you were asking about." 
A refreshing aspect of these wonderful forums is the lack of ego and condescending tone, so please lets keep it that way.
Regarding fstab, a question. Here is my fstab file:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fa0c01ad-7e14-441c-8192-afe094b5477c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=522C246A2C244B75 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=46C0-F9F7  /share          vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=063c9e52-1a50-40d3-91f2-5edae39f578f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Now why does "sda1" (my XP partition) always auto-mount but "sda6" does not? They both seem to have the same options, but SHARE is never auto-mounted. Could someone explain why this is so. Thanks in advance.

---

### Post by lswest on 2007-12-18
sorry about the snappy post, i was a little distracted XD didn't read your post correctly i guess. my apologies.

and @ your post, you sure the mount point exists (e.g. the folder is there?) otherwise you have to make the folder for it with ```
sudo mkdir /share
``` however, generally it's best to keep the mountpoints in /media/ or /mnt/ so that it's all in one place.

and also, not sure if it matters, but the entry for sda6 is missing the nls= before the utf8

---

### Post by mukul_d on 2007-12-18
What are you trying to mount at /share? Are you really trying to mount an external drive at /share? That doesn't sound right to me. Could you please explain?

---

### Post by A$h X on 2007-12-18
Kool, thanks for the help!
I think my definition of "mount" is wrong :redface: 
I just want to be able to access my SHARE partition without having to goto places->computer->SHARE and entering my password. Can't I just edit fstab for that to happen? I looked at the options in man fstab, but command line switches scare me. Actually I see what you mean lswest, maybe nls= would auto-"mount" sda6 at boot?

---

### Post by lswest on 2007-12-18
actually i believe the entire line is necessary for the auto mount, so missing or having an incomplete statement can cause the command to be ignored due to a semantics or syntax error.

---

### Post by meekatron on 2007-12-18
i have just managed to successfully instal a second hard drive on ubuntu gutsy. i am no expert but this is wot i think.
from what i can guess from your posts i think you first need to create folders on your desktop called storage 1, storage2, storage3, 
if you open partition editor it will give you the list of your harddrives the drop down tab at the top right corner.when you click on them  it will tell you what your hard drives are called on the screen. Mine are /dev/sda1 and /dev/sdb1

say storage1 is /dev/sdb1 then find the uuid number for it by typing 

```
ls -l /dev/disk/by-uuid/
```
 
you should see something like this 

```
lrwxrwxrwx 1 root root 10 2007-12-18 16:06 266bf804-2e21-4959-8746-cded3829ff65 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-12-18 16:06 3136-6134 -> ../../sdf1
lrwxrwxrwx 1 root root 10 2007-12-18 16:06 45b40a16-0805-4d3c-a685-b10f4311554f -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-12-18 16:06 f9d93990-0ae1-47b6-b86a-80c416f1d524 -> ../../sda1
```

so the uuid for sdb1 is 45b40a16-0805-4d3c-a685-b10f4311554f

now go to fstab and put in this line(remember to change the uuid and file system)

```
# Entry for /dev/sdb1 :
UUID=45b40a16-0805-4d3c-a685-b10f4311554f /Desktop/storage1 ext3 defaults 0 0
```

save and exit fstab 

then type 

```
sudo mount -a
```

and change permissions 

```
sudo chown -R username:username  /desktop/storage1
sudo chmod -R username /desktop/storage1
```


this worked perfectly for me mounting a ext3 harddrive to "/music" so i should work.

---

### Post by AngryMallard on 2007-12-18
Will using the "chown" command be permanent? I think part of my problem is that they're NTFS drives. I was having to issue those commands every time the computer booted, but I'm not 100% sure that was necessary.

As for the rest of the problem, I changed my fstab so that the two numbers on the end of my three extra drives were 0 2. It said to do that in the man page. 0 0 is for the filesystem and 0 2 is for other drives, at least that was my understanding of it. 

However, now every time my computer boots it does an fsck of all four hard drives which takes about an hour and a half. I either did something wrong in the fstab or need to turn off whatever's telling the computer to run that check every time it turns on.

I'm at work right now but when I get home I'll post my old and new fstabs. (I learned the hard way once while playing with Gentoo: ALWAYS make backups of critical files like that...)

---

### Post by meekatron on 2007-12-18
i dont think the chown commands work for windows filesystems not really sure. 

i also found that if storage1 is a ntfs disk your fstab line would look like 

```
# Entry for /dev/sdb1 :
UUID=45b40a16-0805-4d3c-a685-b10f4311554f /Desktop/storage1 ntfs nls=utf8,umask=0222 0 0

```

or if it is fat32 it should look like 

```
# Entry for /dev/sdb1 :
UUID=45b40a16-0805-4d3c-a685-b10f4311554f /Desktop/storage1vfat iocharset=utf8,umask=000 0 0
```

the read write stuff i don`t know i found this[ link]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html") 
 but not sure if it works with gutsy

---

### Post by jw5801 on 2007-12-18
> **AngryMallard said:**
> Will using the "chown" command be permanent? I think part of my problem is that they're NTFS drives. I was having to issue those commands every time the computer booted, but I'm not 100% sure that was necessary.

As for the rest of the problem, I changed my fstab so that the two numbers on the end of my three extra drives were 0 2. It said to do that in the man page. 0 0 is for the filesystem and 0 2 is for other drives, at least that was my understanding of it. 

However, now every time my computer boots it does an fsck of all four hard drives which takes about an hour and a half. I either did something wrong in the fstab or need to turn off whatever's telling the computer to run that check every time it turns on.

I'm at work right now but when I get home I'll post my old and new fstabs. (I learned the hard way once while playing with Gentoo: ALWAYS make backups of critical files like that...)

Yeah putting 0 0 and 0 2 was about the limit of my understanding as well. It definitely runs fsck on every boot? Anything in fstab should be checked at boot and fsck is normally run every 30th or so mounts (I'm pretty sure those two numbers have something to do with that).

Ok, after some reading, the 6th field (the last number), is used by fsck to determine what order filesystems should be checked on boot. 1 is for the root filesystem, 2 is for others. If the field is not present or 0, fsck will assume that the filesystem does not need to be checked. So there's your solution! Make the lines as follows:
```
/dev/sdb1    /storage1    vfat    defaults    0    0
```
That way fsck shouldn't check them on boot.

---

### Post by jw5801 on 2007-12-18
> **A$h X said:**
> Kool, thanks for the help!
I think my definition of "mount" is wrong :redface: 
I just want to be able to access my SHARE partition without having to goto places->computer->SHARE and entering my password. Can't I just edit fstab for that to happen? I looked at the options in man fstab, but command line switches scare me. Actually I see what you mean lswest, maybe nls= would auto-"mount" sda6 at boot?

So you have a line in /etc/fstab that tells /dev/sda6 to mount to /share? and /dev/sda6 is a FAT32 partition? If so then everything looks to be in the clear, check that everything is in /share after you boot next by using a filebrowser, or by running ```
ls /share
```to list the directory contents. If there's nothing in the folder then it hasn't mounted correctly, so post back and we'll help. If everything is there as it should be then you can create a link to it on your desktop if that would be easier: ```
ln -s /share ~/Desktop/share
```If you get some permission errors or keep getting asked for your password when you try to do things then you might need to run:```
sudo chown -R *your-username* /share 
```But that's a fairly bruteforce approach. chown changes the owner of a particular file and the -R switch makes it recursive, so that command will change everything in the directory so that it's owned by you.

---

### Post by nowshining on 2007-12-18
> **AngryMallard said:**
> Will using the "chown" command be permanent? I think part of my problem is that they're NTFS drives. I was having to issue those commands every time the computer booted, but I'm not 100% sure that was necessary.

As for the rest of the problem, I changed my fstab so that the two numbers on the end of my three extra drives were 0 2. It said to do that in the man page. 0 0 is for the filesystem and 0 2 is for other drives, at least that was my understanding of it. 

However, now every time my computer boots it does an fsck of all four hard drives which takes about an hour and a half. I either did something wrong in the fstab or need to turn off whatever's telling the computer to run that check every time it turns on.

I'm at work right now but when I get home I'll post my old and new fstabs. (I learned the hard way once while playing with Gentoo: ALWAYS make backups of critical files like that...)
external drives with windows type systems, have unknown as the owner, and anyone can access them. I know it's odd tho..

---

### Post by AngryMallard on 2007-12-18
All four of my drives are internal IDE drives.

---

### Post by A$h X on 2007-12-18
> **jw5801 said:**
> So you have a line in /etc/fstab that tells /dev/sda6 to mount to /share? and /dev/sda6 is a FAT32 partition? If so then everything looks to be in the clear, check that everything is in /share after you boot next by using a filebrowser, or by running ```
ls /share
```to list the directory contents. If there's nothing in the folder then it hasn't mounted correctly, so post back and we'll help. If everything is there as it should be then you can create a link to it on your desktop if that would be easier: ```
ln -s /share ~/Desktop/share
```If you get some permission errors or keep getting asked for your password when you try to do things then you might need to run:```
sudo chown -R *your-username* /share 
```But that's a fairly bruteforce approach. chown changes the owner of a particular file and the -R switch makes it recursive, so that command will change everything in the directory so that it's owned by you.
I tried your approach, but the share folder created was empty. If I click on the drive icon named share, then everything's there, but the shortcut folder doesn't seem to be pointing to the SHARE partition. (Screencap attached just to make everything clear). One thing I noticed is that SHARE is NTFS not FAT32, but TBH can't that as a problem as it works fine, just does not auto-mount on boot. How about some mount options that I could just enter into the properties of SHARE? Seems an easy solution. 2nd screencap shows current mount options.

---

### Post by AngryMallard on 2007-12-18
OK here is my current fstab:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=d3c1deb9-8649-4c20-94bf-d3bb0a08d364 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=d5401c56-ff6d-4bd7-a51a-0e7297486921 none swap sw 0 0
##B##/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
##B##/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
##B##/dev/sdb1 /media/hd2 ntfs-3g defaults,locale=en_US.UTF-8 0 0

##B##/dev/sdb1
/dev/sdb1 /storage1 vfat defaults 0 0

##B##/dev/sdc1
/dev/sbc1 /storage2 ntfs defaults 0 0

##B##/dev/sdd1
/dev/sbd1 /storage3 ntfs defaults 0 0
```

And here is my original fstab:
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=d3c1deb9-8649-4c20-94bf-d3bb0a08d364 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=d5401c56-ff6d-4bd7-a51a-0e7297486921 none swap sw 0 0
##B##/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
##B##/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
##B##/dev/sdb1 /media/hd2 ntfs-3g defaults,locale=en_US.UTF-8 0 0

##B##/dev/sdb1
/dev/sdb1 /storage1 vfat rw,user,noauto,exec 0 0

##B##/dev/sdc1
/dev/sbc1 /storage2 ntfs rw,user,noauto,exec 0 0

##B##/dev/sdd1
/dev/sbd1 /storage3 ntfs rw,user,noauto,exec 0 0
```

Currently, the /storage1 is mounted properly on boot, however the NTFS drives, which should mount to /storage2 and /storage3, do not mount on boot. I do have write permissions for them locally now. However, I need write permissions from other computers via samba. How do I give myself that permission?

Oh and I did change it back from 0 2 to 0 0 and fsck no longer runs at boot. Thanks.

---

### Post by nowshining on 2007-12-18
try this unmount both ntfs drives

right-click on menu - edit menus

under system tools find ntfs-3g and check mark it, close out and go into the menus andchoose a mount poing thru it and  and then change them removing ntfs-3g to just ntfs

---

### Post by jw5801 on 2007-12-18
> **AngryMallard said:**
> OK here is my current fstab:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=d3c1deb9-8649-4c20-94bf-d3bb0a08d364 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=d5401c56-ff6d-4bd7-a51a-0e7297486921 none swap sw 0 0
##B##/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
##B##/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
##B##/dev/sdb1 /media/hd2 ntfs-3g defaults,locale=en_US.UTF-8 0 0

##B##/dev/sdb1
/dev/sdb1 /storage1 vfat defaults 0 0

##B##/dev/sdc1
/dev/sbc1 /storage2 ntfs defaults 0 0

##B##/dev/sdd1
/dev/sbd1 /storage3 ntfs defaults 0 0
```

And here is my original fstab:
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=d3c1deb9-8649-4c20-94bf-d3bb0a08d364 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=d5401c56-ff6d-4bd7-a51a-0e7297486921 none swap sw 0 0
##B##/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
##B##/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
##B##/dev/sdb1 /media/hd2 ntfs-3g defaults,locale=en_US.UTF-8 0 0

##B##/dev/sdb1
/dev/sdb1 /storage1 vfat rw,user,noauto,exec 0 0

##B##/dev/sdc1
/dev/sbc1 /storage2 ntfs rw,user,noauto,exec 0 0

##B##/dev/sdd1
/dev/sbd1 /storage3 ntfs rw,user,noauto,exec 0 0
```

Currently, the /storage1 is mounted properly on boot, however the NTFS drives, which should mount to /storage2 and /storage3, do not mount on boot. I do have write permissions for them locally now. However, I need write permissions from other computers via samba. How do I give myself that permission?

Oh and I did change it back from 0 2 to 0 0 and fsck no longer runs at boot. Thanks.

If they're not mounting at boot, what are you using to mount them? As for permissions over samba, I'm not entirely sure. You could try running ```
sudo chmod -R a+rw /storage2
```which should give all users read and write permissions to the folder. Other than that I don't really know. Not all that familiar with samba.

---

### Post by jw5801 on 2007-12-18
> **A$h X said:**
> I tried your approach, but the share folder created was empty. If I click on the drive icon named share, then everything's there, but the shortcut folder doesn't seem to be pointing to the SHARE partition. (Screencap attached just to make everything clear). One thing I noticed is that SHARE is NTFS not FAT32, but TBH can't that as a problem as it works fine, just does not auto-mount on boot. How about some mount options that I could just enter into the properties of SHARE? Seems an easy solution. 2nd screencap shows current mount options.

That "drive icon" on your desktop is a link created by gnome when it's volume manager mounts your drive (which is what the "Computer" menu thing tells it to do). The gnome volume manager will mount filesystems to /media/*label* and then create a link to this mountpoint at ~/Desktop/*label*

If you want the filesystem to automount at boot then you'll need to change fstab. So open it with```
gksu gedit /etc/fstab
```then change the lines that read ```
# /dev/sda6
UUID=46C0-F9F7  /share          vfat    defaults,utf8,umask=007,gid=46 0       1
```It's not actually necessary to use the UUID, and this entry is being ignored because it has a UUID without enough digits. So if you change the line to the following then you might be in a bit more luck:
```
/dev/sda6    /share    ntfs    defaults,utf8,umask=007,gid=46    0    0
```

---

### Post by A$h X on 2007-12-19
I've solved the problem!:KS No need to get down and dirty with gksudo nautilus or chown or editing fstab! You don't even have to use terminal! Just goto to synaptic package manager, and install pysdm!
This lovely little app (27kb!) will give you complete control over your partitions, and SHARE popped up straight after installation and reboot! Again, i've seen many threads about automunting, and lots of advice given, which may or may not work. Just use pysdm and your set. :)

---

### Post by Ampi on 2007-12-20
Does this wonderful little app also incluse internal other harddisks with different OS'??

I have two harddisks and i use one of them (with ubuntu). 
The other one (with fedora 4) I use as storage with other programs. 

I want to be able to acces docs and programs (i guess on remote) without  
1. having to turn off the computer and change the boot order, or 
2. having to look for programs in my nautilus (which doesn't work because I have no writing permissions....).

Anybody have an idea???

---

### Post by A$h X on 2007-12-20
> **Ampi said:**
> Does this wonderful little app also incluse internal other harddisks with different OS'??

I have two harddisks and i use one of them (with ubuntu). 
The other one (with fedora 4) I use as storage with other programs. 

I want to be able to acces docs and programs (i guess on remote) without  
1. having to turn off the computer and change the boot order, or 
2. having to look for programs in my nautilus (which doesn't work because I have no writing permissions....).

Anybody have an idea???

I would assume so, as it sees and manipulates my windows partition and NTFS shared data partition just fine. Try it out, you can always uninstall if it doesn't work.

---

### Post by Ampi on 2007-12-20
I have pysdm now but it still doesn't work. :(

I can see my partitions but when I mount I only see the directories "Grub" and "Lost and Found" instead of my normal fedora-filesystem.

Any possibilty to combine this program with the link I posted I couple of posts before???

---

### Post by A$h X on 2007-12-20
Can't see the link you are referring to. I assume fedora uses a ext3 filesystem like ubuntu? I thought pysdm would work, maybe a equivalent program from fedora repo would work just as well? Never come across fedora so afraid I can't help with that too much.

---

### Post by Ampi on 2007-12-20
Sorry, I forgot the link...

[http://www.linux-sxs.org/storage/fedora2ubuntu.html]("http://www.linux-sxs.org/storage/fedora2ubuntu.html")

Well, I will look for that Fedora program, but I don't see that working as it should be working on my ubuntu or am I mistaken 'bout that?

---

### Post by A$h X on 2007-12-20
That link seems to be exactly what you are looking for. It was written for ubuntu, so there is no doubt it will run. Bear in mind this will allow you to to access your files on the fedora partition only once you have performed those commands, so it's not ideal if you want to access those files on a regular basis.

 In the link, the files which were required were copied over to the ubuntu partition once the fedora partition had been mounted.
You could copy the commands into a script and run it everytime you want to get at your fedora partition, but it seems a bit cumbersome.

How about making fedora read/write to ext3 and making a shared partition where you keep all your data files? That's what I do with windows XP and gutsy :)

---

### Post by Ampi on 2007-12-21
The link does work perfectly, but indeed, doing that after every boot...

I have never done anything with partitions so I don't know how to work with them.


The shared partition sounds good. 
That would mean I could access the docs on that partition from both OS's??

Because what I really want is using both OS's with their own programs and docs, but be able to access (and read/write and very imortant, start programs...) both OS's, whichever OS I start... 


If that what I want would complicate too much everything, I'll just get rid of my Fedora...

---

### Post by A$h X on 2007-12-21
Yeah, you could store your docs, mp3's, whatever files you wanted to keep on the shared partition, but as far programs go, you could install them onto the shared partition, but obviously fedora apps would not work on ubuntu and vice versa.
Apart from that, it's possible to do whatever you want. I recommend burning the gparted iso to a cd-r/rw, then making a new ext3 partition on your fedora HD. That way Ubuntu could see the files on the shared partition. There are many guides on gparted, have a look around.

---

### Post by Ampi on 2007-12-21
Okay, I'm gonna give it a try.... 
Thanks anyway!!! :)

---

