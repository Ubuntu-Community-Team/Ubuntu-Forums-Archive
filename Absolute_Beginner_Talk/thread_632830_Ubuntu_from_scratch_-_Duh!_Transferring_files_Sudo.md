---
title: "Ubuntu from scratch - Duh! Transferring files? Sudo? Huh?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by TRH on 2007-12-05
I hardly know where to begin. I know nothing about Linux or Ubuntu. I have been installing Windows Operating systems on PCs for the last 3 years and we only used Ubuntu occasionally to check some things, but no one knew much about it. I don't work at that place anymore and am at home trying to save important files on a 100 gig hard drive that Windows no longer sees. Ubuntu sees all the files. So I could save them to my 500 gig hard drive. But I keep getting the error message saying I do not have permission because I am not the owner. Argh. I googled the problem and found threads here on this forum saying something about password and sudo, etc. But the ubuntu I am using is directly from a CD and no password was required. Anyway I am starting from scratch. I have the two drives up in two boxes. If this was windows I would simply drag the files and folders from one box to the other. But that doesn't work with Ubuntu. So what do I have to do? How do I get permission. Sorry I must sound like a numbskull but the so-called simple instructions on how to do it that I found when I googled helped me not at all. Would anyone care to walk me through this one step at a time? Argh....

TRH

---

### Post by Hospadar on 2007-12-05
Welcome!

Sudo gives any command appended after it root priviledges, so if you want the ease of drag-and-drop transfer, you should open up a terminal and type ```
sudo nautilus&
sudo nautilus
```this will open up two file browsers as root so you can point them where you want and drag and drop whatever.  if you are running off the livecd, you shouldn't be asked for a password.

If you still get problems, it's possible that
a) you don't have write-capable drivers for ntfs installed (although I think they come standard on the 7.10 cd, but maybe not, also you are just reading, so that seems dubious)
b) the drive is corrupt and for whatever reason can't be read properly (this seems unlikely)

If this doesn't work, post any errors and we can go from there.

also, if you particularly want to use the command line to copy, I could tell you how to do that, but I don't think drives mount in the livecd until you click them in a file browser, so you'd have to do that first, or mount the manually (if it sounds like a lot harder than just dragging stuff, that's because it is)

---

### Post by bodhi.zazen on 2007-12-05
LOL

Fire up the live CD

Open a terminal.

Enter :```
gksu nautilus
```

Twice ...

Now you can drag and drop ...

==========================

For a detailed explanation :

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)
[indent]Vista: Install the fs-driver using the "Windows XP compatibility mode"[/indent]

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by UltraMathMan on 2007-12-05
EDIT: Geez. I'm slow. Can you tell I like the command line? Can't believe I forgot gksu nautilus!   :)


First things first, make sure you are running the latest Live CD (7.10). You can check this by going to System -> About Ubuntu. The reasoning behind this is that the latest release supports native NTFS writing (whereas in prior versions one had to set that up manually).

Next navigate to the folder you want to copy. In a new File Browser window (Ctrl+n) navigate to the drive you want to copy to.

Open a terminal (Applications -> Accessories -> Terminal

**Read the entire post before entering commands, do not press Enter until you have the local and destination paths in.**

Type ```
sudo cp -Rv 
``` then go to the window with the folders files you want to copy and highlight the path (Next to Location: ). Click and drag the highlighted path into the terminal window, so that it looks like ```
sudo cp -Rv /path_to_folder/
```

Now go to the window where you want the files copied to and highlight that path and drag it into the terminal so that you have something like ```
sudo cp -Rv /path_to_folder/ /path_to_destination/
```

Make sure your spaces are correct and make sure any path with spaces is contained in single quotes '  '.

Press Enter, being a LiveCD it shouldn't prompt you for a password. 

By the way, sudo cp -Rv breaks down as sudo = run as root, cp  = copy, -Rv = Recursive (ie. copy folders) and verbose (ie. show what it is doing) options.

-Hope this helps :)

---

