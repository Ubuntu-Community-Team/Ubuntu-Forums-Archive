---
title: "GeForce 7400Go (Dell XPS M1210) Nvidia Driver Issues"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by planetes42 on 2007-07-04
I am trying to install the proper Nvidia drivers (for GeForce 7400Go on Dell XPS M1210).

I followed the instructions on this site: [http://www.nvidia.com/object/linux_display_ia32_100.14.11%20.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11%20.html)
and the result was a black screen with a blinking cursor.  

I also followed Method 1 of this site: [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty).
This allowed me to select "Nvidia" as my driver in Settings -> Monitor & Display -> Hardware, but choosing my exact card made no difference (the next time I logged in, it reverted back to card: nv)

Simply selecting my card in Settings -> Monitor & Display -> Hardware leads to a screen with black/white/gray squiggly lines & a large 'x' as a cursor that I can't get out of.

I have backed up my xorg.conf so whatever changes I try I can 'undo'.  

Thank you so much for your help in advance!

---

### Post by mmogar on 2007-07-04
The screen with the gray/black squiggly lines is showing the error that is causing x not to load. You can also see it in the log:
/var/log/Xorg.0.log

That will at least tell you what is failing and at what point and maybe you can edit your bad Xorg.conf file to correct it.

---

### Post by Alfdog on 2007-07-11
I use Envy to install my nvidia drivers, it's pretty easy you should give it a shot.

---

### Post by testube_babies on 2007-07-11
EDIT:  wrong thread :P

---

