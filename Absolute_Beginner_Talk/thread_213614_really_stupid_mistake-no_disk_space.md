---
title: "really stupid mistake-no disk space"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by sweeney on 2006-07-11
well, i left my laptop running, pasting copied files to fill up unused disc space before 'secure' deletion.

in the meantime the process finished and the laptop shut down.

I returned today to log on and, OF COURSE, my disk was full and i had no space left to log on: GDM could not write to my authorisation file.

so, can anybody help me to log on without the requsite disk space???

---

### Post by stupidkid on 2006-07-11
You can always use a LiveCD.

---

### Post by timetunnel on 2006-07-11
Download somethin which runs a Linux from CD-ROM,  like Knoppix. Once it's fully started you can mount your hard drives with read/write access and free up some space. Be careful not to delete wrong files.

[http://www.knoppix.com](http://www.knoppix.com)

Jens

---

### Post by sweeney on 2006-07-11
is there any other solution? is there no way to get into the command line and delete files there before Gnome loads???

---

### Post by timetunnel on 2006-07-11
You could try to boot up you system by choosing "recovery mode" in the boot manager. IIRC this will boot but won't start the X-Server / GNOME. From there you can fiddle around with the command line, I guess.

---

### Post by sweeney on 2006-07-13
problem fixed successfully through the command line

---

### Post by Engnome on 2006-07-13
> **timetunnel said:**
> You could try to boot up you system by choosing "recovery mode" in the boot manager. IIRC this will boot but won't start the X-Server / GNOME. From there you can fiddle around with the command line, I guess.

I've always wondered what's so special about "recovery mode" and that's it? no gdm or xserver? If that's all I think I'll make that my NORMAL boot bc I don't always need gui.

---

### Post by bluenova on 2006-07-13
> **Engnome said:**
> I've always wondered what's so special about "recovery mode" and that's it? no gdm or xserver? If that's all I think I'll make that my NORMAL boot bc I don't always need gui.
I think there is more to it than that, like hardware support etc. The best way to not boot the GUI is to boot to a lower runlevel.

---

