---
title: "is there a boot option to shrink display?"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by moshuptrail on 2006-12-03
When I boot, the splash is too big and the last line of text is below the bottom of the visible screen.  The same thing happens when I ctrl/alt/F2 to close X and go to the black screen.  It's impossible to see what your doing when the cursor goes below the bottom of the screen!

---

### Post by LLRNR on 2006-12-03
I think it's got something to do with the VGA modes that you can specify by editing your /boot/grub/menu.lst file. Here are the generic values (there are other VGA modes for widescreen monitors, but I don't know them, sorry):
[html]
Color depth      | 640x480  800x600  1024x768 1280x1024
-------------------------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795
[/html]

First do a copy of your menu.lst file:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_original
```

You'd have to ```
gksudo gedit /boot/grub/menu.lst
```
or```
sudo nano /boot/grub/menu.lst
```depending on which method you prefer, and then you'd have to locate a line that looks like this one:
```
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro
```
It's usually towards the end of the file. Edit the file with one of the values in the above table - it will look like this one:
```
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro **vga=788**
```

Please don't change anything else in this line, except adding the VGA mode, because this is the line that I have in my menu.lst file, I edited it too to disable the splash (I wanted a clean text boot), yours should be different (I think you run Dapper and the partitions may differ as well).

HTH,

LLRNR

---

### Post by moshuptrail on 2006-12-03
Thanks!  That was exactly what it needed.

(I use sudo vi /boot/grub/menu.lst)

Old fashioned I guess.

---

### Post by LLRNR on 2006-12-03
> **moshuptrail said:**
> 
(I use sudo vi /boot/grub/menu.lst)

Old fashioned I guess.

Thumbs up ! ;)

Good luck, for me it worked for any VGA mode for 16 and 24 bits, I hope it works for you as well.

LLRNR

---

