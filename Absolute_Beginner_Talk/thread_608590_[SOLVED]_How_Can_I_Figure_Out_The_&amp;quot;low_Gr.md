---
title: "[SOLVED] How Can I Figure Out The &amp;quot;low Graphic Mode&amp;quot;?```"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by biobread on 2007-11-10
everything is ok just after i finished installing my ubuntu
the resolution is 1280*1024 
but after i enabled the ati accelerated graphic driver in RESTRICTED DRIVERS and restarted the OS i entered the low graphic mode 
the resolution is locked at 800*600 
i really need help... sorry for my poor english
[img]http://photo11.yupoo.com/20071110/193753_623597845_acaxclpx.jpg[/img]

---

### Post by overdrank on 2007-11-10
HI and what is the model of the ati card? You may try this command in the terminal 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` And hopefully this will help.

---

### Post by biobread on 2007-11-10
thanks a lot
i'm running on a radeon hd 2600 pro... 
i've tried your code 
it replies:
dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !



what should i do..?.

---

### Post by overdrank on 2007-11-10
> **biobread said:**
> thanks a lot
i'm running on a radeon hd 2600 pro... 
i've tried your code 
it replies:
dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !



what should i do..?.

Hi and that is strange, did you copy and paste that command? You may need to make sure you type that command correct or just paste it in the command line. :confused:

---

### Post by biobread on 2007-11-10
:o this time it replies this:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071110201548

shall i restart?

---

### Post by overdrank on 2007-11-10
> **biobread said:**
> :o this time it replies this:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071110201548

shall i restart?

You can try and just restart X with the ctrl, alt, backspace keys, but a restart maybe better. :)

---

### Post by biobread on 2007-11-10
Great!~!! the resolution is back to normal:) THANKS!

but i find the MODEL in SCREEN AND GRAPHIC is still PLUG N PLAY 
what is it? everytime i change it to samsung 730b the screen will crash.
and the DRIVER is still VESA -GENERIC VESA-COMPLIANT VIDEO CARDS
could you please tell me how to install the latest ATI DRIVER properly?

---

### Post by overdrank on 2007-11-10
> **biobread said:**
> Great!~!! the resolution is back to normal:) THANKS!

but i find the MODEL in SCREEN AND GRAPHIC is still PLUG N PLAY 
what is it? everytime i change it to samsung 730b the screen will crash.
and the DRIVER is still VESA -GENERIC VESA-COMPLIANT VIDEO CARDS
could you please tell me how to install the latest ATI DRIVER properly?

HI and I have not had the privilege to use that card as of yet. SO if the system is working you should search the forums and then be sure before you make any changes to your xorg is back it up. This way you can just restore the backup if it goes wrong. 
To copy Xorg
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
To restore backup
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
Good luck!

---

### Post by biobread on 2007-11-10
Ok Thnks~:)

---

