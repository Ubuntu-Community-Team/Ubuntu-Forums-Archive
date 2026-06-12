---
title: "Make Grub Default to Load Windows"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by meistercobbman on 2007-01-02
I just installed Ubuntu Edgy on my laptop. I already have WindowsXP. I want the grub to load the windows OS first, unless I do something to direct it to load Ubuntu. Preferably, I would like to just hold down a key on the keyboard, such as "L" or "U" and that would tell the grub to load Ubuntu instead of WinXP. Anybody know how to do that? Thanks!

---

### Post by h0ax on 2007-01-02
What you want to do is edit your grub's menu.lst located --> /boot/grub/menu.lst

search around on the forum for ways to do this.
Also - just turn off the option for menudisplay in menu.lst and it will say "Push ESC to open Grub menu" - otherwise it will boot to the first option
if you have windows first, there you go.

---

### Post by K.Mandla on 2007-01-02
You'll need to boot into Ubuntu to edit the /boot/grub/menu.lst file. Find the line that says "default 0" and change it to automatically pick the Windows boot line. I think, but I'm not sure, that it's usually 3. It will vary with kernel updates and where Windows is in the menu.lst file.

---

### Post by meistercobbman on 2007-01-11
got it all worked out. thanks! i had permissions issues... which i learned to handle... in terminal, type sudo gedit /boot/grub/menu.lst. i felt like a powerful newb after that.

---

### Post by MyBuntu on 2007-01-21
easy just copy the windows info before the ubuntu info......

Quote from meistercobbman:

Step 1: "in terminal, type sudo gedit /boot/grub/menu.lst"

the window pops up "menu.lst(boot/grub)-gedit"

SCROLL DOWN HALF WAY WHERE IT STARTS:


[I]
## ## End Default Options ##

title		Ubuntu, kernel 2.6.-1-36
root		(hd0,5)
kernel		/boot2.6.1root=UUID=dad ro quiet splash
initrd		/boot/initrd.im.-
savedefault
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		OTHER OPERATING SYSTEM
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4

title		Windows NT/2000/XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1

..........[/I]

OKAY SO COPY EVERYTHING BELOW THE "OTHER OPERATING SYSTEM"
AND PASTE IT ONTOP OF THE UBUNTU INFO...LIKE THIS


## ## End Default Options ##

[I]
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows NT/2000/XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1[/I]

title		Ubuntu, kernel 
root		(hd0,5)
kernel		/boot/vmlinuz-6 root=UD=uiet splash
initrd		/boot/inmg-2
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		OTHER OPERATING SYSTEM
ROOT







RESTART WHEN YOU feel LIKE IT.....FYI YOU CAN ALSO RENAME THE TITLE FOR WINDOWS XP/2000/NT TO ANYTHING "LINUX IS BETTER" DOESNT REALLY MATTER WHAT MATTERS IS THE ROOT (hd, 1) where 1 is where your windows partition is located...so dont mess with this unless you know exactly where it is.

---

### Post by meistercobbman on 2007-01-21
Yeah I even found out that you can put anything you want as an option by doing:
**title** *say what ever you want here*
**root** *leave this blank for null selection, or specify drive (hda0,1) to boot to if selected *

(in the section where all the boot options are listed, just after
 ## ## End Default Options ##).

By doing this I was able to make my grub say cheesy things like this:
[INDENT]Hello, you always turn me on when your around...

Gimme some Ubuntu, baby!
Windblows XP[/INDENT]

I set the fist line to default to Ubuntu (I switched from XP for many typical reasons), just in case I wasn't around to move the cursor to the  "Gimme some Ubuntu..." line, so it would always load.

Here's an example of the first line:
> title		Hello, you always turn me on when you're around...
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

---

### Post by jbayone on 2007-01-21
I recommend grubed.  It's really easy to use and you can customize the colors and background and stuff if you want.

---

### Post by jbayone on 2007-01-21
Sorry, here's the link - [http://www.ubuntuforums.org/showthread.php?t=228104&highlight=grubed]("http://www.ubuntuforums.org/showthread.php?t=228104&highlight=grubed")

---

### Post by maurolust on 2008-04-30
I've come here with the same purpose, but this doesn't work for me. This is what I get. 
> 
mauro@hamming:~$ sudo gedit /boot/grub/menu.lst
sudo: gedit: command not found
mauro@hamming:~$ sudo gedit/boot/grub/menu.lst
sudo: gedit/boot/grub/menu.lst: command not found


The two last lines were just me checking if I had left too many blank spaces, but since I'm working as root this can be dangerous, right?

I'm using XubunTOS.

---

### Post by akiratheoni on 2008-04-30
> **maurolust said:**
> I've come here with the same purpose, but this doesn't work for me. This is what I get. 


The two last lines were just me checking if I had left too many blank spaces, but since I'm working as root this can be dangerous, right?

I'm using XubunTOS.

I don't think Xubuntu comes with gedit. I think it comes with a text editor called 'mousepad'. So try:

```
gksu mousepad /boot/grub/menu.lst
```

Just remember, if you're running graphical apps as root, run it as 'gksu' (or 'kdesu' if you're using KDE), not 'sudo'.

---

### Post by maurolust on 2008-04-30
My problem is solved, thank you everyone for helping :KS. I would just like to mention that -- in my humble opinion -- no excessive *menu.lst* editing should be encouraged to beginners  like myself (the main target in this forum)

What I mean is that after I got the hang of it, I realized the simplest thing to do was just edit the parameter *default 0* to *default saved* in the beginning of the menu.
 
After that, GRUB itself allows me to set the OS I chose as the default (and to erase the *savedefault* statement from the wrong OS). I can only wonder why GRUB doesn't set *saved* as default (something to do with dmraid?), which would enable me to solve this problem without ever typing sudo. I considered installing GRUBED, but since it doesn't even have a DEB package assembled yet I figured it's a bit early for this.

---

