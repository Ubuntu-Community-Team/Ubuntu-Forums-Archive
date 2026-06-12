---
title: "[SOLVED] all fonts unreadable can only use terminal"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-08-23
my windows hard drive wont boot i put the drive in a usb container and accessed the /windows/fonts via the usb. it wouldn't copy so i was able to copy them to a thumb drive.
I added *.ttf and *.TTF fonts from the thumb drive.
I did it as root (sudo su) i copied them to /usr/share/fonts/truetype/myfonts
i did it in the desktop of the home directory
as root on the terminal
now i have the files in the myfonts folder but they have a red x and i dont' have permission to use them i tried chmod as root to 777 (just desperate)
still not usable.
Help????
before i could reset my cache all of my fonts turned to little squares computer unusable ugh!!!

can ii change my chmod to 746 and get it back that way.

i tried deleting the folder but sudo su
then rm /usr/share/fonts/truetype/myfonts answered this is a directory operation failed.

do i have to reinstall it seems like the chicken way out
__________________

---

### Post by ridgeland on 2007-08-23
try 
$ sudo nautilus
This is an easier way to manipulate rights, owner, delete folders etc.

---

### Post by ridgeland on 2007-08-23
I've copied over fonts before.  This installation though I only used
msttcorefonts
I see it in Synaptics, but I might have downloaded a *.deb.
It gives you:
Installer for Microsoft TrueType core fonts
This package allows for easy installation of the Microsoft True Type
Core Fonts for the Web including:

  Andale Mono
  Arial Black
  Arial (Bold, Italic, Bold Italic)
  Comic Sans MS (Bold)
  Courier New (Bold, Italic, Bold Italic)
  Georgia (Bold, Italic, Bold Italic)
  Impact
  Times New Roman (Bold, Italic, Bold Italic)
  Trebuchet (Bold, Italic, Bold Italic)
  Verdana (Bold, Italic, Bold Italic)
  Webdings

---

### Post by nvteighen on 2007-08-23
> **DarinB said:**
> my windows hard drive wont boot i put the drive in a usb container and accessed the /windows/fonts via the usb. it wouldn't copy so i was able to copy them to a thumb drive.
I added *.ttf and *.TTF fonts from the thumb drive.
I did it as root (sudo su) i copied them to /usr/share/fonts/truetype/myfonts
i did it in the desktop of the home directory
as root on the terminal
now i have the files in the myfonts folder but they have a red x and i dont' have permission to use them i tried chmod as root to 777 (just desperate)
still not usable.
Help????
before i could reset my cache all of my fonts turned to little squares computer unusable ugh!!!

can ii change my chmod to 746 and get it back that way.

i tried deleting the folder but sudo su
then rm /usr/share/fonts/truetype/myfonts answered this is a directory operation failed.

do i have to reinstall it seems like the chicken way out
__________________

Actually, you can install fonts in an easier way.

Enter a **new** terminal and type:
```

mkdir .fonts
nautilus .fonts

```

And copy all fonts there. This will "install" your fonts user-wise and it will be impossible to break your system. (if you have other users, repeat the process for each one). Maybe you'll have to reboot to make them appear in font lists.

---

### Post by DarinB on 2007-08-23
i started this morning by deleting the fonts w/ terminal sudo su. 
i rebooted to get the cache cleared and my system returned to readable and all the boxes disappeared i would like to use the windows fonts i have tons of them but i am worried about messing it up again
how do i use the nautillus i need details since i am a beginner

thank you
db

---

### Post by nvteighen on 2007-08-23
> **DarinB said:**
> i started this morning by deleting the fonts w/ terminal sudo su. 
i rebooted to get the cache cleared and my system returned to readable and all the boxes disappeared i would like to use the windows fonts i have tons of them but i am worried about messing it up again
how do i use the nautillus i need details since i am a beginner

thank you
db

Can you use the graphical interface now or is still broken? Nautilus is almost like Explorer in Windows: you can drag-and-drop files from one folder to another easily. You just have to open the folder where your fonts are and copy them into the ".fonts" folder (don't forget the period at the beginning).

Believe me: it's easier than you think. Actually, what you did was the hardest way possible! Also, don't worry: if you follow exactly the commands I gave you, it's **impossible** to destroy the system: you'll install your fonts into your home folder, without sudo.

---

### Post by DarinB on 2007-08-23
i got my system working and did what you said and added the fonts in .fonts of the home folder it works great i even bookmarked the .fonts folder just in case i have to delete i again

thanks a bunch

sos un Capo!!

db

what folders should i copy to redo my system easy? 
i already have an aptoncd disk made.
then how do i copy the folders back to a new install?
like the home folder or etc folder ??

thanks
db
my favorite line Microsoft gives you a window ubuntu gives you the whole house (home)

---

### Post by ridgeland on 2007-08-23
Hi DarwinB,
Glad you found a solution.
Please edit the post name to include: [Solved] 
To change subjects should be a new thread though.

---

### Post by DarinB on 2007-08-23
sorry i am a newbie how do i mark it solved and i will repost 

sorry about the inconvenience,
Darin

---

### Post by forestpixie on 2007-08-23
thread tools on your first thread post

---

### Post by ridgeland on 2007-08-23
Thanks forestpixie,
I did some house keeping and marked a couple of my own threads [Solved]

---

### Post by nvteighen on 2007-08-24
> **DarinB said:**
> sos un Capo!!
Ché, gracias (y, de saber que hablás castellano...). De lo otro que preguntabas, ahí ya no sé.

---

