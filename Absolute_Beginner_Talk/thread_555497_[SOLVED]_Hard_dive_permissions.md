---
title: "[SOLVED] Hard dive permissions"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by offroad64 on 2007-09-20
First off I'm a real noob with linux. I have 3 sata drives in my machine.
1 dive for the OS and the other 2 for storage. I don't have permission to write to the storage drives. I fomatted using sudo gparted and all was good for a while. The problem started when I wanted them to auto mount. I used the drive management tool for the auto mount.At this point I lost permissin the write to the drives. Since I have reformatted them and still no luck. Any ideas

---

### Post by Jeroen Vernooij on 2007-09-20
Hi,
Try to type
```
sudo chown <YOUR-USERNAME> <MOUNT-POINT-OF-HARDDRIVE>
```

example
```
sudo chown jeroen /media/sda1
```

---

### Post by Bothered on 2007-09-20
Which tool did you use to configure the automount?

Also, do you know where the drives are mounting to?

---

### Post by offroad64 on 2007-09-20
Thank you Jeroen
It worked like a charm.
Now all I have to do is unlearn Windos

Jeff Masygan

---

### Post by davlaw2000 on 2007-09-20
I too experienced exactly the same problem. It's a shame that you have to resort to arcane commands in a terminal window to overcome such a basic problem. 
I know you will all say "you don't understand it's done for security reasons" or something similar but something as basic as this shouldn't be so hard. 
Us noobs install the OS, scratch around for ages trying to work out how to do something really simple (like how to find the second hard drive, and how to copy stuff to it), and finally give up thinking "jeez I'm such an idiot I can't even work out how to create a folder on my own hard drive".  
In desperation we post a question on a forum, thinking "I am going to look such a fool when someone posts the solution".
Then we see the answer! Of course! We should have known from the start. Just open a terminal window and type  sudo chown <YOUR-USERNAME> <MOUNT-POINT-OF-HARDDRIVE>. What a fool I was not to have known that. 
My point is this - the OS has to be more user-friendly. I appreciate the need for security, ownership and permission, but we need the OS to guide us to the solution, even if it says "now I need the magic password before I can let you do this". Such fundamental things should not be hidden away like this.  If there is a good GUI-based tool to do such things it needs to be part of the distribution. 
Rant over. Sorry.

---

### Post by Bothered on 2007-09-20
> **davlaw2000 said:**
> I too experienced exactly the same problem. It's a shame that you have to resort to arcane commands in a terminal window to overcome such a basic problem.

This problem can also be solved within nautilus (in Gnome), if run with root privaledges:

1. Press Alt-F2
2. Type: gksudo nautilus and enter password for root privaledges
3. Navigate to mount point, right click and select "properties"
4. Select the permissions tab, and change the owner (and I recommend the group) to your usename.

EDIT: Often I find it's just more concise when responding on the forum to give a single terminal command than many GUI instructions.

---

### Post by davlaw2000 on 2007-09-20
Thanks for the response, but I fear you missed my point. The GUI should provide such basic facilities as standard. Sure all the necessary permission, security and password protection should be there, but even your solution requires commands to be typed in a terminal window. 
I think Ubuntu is fantastic, and you get an amazing amount of software bundled with it to do all kinds of stuff, but I have a natural dread of command windows and feel that GUIs were invented to render them unnecessary. 
I still feel that something as fundamental as this should be covered in some way by the GUI without the need to type commands in a window.
I am a programmer, but mainframe only. I just wish I had the programming skills to knock up a user-friendly utility with a nice simple GUI to handle this. We get something called the 'Removable Drives and Media' application but nothing to manage internal hard drives. Why not?
Second rant over. Sorry again. 
Don't get me wrong - I love the OS but it just needs to be that bit friendlier in some areas.....

---

### Post by Bothered on 2007-09-20
> **davlaw2000 said:**
> your solution requires commands to be typed in a terminal window.

It's a "run command" window, but that's splitting hairs I admit.

> **davlaw2000 said:**
> We get something called the 'Removable Drives and Media' application but nothing to manage internal hard drives.

I agree, this is annoying. However, as you can see from the screen shots in [this thread]("http://ubuntuforums.org/showthread.php?t=555707") a similar tool does exist. I don't actually know what that tool is - it's possible it's a screenshot of Gutsy.

---

### Post by davlaw2000 on 2007-09-20
Disk Manager looks interesting. Still falls foul of the old permissions/security thing and doesn't do anything user friendly like prompt for a password. I see the solution is yet another bizarre command in yet another terminal window. 
Is it just me? I would rather not have to sit and learn this stuff when all I want to do is copy some pictures or music onto my second hard drive. 
Why is it so hard?
I used GpartEd to delete everything off the drive and create and format a new partition from scratch. Now for some reason it won't mount, I can't see it when I explore the computer with the file browser, so I am totally stuck. 
It's so frustrating when everything else looks so good. :(

---

### Post by Bothered on 2007-09-20
Ah, that problem is easier to resolve with the help of the command line ...

Could you type the following in a terminal and post the results:

```
sudo fdisk -l
```

---

### Post by davlaw2000 on 2007-09-20
Here is the output from fdisk....
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2             393        4981    36861142+   f  W95 Ext'd (LBA)
/dev/hdb5             393        4981    36861111   83  Linux

Just don't ask me what it all means.....:)

Surely you guys get sick of the same old questions all the time??

---

### Post by Bothered on 2007-09-20
> **davlaw2000 said:**
> Just don't ask me what it all means.....:)

It's a list of the partition tables on your system.

> **davlaw2000 said:**
> Surely you guys get sick of the same old questions all the time??

There's enough people answering questions that you don't need to answer the same questions again and again.

Could you now enter the following in a terminal and post the result:

```
cat /etc/fstab
```

EDIT: And also enter the following in a terminal and post the result:

```
ls -l /dev/disk/by-uuid
```

---

### Post by davlaw2000 on 2007-09-20
Ok here goes....
Command 1....
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e3736227-fa3b-451e-8565-7586e9c5b529 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=332f05d1-474f-4c2e-9836-0ce492dd1bab none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
Command 2.....
total 0
lrwxrwxrwx 1 root root 10 2007-09-20 21:12 332f05d1-474f-4c2e-9836-0ce492dd1bab -> ../../hda5
lrwxrwxrwx 1 root root 10 2007-09-20 21:12 e3736227-fa3b-451e-8565-7586e9c5b529 -> ../../hda1

BTW thanks for your patience!

---

### Post by Bothered on 2007-09-20
I am a bit confused. The partition on your second hard drive doesn't appear to have a uuid.

Ok, to fix the problem try (largely terminal based I'm afraid):

1. In a terminal backup your fstab with "sudo cp /etc/fstab /etc/fstab.bak"
2. Type "sudo mkdir -pv /media/hdb5" - this is where your drive will appear
2. Type "gksudo gedit /etc/fstab"
3. Add a line at the bottom of the file containing the following:

```
/dev/hdb5 /media/hdb5 ext3 defaults 0 1
```

4. Save and close gedit.
5. Type "sudo mount -a". The drive should now appear in /media/hdb5.

If there is a problem, try:

1. Type "gksudo gedit /etc/fstab"
2. Change the line for /dev/hdb5 to:

```
/dev/hdb5 /media/hdb5 auto defaults 0 1
```

Important note: If the drive is not permanently connected change the two numbers in the above code sections to "0 0" - otherwise your computer may fail to boot when you remove the drive!

---

### Post by davlaw2000 on 2007-09-20
OK did all that. I added a line to fstab as there wasn't one there already for hdb5. 
It seems to have done the trick. On reboot I have an icon on my desktop labelled hdb5 and when I click on it, I see the drive contents (currently empty). 
Can't create any folders though. Must be a permissions thing I guess. I will have a go at solving that myself as I have seen solutions posted. 
Thank you for all your help. 
I still stand by my original comments - there needs to be a more user-friendly way to do something as basic as accessing and copying stuff to a second hard drive.

---

### Post by Bothered on 2007-09-20
I agree that sorting out problems with fstab is a bit tricky. A GUI would certainly be helpful.

---

