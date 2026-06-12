---
title: "no screens found, apt-get didnt fix it..."
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by taseal on 2005-09-22
I recently had a friend guide me through the livecd update and everything worked out when he told me to use the command

sudo apt-get install xorg-driver-fglrx

now i just did that, and it installed the drivers etc. but it still gives me the same error :(

whats going on?

i'm just surpised cuz it worked on livecd but not once i installed it?

---

### Post by taseal on 2005-09-22
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

well i found this and some more info on the forums, but i'm kinda confused now :(

---

### Post by xmastree on 2005-09-22
Here's an idea. I suspect it's something with your xorg.conf file.
So... boot from the live CD again, copy etc/X11/xorg.conf to something external. Floppy, flash disk, whatever.

Then go back to your install, back up your original and copy the live CD's one over it.

Might work.

---

### Post by taseal on 2005-09-22
[QUOTE=xmastree]Here's an idea. I suspect it's something with your xorg.conf file.
So... boot from the live CD again, copy etc/X11/xorg.conf to something external. Floppy, flash disk, whatever.

Then go back to your install, back up your original and copy the live CD's one over it.

Might work.[/QUOTE]
 ok lets try that and see what happens

but nothing is easy.. so it prolly wont work til i try 50 more ways to do it :D

since i'm kinda new i'm not sure how to copy over something in the termnial window... how do i do that? (where it says ubuntu $)

---

### Post by heimo on 2005-09-22
put in formatted blank floppy
```

mount /media/floppy
cp -a /etc/X11/xorg.conf /media/floppy
umount /media/floppy

``` 

boot back to your regular install
```

mount /media/floppy
sudo cp -a /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo cp -a /media/floppy/xorg.conf /etc/X11
umount /media/floppy
 
```

EDIT: You can probably do all this in GUI too.

---

### Post by taseal on 2005-09-22
[QUOTE=taseal]ok lets try that and see what happens

but nothing is easy.. so it prolly wont work til i try 50 more ways to do it :D

since i'm kinda new i'm not sure how to copy over something in the termnial window... how do i do that? (where it says ubuntu $)[/QUOTE]
 wtf ugh

right after it says xserver is disabled and disabling GNI (w/e that said i cant remember lol)

the ubuntu$ used to come up... now its just the blinking cursor and i cant input any info :mad:

---

### Post by heimo on 2005-09-22
Blinking cursor? Just a short white line - does it show any text at all? (I'm just trying to understand if you're on console or not.)

You can change between virtual consoles using CTRL+ALT+F1 .. F2 .. F3 and so on. Normally, GUI (graphical user interface, X) is on F7. You can kill GUI/X pressing CTRL+ALT+backspace. If you can't do that, you can always boot to recovery mode. At the very beginning of boot, hit [esc] to see Grub menu (boot loader menu).

From there, you can copy back the backup xorg configuration (if you just followed my instructions), using cp command:
 ```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` 
Or you could just try to reconfigure X using this command:
 ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by taseal on 2005-09-22
[QUOTE=heimo]Blinking cursor? Just a short white line - does it show any text at all? (I'm just trying to understand if you're on console or not.)

You can change between virtual consoles using CTRL+ALT+F1 .. F2 .. F3 and so on. Normally, GUI (graphical user interface, X) is on F7. You can kill GUI/X pressing CTRL+ALT+backspace. If you can't do that, you can always boot to recovery mode. At the very beginning of boot, hit [esc] to see Grub menu (boot loader menu).

From there, you can copy back the backup xorg configuration (if you just followed my instructions), using cp command:
 ```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` 
Or you could just try to reconfigure X using this command:
 ```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]

yeah it was ctrl alt f2

my friend just helped me out with it

he made me configure it with sudo... couldnt have been any easier, i forget what the comand was but i think it was like sudo flgrxrconfigure or something just a single word

---

