---
title: "Anyone getting a crappy 16 color usplash screen?"
date: 2006-10-26
forum: Apple PPC Users
---

### Post by plush on 2006-10-26
For some reason I'm getting a teeny tiny usplash that appears to be in 8 bits or something.  I think it's because of having an nVidia card.  It looks awful.  IS there any way to fix this?  I use a widescreen cinema display, but I'm sure that can't be it, can it?

---

### Post by Doobie9 on 2006-10-27
I have a G4 with a Nvidia card and I get a crappy splash screen as well. And I also can only see 16-bit colors when I log in -- everything looks like crap! 

And my xorg.conf says I have 24 bit.

---

### Post by Dixius99 on 2006-10-27
I think I have the same problem, but I have an ATI card (X700). I'm running from the live CD so far.

I tried to take some photos of it, but none of them turned out due to the relatively black screen; either came out with a lot of glare (lights on), or the ubuntu logo was so bright, it glowed and obscured the problem (lights off).

To try to explain the problem, the usplash is displaying as a black background, and all elements look very dithered, especially a halo that surrounds all of the letters. After progressing most of the way through loading, it changes, but is still very dithered, and along the length of the progress bar are blue scribbles.

When shutting down, the text that says "Please remove the disc, and close the tray (if any)..." is a very dark blue, and almost invisible on the black background.

My usplash certainly doesn't look like the one [here]("http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution=Ubuntu%206.10").

For me, the letters are all red outlines, and much more dithery...

---

### Post by mongee on 2006-10-28
You need to modify the settings in the /boot/grub/menu.lst file. Set the vga option to be one from the table in [this post]("http://www.ubuntuforums.org/showthread.php?p=1541970")

---

### Post by plush on 2006-10-28
There is no GRUB, Apple PPC users use Yaboot!  Thanks anyway :)

---

### Post by plush on 2006-10-28
I believe this is an incorrect bit depth issue at startup.  If only I knew more about video settings in the init file or with yaboot...:-k

---

### Post by zenzo82 on 2006-10-28
well as i know grub allows the setting vga=xyz but yaboot does not.
i hope someone could deny this.

---

### Post by Torrance on 2006-10-28
A new kernel with the 24bit splash option enabled fixes this... unfortunately, Edgy wont let me compile any kernels right now, so I'm stuck with a purple mess in the top right of my screen on start up.

---

### Post by Dixius99 on 2006-10-29
> **mongee said:**
> You need to modify the settings in the /boot/grub/menu.lst file. Set the vga option to be one from the table in [this post]("http://www.ubuntuforums.org/showthread.php?p=1541970")

Thanks mongee.

BTW: for those of us who are still running the live CD, the video options can easily be set from the first boot menu (the one that asks whether to load Ubuntu, load the installed OS, check the CD, etc.)

Just hit F4, and select one of the options that your video card can support.

---

### Post by je m'ennuie on 2006-10-29
F4 doesn't give anything for me. Seems to be hopeless

---

### Post by plush on 2006-10-30
:???: Doh!  I KNEW you were gonna say that 

> **Torrance said:**
> A new kernel with the 24bit splash option enabled fixes this... unfortunately, Edgy wont let me compile any kernels right now, so I'm stuck with a purple mess in the top right of my screen on start up.

---

