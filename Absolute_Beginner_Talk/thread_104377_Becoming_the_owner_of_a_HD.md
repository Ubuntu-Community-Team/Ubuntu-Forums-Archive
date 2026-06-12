---
title: "Becoming the owner of a HD"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Jinto.Lin on 2005-12-16
I've installed a 2nd HD, drv/hdb1. I can't write files to it. How do I become the owner of it?


edit: dev/hdb1

---

### Post by mherring on 2005-12-16
/dev/hdb ??  hdb1 means partition 1 on drive 2

You don't own drives, you own their mount point.  

Is the new drive formatted and mounted?  If so, then look at the permissions for the mount point.
To what is mounted where:  "more /etc/mtab"-

---

### Post by joshuapurcell on 2005-12-16
This command will show you what hard drives the OS knows about and what partitions they have:> sudo fdisk -l
If you see the hard drive that you have just installed, then you probably also see that there aren't any partitions on that drive. Use fdisk again to create the needed partitions:> fdisk /dev/hdb
You may want to read the [man file](http://www.die.net/doc/linux/man/man8/fdisk.8.html) for fdisk or [google](http://www.google.com/search?hs=NWS&hl=en&lr=&client=firefox&rls=org.mozilla%3Aen-US%3Aunofficial&q=fdisk+howto&btnG=Search) how to use the command.

---

### Post by aysiu on 2005-12-16
Is this a Windows hard drive? You may want to check out the fourth link in my sig for that.

---

### Post by Jinto.Lin on 2005-12-16
It is not windows. Also, it named it that when I used gparted to make the partition on the 2nd drive, so I could use it (the New drive)... but while I'm at it, what is the better partition type?


Also... the whole reason I needed the 2nd HD was for more space... I can't boot now because there is so little space! I'm downloading the live CD to delete a few files, but is there a way to do that without logging in?

---

### Post by aysiu on 2005-12-16
Is it Ext3?

If so, I'd do this: ```
sudo cp /etc/fstab /etc/fstab_backup
sudo mkdir /more_room
sudo nano /etc/fstab
``` And then add in this line: ```
/dev/hdb1  /more_room   defaults   0    0
``` Save (Control-X), confirm (y), and exit (Enter). Then ```
sudo mount -a
sudo chown -R jintolin:jintolin /more_room
``` This assumes, of course, that your username is jintolin on your Ubuntu machine.

If it's not Ext3, change the line in the /etc/fstab to ext2 or reiserfs or whatever's appropriate.

---

### Post by Jinto.Lin on 2005-12-16
I've done all but the last bit
(sudo mount -a
sudo chown -R jintolin:jintolin /more_room)
because when I type 'sudo mount -a' it says it is an unknown files system (The default is Ext3, right?)

---

### Post by aysiu on 2005-12-16
It's not the default--it's what I put in the /etc/fstab. I was guessing.
Unfortunately, the partition table doesn't really tell you much. If you type in ```
sudo fdisk -l
``` to list the partitions, it'll probably tell you that /dev/hdb1 is of type "Linux," which doesn't really tell you whether it's Ext3/Ext2/Reiserfs...

How did you format it...? Or did you format it? Did you just set aside a space for the hard drive or did you actually format it? If you formatted it, you should have chosen a filesystem type.

---

### Post by Jinto.Lin on 2005-12-16
that was so long ago! Really, not to long ago, but about a month ago I started to work at GeekSquad. That plus holidays means no working memory! 

I've written the Live CD, is there a way to do it from the CD?


Edit: (rw,errors=remount-ro) for /dev/hda1 on / tyep ext3

---

### Post by aysiu on 2005-12-16
Sure. ```
sudo apt-get install gparted
gparted
``` Then, it'll scan your partition table and let you know what file type it is. As you can see from the attached screenshot, my Linux partitions are Ext3. Yours are probably something else.

---

### Post by Jinto.Lin on 2005-12-16
while it boots up, I'm going to create a HD from the memory?


edit: and I can't run it :D It says I must be root, how do I login as root?

---

### Post by aysiu on 2005-12-16
[QUOTE=Jinto.Lin]while it boots up, I'm going to create a HD from the memory?[/quote] What? How do you create a hard drive?

> 
edit: and I can't run it :D It says I must be root, how do I login as root? You don't log in as root. Just press alt-F2 and type ```
gksudo gparted
```

---

### Post by Jinto.Lin on 2005-12-16
ok, it is ext3. I might have typed the info in wrong. I'll try again now.


Oh, when I say create a HD, I mean in how you use a virtual memory, but backwards (Memory not on HD, but HD on memory)

---

### Post by aysiu on 2005-12-16
Sorry! You didn't type the info wrong. I typed the instructions wrong.

The /etc/fstab line should read ```
/dev/hdb1 /more_room  **ext3**  defaults 0 0
``` I didn't even put Ext3 in before!

After you modify the line, then do the ```
sudo mount -a
sudo chown -R jintolin:jintolin /more_room
```

---

### Post by Jinto.Lin on 2005-12-16
ok, so now what do I do? After I typed in the last command, it does nothing. I tried to restart but still the same issue.... I can delete files if I boot from the CD? Or will it not let me?


edit: I'll try tomorow. Night!

---

### Post by aysiu on 2005-12-16
[QUOTE=Jinto.Lin]ok, so now what do I do? After I typed in the last command, it does nothing.[/quote] What do you mean "it does nothing"? Go to /more_room and try to create a file there. Can you? If not, what message do you get? 

> I tried to restart but still the same issue.... I can delete files if I boot from the CD? Or will it not let me? Yes, you can delete files from the CD. You have to mount the partition first.

I don't really understand what's at issue here.

---

### Post by Jinto.Lin on 2005-12-16
I can't boot into Ubuntu because the first HD is full. So full it can't create files!

edit: the files to login.

---

