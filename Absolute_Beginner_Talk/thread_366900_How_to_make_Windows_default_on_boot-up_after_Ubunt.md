---
title: "How to make Windows default on boot-up after Ubuntu install"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by jkrumm on 2007-02-21
I've installed Ubuntu edgy and like it quite a bit (except for the mysterious and myriad program installing methods that I hope will be helped by CNR--I was hoping for a simple way to install a chess game...). But now my wife is pissed because if she doesn't pay attention on Bootup the computer just boots into Ubuntu. How do I switch it so Windows is the default bootup, with Ubuntu a choice down the list? I've looked at some of the options with the bootup screen, but none seem very clear (I was hoping for "make Windows the default at boot--click here").

---

### Post by mikewhatever on 2007-02-21
You'll have to edit the GRUB menu
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

to save you time and trouble, it is this part:
> Changing the default (operating system booted by the timer)

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

fig 8 grub

---

### Post by jkrumm on 2007-02-21
Thanks, I think I managed to change it. But it was all very cryptic, and difficult to know if what I was doing was right. Absolute newbies like me could really use step by step instructions for doing common requests like this. The instruction page you sent me to was way too complicated. We need something written with the absolute newbie in mind. That might make serious Linux users sigh since they've taken the time to learn all the commands and such, but that's the way it is. 

Thanks again,

John

---

### Post by Vivix729 on 2007-02-21
Out of curiosity, why did you have so much trouble installing a game?  You can just go to Add/Remove menu, find your chess game under Games for example, and click Ok.  That's it.

---

### Post by jkrumm on 2007-02-21
I tried installing the available chess games in the add/remove program, but they all say they conflict with existing software, and to go to advanced mode.

---

### Post by chaplanger on 2007-02-21
Try these instructions for altering your boot order, (attached in Open Office format).

Post back if you need additional help.

---

### Post by jkrumm on 2007-02-22
Thank you very much for the last set of instructions. After three tries, 6 was the magic number and my computer now boots first to Windows, to my wife's delight (I thought previously I had changed boot prefs but I hadn't). You have eradicated a potential source of marital strife. 

I think a simple graphical Grub would be a worthy addition to Ubuntu, as I suspect many beginner adopter/experimenters will have the same problem that I did.

---

### Post by kryos on 2007-02-22
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
This site has helped tremendously with Dapper so I'm sure with Edgy too.

I had to do the same for my family!  Just updated with new kernel and had to increase the default number by 2.  Have had 2 kernel updates so far but am getting used to the terminal.
Good luck.

---

