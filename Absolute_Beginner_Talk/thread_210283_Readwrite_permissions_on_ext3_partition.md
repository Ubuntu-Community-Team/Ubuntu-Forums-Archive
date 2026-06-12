---
title: "Read/write permissions on ext3 partition"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by Tallman on 2006-07-06
Hi all,

First of all I would like to mention that since I started using Ubuntu about a month ago, I am really impressed. I guess it will take me a few re-installs before I get everything to work the way I want to, but instead of being annoyed by that (which I used to be in my Windows-era), I am actually looking forward to it. Especially browsing through these forums makes me confident that I will succeed. You guys and girls kick *** with the way you help each other out here!

Now, for my newbie question...

I have made a partition where I need to store some data files temporarily (giving me the chance to remove Windows from my system). It keeps om giving me the message "You do not have permission to write to this folder".

I have been playing with the /etc/fstab, but I can get it to work. This is how my file looks now (the partition in question is the last one in the file):

# /etc/fstab: static file system information.
#
# <file system> <mount point>    <type>  <options>       <dump>  <pass>
proc            /proc            proc    defaults        0       0
/dev/hda5       /                ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb1       /media/hdb1      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb6       /media/hdb6      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb7       /media/hdb7      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb8       /media/hdb8      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       none             swap    sw              0       0
/dev/hdc        /media/cdrom0    udf,iso9660 user,noauto     0       0
/dev/hda1       /media/windows   ntfs    nls=utf8,umask=0222 0 0
/dev/hdb5       /media/music     ntfs    nls=utf8,umask=0222 0 0
/dev/hdb7       /media/video     ntfs    nls=utf8,umask=000 0 0  
/dev/hda7       /media/tijdelijk ext3    auto,rw 0       1

Please tell me what I am doing wrong here?

Thanks
Paul

---

### Post by Loffe_ on 2006-07-06
Try this row! It works for me...

/dev/hda7       /media/tijdelijk     ext3    defaults        0       2

:mrgreen:

---

### Post by aysiu on 2006-07-06
It doesn't matter how it's mounted if it's Ext3. It matters what permissions and ownership it has: ```
sudo chown -R tallman:tallman /media/tijdelijk
sudo chmod -R 755 /media/tijdelijk
```

---

### Post by Tallman on 2006-07-06
[QUOTE=aysiu]It doesn't matter how it's mounted if it's Ext3. It matters what permissions and ownership it has[/QUOTE]

Great, aysiu, that did it!

Thanks.
Paul

---

### Post by Bloch on 2006-07-06
Aysiu (or someone who knows stuff!)

I just installed an external hard drive using the ubuntu documentation at
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

I too could not write to my new disk, even though it appeared mounted.
It seems to me this documentation is faulty, or insufficient. There is no mention of changing permissions. It also should mention whether this advice applies equally to external (usb) and internal hard drives. It worked for me, but still this needs to be clarified.

I do not feel qualified to rewrite this documentation, but where can I point out these deficiencies?

---

### Post by aysiu on 2006-07-06
I don't know. I wrote my own documentation:
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by Bloch on 2006-07-06
Aysiu, you're the man!

I downloaded gparted. They should really get rid of the fdisk instructions (the CLI purists will howl)

I'll look into where to make suggestions about documentation. Seeing as it's community developed, couldn't you propose your page, or at least the gparted sections? (and that crucial bit on permissions)

And that documentation I linked to above has another fault. It tells you that you need to edit fstab, then drops you over the edge with a link to an advanced comprehensive page on fstab. It's like being led by the hand to a cliff.

---

### Post by Tallman on 2006-07-06
One more thing...

I am now able to (for example) drag files from my desktop to this partition. But when I open the partition I am unable to create a new folder. When I browse to /media/tijdelijk in the terminal I can create a new directory there (mkdir, without involing sudo).

Why is that?

Thanks
Paul

---

### Post by aysiu on 2006-07-06
That's weird. I'm not sure what the issue is...

---

### Post by Tallman on 2006-07-06
The thing is, when I open my "tijdelijk" partition by double-clicking on the icon on my dekstop, it opens in a new File Browser window. In this Window, the option File -> Create Folder (and File -> Create Document for that matter) is greyed out.

Opening the terminal and switching to /media/tijdelijk makes it possible to invoke an mkdir command (even without sudo). It creates the directory succesfully.

It's not a trainsmash, I am just getting curious...

Thanks
Paul

---

### Post by aysiu on 2006-07-06
What happens if--instead of double-clicking the desktop icon--you just go to the file browser and type ```
/media/tijdelijk
``` in the address bar.

Does the resulting window let you create folders...?

---

### Post by Tallman on 2006-07-06
[QUOTE=aysiu]Does the resulting window let you create folders...?[/QUOTE]

Nope, both options are still greyed out in /media/tijdelijk.

FYI, in my home folder the options are available.

---

### Post by aysiu on 2006-07-06
I have no idea what it could be. If you can make the directory in the terminal, you should be able to do it in the file browser as well.

---

### Post by Tallman on 2006-07-06
[QUOTE=aysiu]I have no idea what it could be. If you can make the directory in the terminal, you should be able to do it in the file browser as well.[/QUOTE]

Okay, just rebooted the computer and now it works in the file browser as well.

Thanks, aysiu =D>
Paul

---

### Post by 43moon on 2006-07-09
This has been kicking my butt.  Aysiu, thanks for providing the solution to this and many other issues that I have resolved as a result of your advice to others.  You are a great resource and part of what makes the Ubuntu community great.

---

### Post by bluepowder7 on 2007-11-01
> **aysiu said:**
> I don't know. I wrote my own documentation:
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

dude, you ROCK!  haha!  i was looking on how to set up read / write permissions to a separate non-home partition, and your writeup was DEAD EASY to follow.  glad this thread came up in a search.

:guitar:

thanks!!!!

---

