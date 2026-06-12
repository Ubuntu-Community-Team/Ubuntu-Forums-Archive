---
title: "making a folder for hda1 on the desktop"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by amidude on 2007-03-20
I just bailed on SuSE Linux and one of the things that I enjoyed about that flavor of Linux was the ability to have my NTFS partition show up on the desktop. I followed the instructions at "psychocat" to set up my new mount point and now /dev/hda1 is mounted on /windows.

My query is to how one would set it up to where I could traverse that mounted point in a window on the desktop versus only being able to use the terminal window.

Any help would be greatly appreciated. Thx.

---

### Post by Efwis on 2007-03-20
first make sure that under Applications=>System tools you have configuration editor available. if not you can show using applications=>accessories=>Alacarte menu editor, and in the section for system tools check the box next to configuration editor.

now in configuration editor click on Apps => Nautilus => Desktop then put the checkmark next to volumes visible. This will put an icon on your desktop that is direct access to your Windows drive.

---

### Post by taurus on 2007-03-20
Just mount it to /media/windows instead of /windows in /etc/fstab.  Then, you would see an icon on your desktop for your partition, /dev/hda1.

Don't forget to create a new mount point, /media/windows, if you decide to change the mount point.

```
sudo mkdir /media/windows
```

---

### Post by silkstone on 2007-03-20
^^^^^ What he said! I fiddled around for ages with the same thing until I discovered that you had to mount to a subdirectory of /media for it to show. I should have asked!

---

### Post by amidude on 2007-03-20
thx...changed it. Now do I remove the /windows directory I created?

---

### Post by taurus on 2007-03-20
If you want.

```
sudo rmdir /windows
```

p.s.  Don't forget to reboot first it so /dev/hda1 will be mounted to /media/windows before you run that command from above.

---

### Post by amidude on 2007-03-20
Thank you so much for your help. You guys are great.

---

