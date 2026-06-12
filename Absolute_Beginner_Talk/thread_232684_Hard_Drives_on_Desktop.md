---
title: "Hard Drives on Desktop"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by TheEmb3rEgg on 2006-08-09
I just dual booted Ubuntu and Windows on my PC after having another PC with Ubuntu already(I love it!). After I finished the install, All of my partitions were on my desktop (This is not the case on my other Ubuntu box). To get rid of them from my desktop, it requires me to unmount them. I am afraid them to this because I don't really understand what this does. Should I unmount them? If not, what can I do to rid them from my desktop?

---

### Post by orb9220 on 2006-08-09
You don't have to unmount them.
Instead you can remount them in a new folder that won't be displayed on the desktop all you have to do is modify fstab and create a new folder.

Here is minde:

/dev/hda1       /home/orb/Drives/hda1/     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/hdd1       /home/orb/Drives/hdd1/     vfat    defaults,utf8,umask=007,gid=46 0       0

I created a folder in home/orb called Drives and in that folder I created two more folders called hda1 and hdd1 and they get mounted there. I can still access them and they are not on the desktop.

Anything you want to show up on desktop will be from the /media/ folder. that is how ubuntu is set up.

Hope this helps.

---

### Post by TheEmb3rEgg on 2006-08-09
So, I unmount them from my desktop, then mount them into the folder? 

What does mounting them actually do?

---

### Post by davebgimp on 2006-08-09
I believe you can get into your Gnome config editor and select not to show them on the desktop graphically. I'm on Kubuntu, so maybe someone else can be a bit more specific, but i remember it was a simple step.

---

### Post by aysiu on 2006-08-09
If the hard drives are mounted within the /media folder, they will appear on the desktop unless you Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop > Volume_Visible and then uncheck the box.

If you want them never to appear, regardless of what box is checked, mount them somewhere else.

For example: 
mounted to /media/windows will show up on the desktop
mounted to /windows will not show up on the desktop
mounted to /media/hda1 will show up on the desktop
mounted to /hda1 will not show up on the desktop

Where it's mounted to is defined in the /etc/fstab file. Let's say you have your drive mounted to /media/hda1 and want it mounted to /hda1 instead. This is what you'd do: ```
sudo umount /media/hda1
sudo mkdir /hda1
sudo nano -B /etc/fstab
``` Then find the line that looks like this (or similar): ```
/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222 0 0
``` and change it to this: ```
/dev/hda1 /hda1 ntfs nls=utf8,umask=0222 0 0
``` Save (control-x, y, enter) and then ```
sudo mount -a
```

---

### Post by TheEmb3rEgg on 2006-08-09
That works great asyiu. 
Thanks for all of the help guys!

---

### Post by rune on 2006-10-16
The "mount outside of /media" doesn't work on Edgy. No matter what I try, they show up.

---

### Post by aysiu on 2006-10-16
What about if you Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop > Volumes_Visible?

---

