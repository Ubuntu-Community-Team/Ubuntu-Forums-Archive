---
title: "[SOLVED] can't access added fonts"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-08-22
my windows hard drive wont boot i put the drive in a usb container and accessed the /windows/fonts via the usb. it wouldn't copy so i was able to copy them to a thumb drive.
I added *.ttf and *.TTF fonts from the thumb drive.
I did it as root (sudo su) i copied them to /usr/share/fonts/truetype/myfonts
i did it in the desktop of the home directory
as root on the terminal
now i have the files in the myfonts folder but they have a red x and i dont' have permission to use them i tried chmod as root to 777 (just desperate) 
still not usable.
Help????

thanks db

---

### Post by testube_babies on 2007-08-22
Did you update the font cache after you copied the fonts to /usr/share/fonts?
```
sudo fc-cache -f
```

---

### Post by DarinB on 2007-08-23
before i could do that all of my fonts turned to little squares computer unusable ugh!!!

can ii change my chmod to 746 and get it back that way.

i tried deleting the folder but sudo su 
then rm /usr/share/fonts/truetype/myfonts answered this is a directory operation failed.

do i have to reinstall it seems like the chicken way out

---

