---
title: "I need restart features"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Rich3077 on 2006-07-01
I have yet to convert my wife and kids to linux.. I will though as soon as I can get this system tweaked to their liking. Ubuntu Linux is the default operating system on Grub, I have tried many times to edit my grub file with no luck.
I even installed gnome-system-tools because its supposed to have a graphical grub editor and I cannot find evidence of any such editor anywhere.. and I am sure its installed. I even reinstalled it a couple of times. If they miss the bootloader Linux will load and once its loaded there is no option to reboot on the login screen.. and if you log in there is still yet not an option to reboot. I really need to resolve this as trapping them within Linux is not the best way to convert them. Any advice is appreciated.


Peace
Rich

---

### Post by falcon15500 on 2006-07-01
Ummm... Configuring GRUB to default boot Windows should be pretty simple.  I can't help you with that though, as mine doesn't have a windows entry (my main boot loader is NTLDR).

However you definately should have a reboot option on the login screen.  I am at work at present on a windows box, so I won't have the names right - but on the login screen, bottom left corner there should be an option there... Sessions, it might be called.  In that there should be a reboot option.

Failing that, when you login to Gnome (you did say Ubuntu, not K or X) there should be a big red button on the top right hand corner of the screen.  Click that and a window will pop up with options - including reboot.

falc

---

### Post by Rich3077 on 2006-07-01
No reboot options in any of those places.

---

### Post by falcon15500 on 2006-07-01
Something strange with your setup then, as they are definitely there on mine!

Anyone else got any ideas?

falc

---

### Post by Rich3077 on 2006-07-01
[QUOTE=falcon15500]Something strange with your setup then, as they are definitely there on mine!

Anyone else got any ideas?

falc[/QUOTE]

The reboot option was there at one time.. but I have been screwing around with just about every setting imaginable trying to set this install up to meet my needs. I have no clue what I did to remove the reboot option.


Peace
Rich

---

### Post by Rich3077 on 2006-07-01
Okay I fixed it by going to system/administration/login window and checking the box for "show actions menu"

Peace
Rich

---

### Post by Nikusan on 2006-07-01
```
sudo gedit /boot/grub/menu.lst
```

Find this line:

default		0


Replace the 0 with a 4 or 5 or so. You can find out the number you need by counting the lines in the grub menu when you boot. Remember that the "Other OS's" line is counted.

---

### Post by aysiu on 2006-07-01
[QUOTE=Rich3077]No reboot options in any of those places.[/QUOTE]
Something's wrong with your GDM or KDM, then. [quote=Nikusan]
```
sudo gedit /boot/grub/menu.lst
```[/quote] It may be fine for Gedit, but in general I would recommend *gksudo* for graphical applications. Read more about why here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> Find this line:

default 0


Replace the 0 with a 4 or 5 or so. You can find out the number you need by counting the lines in the grub menu when you boot. Remember that the "Other OS's" line is counted. Keep in mind that numbering starts at 0.

First entry - 0
Second entry - 1
Third entry - 2
etc.

---

