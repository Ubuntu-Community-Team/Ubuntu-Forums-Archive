---
title: "How can I access my mounted hard drive?"
date: 2010-02-15
forum: Apple Hardware Users
---

### Post by Death.Cab on 2010-02-15
Hey everyone.

I have a Macbook 4,1 and I've installed Ubuntu and Mac OSX. However, I'm having some difficulties accessing my Macintosh HD while on Ubuntu.

I've been searching and can't find a solution. I think I should try to copy those files to ubuntu but I don't know which path to follow (eg: Macintosh HD/Users/etc...).

Where can I find that path and how can I copy them without those permissions blocking me?

---

### Post by linuxopjemac on 2010-02-15
copying is probably the best solution.

```
sudo fdisk /dev/sda
```

if /dev/sda is your HD, it could also be /dev/hda
then you issue a "p" to print the partition table, then you know where OSX resides.

then

```
sudo mkdir /mnt/osx
sudo mount -t hfsplus /dev/sdaX (where sdaX is the OSX partition)
then you copy all that stuff as root to some folder
then you chown it to your own user name
chown -R name.name folder 
```

done

---

### Post by Death.Cab on 2010-02-15
Ok, got the first commands right. But what should I do at the chown -R name.name folder?

Thanks in advance.

---

### Post by linuxopjemac on 2010-02-15
what's your username in the Linux environment ?

what is the folder name where you put all these files ?

---

### Post by Death.Cab on 2010-02-15
My username is deathcab. And I haven't put them anywhere, lol :D

I just ran those commands :s

---

### Post by linuxopjemac on 2010-02-15
you don't understand me, the user name in Ubuntu

it looks like name@ubuntu or something, name is the user name...if you know what I mean (I am not talking about your name in this forum)... The folder name is the folder you put the copied files from OSX in.

---

### Post by Death.Cab on 2010-02-15
Yeah, but I also use deathcab in Ubuntu :D deathcab@deathcablinux

---

### Post by linuxopjemac on 2010-02-15
ok :)

then issue to the folder where you have those files in, I call it /home/users/deathcab/osx_files for simplicity:

sudo chown -R deathcab.deathcab /home/users/deathcab/osx_files

then all the files are accessible as deathcab

---

### Post by Death.Cab on 2010-02-15
Hum, ok :D

So, this is still kinda new to me. What will the 'sudo mount -t hfsplus /dev/sda2' do?

Will it mount the Macintosh HD at /dev/sda2?

---

### Post by linuxopjemac on 2010-02-15
```
sudo mount -t hfsplus /dev/sda2
```

will mount the second partition on drive sda, which is in hfsplus format. You still need to give a place where to mount, for example /mnt/osx, so it becomes

```
sudo mount -t hfsplus /dev/sda2 /mnt/osx
```

---

### Post by Death.Cab on 2010-02-15
Ok I did it but it is still empty (the /mnt/osx)...

:s

---

### Post by linuxopjemac on 2010-02-15
are you sure that /dev/sda2 is your osx partition ?

---

### Post by Death.Cab on 2010-02-15
I tried with both sda2 and sda3.

---

### Post by linuxopjemac on 2010-02-15
can you copy paste the output of "p" in 

sudo fdisk /dev/sda

please ?

---

### Post by Death.Cab on 2010-02-15
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       54463   437266684   af  HFS / HFS+
/dev/sda3           54480       60785    50652916   ef  EFI (FAT-12/16/32)


There you go :P

---

### Post by warp99 on 2010-02-15
> **Death.Cab said:**
> Hey everyone.

I have a Macbook 4,1 and I've installed Ubuntu and Mac OSX. However, I'm having some difficulties accessing my Macintosh HD while on Ubuntu.

I've been searching and can't find a solution. I think I should try to copy those files to ubuntu but I don't know which path to follow (eg: Macintosh HD/Users/etc...).

Where can I find that path and how can I copy them without those permissions blocking me?

What's the file system the MAC is using? If it's HFS+ you should be able to mount those files read-only with ease unless you have encryption turned on. If you want to share the files between the MAC and Ubuntu you could set up a separate partition like this person did:

[http://www.ubuntuproductivity.com/journal/macintosh/08/2009/readwrite-to-hfs-on-ubuntu/](http://www.ubuntuproductivity.com/journal/macintosh/08/2009/readwrite-to-hfs-on-ubuntu/)

I would also change the user/group ID number in Ubuntu or OS X so they both match as suggested by one of the comments. You can also install the hfsprogs package in Synaptic so you can repair (fsck) the drive from Ubuntu if needed.

---

### Post by Death.Cab on 2010-02-15
Well, I'm not really up to creating another partition, only if I screw up anything and I need to restore my hard drive.

So...what should I do then?  It doesn't look like it will work...

---

### Post by warp99 on 2010-02-15
You need to mount the drive "read-only" since it will not mount with write permissions unless you install the hsfprogs package. So with your command add the option so it looks like this:

```
sudo mount -t hfsplus /dev/sda2 **-o ro** /mnt/osx
```

That's the letter o and not a zero.

Edit: I assume you already created the directory "/mnt/osx"?

---

### Post by warp99 on 2010-02-15
According to this article if you install the hfsprogs you need to use the force option:

[http://raamdev.com/mounting-hfs-with-write-access-in-debian](http://raamdev.com/mounting-hfs-with-write-access-in-debian)

You could install the hfsprogs in Synaptic then try to force mount the drive like this if all else fails:

```
sudo mount -t hfsplus /dev/sda2 -o force /mnt/osx
```

---

### Post by Death.Cab on 2010-02-15
Ok mounted it. Now I need to copy it right?

EDIT: Tried 'sudo cp /mnt/osx/Users/alexandrepinto/Music ~/Desktop'. Not working.

---

### Post by warp99 on 2010-02-15
Easy. Just open the file manager in Ubuntu, aka Nautilus, then drag and drop. Not everything in Linux needs a command line your know, unless you feel more comfortable using it. ;)

---

### Post by Death.Cab on 2010-02-15
Well I like the command-line, but drag-n-drop feels easier :P

I summoned Nautilus and went to the folder I wanted to copy. But it seems like I don't have enough permissions :s

---

### Post by warp99 on 2010-02-15
> **Death.Cab said:**
> Ok mounted it. Now I need to copy it right?

EDIT: Tried 'sudo cp /mnt/osx/Users/alexandrepinto/Music ~/Desktop'. Not working.

Use the -r paramter and drop the sudo since you don't want to copy the files into your home directory with root permissions. You command should look like this:

```
cp -r /mnt/osx/Users/alexandrepinto/Music ~/Desktop
```

Or better yet just use Nautilus then drag and drop or copy and paste, your choice. :D

---

### Post by warp99 on 2010-02-15
> **Death.Cab said:**
> Well I like the command-line, but drag-n-drop feels easier :P

I summoned Nautilus and went to the folder I wanted to copy. But it seems like I don't have enough permissions :s

You have permissions to copy the files, but not to move them to your home directory. Highlight the files, then choose copy and paste them to your /home/$user directory, deathcab something, right?

---

### Post by warp99 on 2010-02-15
You may not have enough permissions to access just your user directory on OS X. I suggest you use the "cp -r" command with sudo or open a root Nautilus session by typing "gksudo nautilus" at the command line or press "alt-F2" then type "gksudo nautilus" into the run dialog.

---

### Post by Death.Cab on 2010-02-15
> **warp99 said:**
> Use the -r paramter and drop the sudo since you don't want to copy the files into your home directory with root permissions. You command should look like this:

```
cp -r /mnt/osx/Users/alexandrepinto/Music ~/Desktop
```Or better yet just use Nautilus then drag and drop or copy and paste, your choice. :D

I think this worked. Yeah. It did :P But I had to put sudo though.

What does the -r stand for?

---

### Post by warp99 on 2010-02-15
On any command just add the --help switch:

```
cp --help
...
-R, -r, --recursive          copy directories recursively
```

It copies the files and directories, not just the files. I believe the command is the same in OS X.

---

### Post by Death.Cab on 2010-02-15
Well, thanks everyone for your helpful advice :D

---

