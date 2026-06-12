---
title: "Dont know what Im doing"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by Nesagwa on 2005-06-20
(nevermind on the first thing, formatted the whole drive, no big loss though).

When setting up I didnt select all of the higher resolutions I wanted (hit enter by mistake and it only selected 640, 800, and 1024).  How would I get the higher resolutions available again (running a ATI Radeon 9800 Pro).

Is there a simple way to do this?

---

### Post by stonecrest on 2005-06-21
[QUOTE=Nesagwa]Ok.  I just installed Ubuntu.

I installed it on my first partition and left the other existing partition alone.  I know it didnt partition it and I didnt do anything to it.  In windows it was named D (Stuff) and was NTFS.  I read a little bit about mounting partitions but Im really confused about it.[/quote]

You will want to add an entry to your /etc/fstab file (sudo gedit /etc/fstab). It will probably look something like this:
```

/dev/hda1         /mnt/win     ntfs      ro,auto,exec,user,umask=002 0 0

```

This means that when you boot your computer, your windows partition will be automatically mounted to /mnt/win as read-only (it's generally not recommended to write to ntfs partitions in linux). /dev/hda1 assumes that the windows partition is the 2nd partition on your first ide hard drive, change as necessary. Reboot after you've made the change and see if the files show up in /mnt/win.

> Also.  When setting up I didnt select all of the higher resolutions I wanted (hit enter by mistake and it only selected 640, 800, and 1024).  How would I get the higher resolutions available again (running a ATI Radeon 9800 Pro).

Is there a simple way to do this?

You'll want to edit your /etc/X11/xorg.conf file (sudo gedit /etc/X11/xorg.conf). Scroll down to where you see all the resolutions listed and add the ones you want, should be self explanatory. Be sure to restart gnome after you make the change.

---

### Post by aysiu on 2005-06-21
Don't forget to check the HorizSync and VertRefresh ranges, too.

---

### Post by Nesagwa on 2005-06-21
I fixed the second problem.  The first one I tried, but its gone and theres no point worrying about it.

Now I just have to figure out how to run programs I download.......  (such as ZSNES and the like)

---

### Post by poofyhairguy on 2005-06-21
[QUOTE=Nesagwa]

Now I just have to figure out how to run programs I download.......  (such as ZSNES and the like)[/QUOTE]


Just type the name in the "run application" thing.

---

