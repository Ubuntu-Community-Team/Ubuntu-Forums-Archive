---
title: "/home partition a folder?!"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by DSAKA on 2007-06-01
OK, so we're new at the whole Linux thing, but are familiar with partitioning in Windows. Well, we completely got rid of Windows and are only working with Ubuntu 7.04 now. Whilst doing the partitioning we set up the following partitions:

"/" for Ubuntu
"/swap" for the swap :)
"/home" for stuff we want to keep separate so we don't have to burn a bunch of dvd's of our pictures and downloaded programs etc. upon reinstalling or upgrading Ubuntu in the future
and I think one other random partition (we're at school right now so we can't check!)

So now when we go to look at the partitions the home partition shows up as a folder and not a partition. What did we do wrong?! 

On a side note: the Ubuntu installer didn't want to let us name a partition whatever we wanted to and we only had a list of weird names to choose from...(including /, /home, /osf, etc.) probably normal, but do all the suggested names have a specific purpose? For example, it'd be nice to name one /programs, where we would download all of our ubuntu compatible programs to, so we don't have to redownload them after a reinstall.

(I hope I'm not repeating a question that has been answered a thousand times, but I did a few searches and couldn't really find anything specific!)

Thanks!!!!

---

### Post by eentonig on 2007-06-01
Linux just handles 'everything' as a file or folder.

You did nothing wrong.

---

### Post by Wim Sturkenboom on 2007-06-01
1)
There is no /swap :) ; it's just swap

2)
Nothing wrong; there's a mountpoint where the home partition is mounted. A mountpoint is a directory in the file system.
I don't have an Ubuntu box at hand, but you can view the file /etc/fstab. On my Slackware box it says that /dev/hda5 is mounted on the directory /home

---

### Post by Sparkster185 on 2007-06-01
> 
For example, it'd be nice to name one /programs, where we would download all of our ubuntu compatible programs to, so we don't have to redownload them after a reinstall.


It's not quite that easy.  Linux installed programs all over the place, in a sense.  Although the actual executable is usually in /usr/bin, the entire "program" is spread out over a bunch of files.  Linux makes it so shared libraries are only on disk once.

Although you could install every program to a /programs directory, it would be pretty rough to manage all the library dependencies manually.  Or if you kept all the necessary libraries inside the applications specific folder in /programs, you would have duplicate libraries all over the place, being terribly inefficient.

---

### Post by starcraft.man on 2007-06-01
> **Wim Sturkenboom said:**
> 2)
Nothing wrong; there's a mountpoint where the home partition is mounted. A mountpoint is a directory in the file system.
I don't have an Ubuntu box at hand, but you can view the file /etc/fstab. On my Slackware box it says that /dev/hda5 is mounted on the directory /home

Alternatively, if you want a nice GUI way of looking (and editing to some degree) the partitions (mount point, space free/used, flags, etc...), just install gparted into Ubuntu. Terminal command  (applications > Accessories > terminal):

```
sudo aptitude install gparted
```

It then appears in System > Administration > gparted. 

Other than that, like everyone said you didn't do anything wrong. Strictly speaking I'd call em directories, a bit more important than casual user created folders (I'm just picky on my words) :).

Oh and, I wouldn't worry about the programs thing...

---

### Post by eentonig on 2007-06-01
> **DSAKA said:**
> ...
On a side note: the Ubuntu installer didn't want to let us name a partition whatever we wanted to and we only had a list of weird names to choose from...(including /, /home, /osf, etc.) probably normal, but do all the suggested names have a specific purpose? For example, it'd be nice to name one /programs, where we would download all of our ubuntu compatible programs to, so we don't have to redownload them after a reinstall.
...

The names in the partitioner are premade for standard linux (distro dependant in some cases) file system hierarchy.

In linux, every type of file is supposed to be placed under a specific location.
System configuration usually goes under /etc
system programs go under /bin
system wide data like icons, dos, etc go under /usr
Personal files -- > /home/<username>
external media (usb disk, CDROM)--> /media
devices (the physical interface to the OS) --> /dev
etc, etc, 


This allows for devellopers to 'know' where they can find required libraries and such, so they don't need to include them over and over again in the programs they make. Thus, programs tend to be smaller in linux.

---

### Post by DSAKA on 2007-06-01
Cool! And thanks for the quick responses...it's good to know that we didn't do anything wrong. As a bonus you guys answered another unasked question of ours...namely where file system came from/what file system is! I still think we'll do a reinstall and just go with the partitions "/", and "/home" and the swap and save everything we don't want to have to redownload in home...sound reasonable?

---

### Post by Patrick K on 2007-06-01
You can create mount points with names of your choosing. You should create the directories in /media then edit fstab to point to the mount points you want to use. For example /media/my_files. Then edit fstab to mount the partition you want to that mount point. It's not hard but if you screwup your partitions may not be accessible. I wouldn't do this with any system partitions, though, just user partitions.

---

### Post by phr0ze on 2007-06-01
Windows chooses drive letters to identify partitions, linux uses 'folders'. However even in windows you can use folders too. C:\Foo can be a completely different drive than C:\. 

I'm just mentioning this because windows has us convinced drive letters are the only way of working when it too supports the alternative.

---

### Post by Chayak on 2007-06-01
As mentioned any partitions you create you'll never really notice as to the user everything looks like the regular folders until you dig into disk data and such.  It's always a good idea to keep a seperate partition for /home anyway as you said if you upgrade the rest of the os all your saved data isn't touched and you can simply point the new installation to your /home and you're set.  As for programs I'm reading that you want to keep the installers (packages, etc)  stored so you can install stuff later without having to download it again.  In that case you can make your /programs folder in your home directory.  I wouldn't really suggest it as I always like to get the most up to date software, but there's nothing stopping you from doing it.

---

### Post by vortmax on 2007-06-01
You can install the programs to their own folder.  I do this whenever I have to build something from source. 

Once you unpack/compile the program to a directory, you just need to go into that directory and link the /bin /lib and /include folders to /usr/bin /usr/lib /usr/include respectively.  A link is like a shortcut.  So when you run the program, linux looks in the /usr/bin folder, sees the link and runs the program from wherever you installed it.

It's actually a really good habit to get into for programs that you will upgrade or run different versions, as you can have several versions installed at once, and just change the links to point to whatever version you want to run.  Same goes for libraries.

To make things really clean, you could create /programs/bin, /programs/lib and /programs/include folders, to house all the links from the stuff you install yourself.  Then either link those folders to /usr/local or edit your environment variables to point there. 


to link a file  you use this command:

ln -s /the/source/file  /the/target/link

so to make a link from /programs/myprog/bin/myprog  to /usr/bin  you would use:

ln -s /programs/myprog/bin/myprog  /usr/bin/

or to link all the files in /programs/bin to /usr/local/bin  type:

ln -s /programs/bin/* /usr/local/bin/

just replace bin with lib or include for the others

To change your path, which tells linux where to look for stuff, type: 

export PATH=$PATH:/new/bin/location
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/new/lib/location

substituting /new/bin/location or /new/lib/location for wherever you put them (/programs/bin maybe?)

the : is important.  To add that path perminantly, just add that line to the end of your /home/.cshrc or /home/.bashrc depending on what shell you use.  That will make those programs accessible to just one user.  To make them accessible to all users, add the same line to /etc/profile and /root/.bashrc (cshrc)

You will still have to use a link for the include folder though
now i said all of that, if you use a package manager like apt-get or aptitude, I would just let it worry about all the installing.  That will keep things updated and prevent you from entering 'dependency hell', but installing a program or two like this will really teach you about the linux file system and how linux 'thinks'.

---

### Post by ncappel1 on 2007-06-02
> **Sparkster185 said:**
> Although you could install every program to a /programs directory, it would be pretty rough to manage all the library dependencies manually.  Or if you kept all the necessary libraries inside the applications specific folder in /programs, you would have duplicate libraries all over the place, being terribly inefficient.

isn't this what /opt can be used for?

---

