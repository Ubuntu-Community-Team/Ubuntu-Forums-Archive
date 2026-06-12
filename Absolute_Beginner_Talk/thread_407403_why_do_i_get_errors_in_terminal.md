---
title: "why do i get errors in terminal?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by mpooley on 2007-04-12
why when i type  
sudo gedit blah.sh do i get a string of errors in the terminal but then gedit opens with the file? 

am i doing something wrong?

these are the erros i get every time

mike@mike-desktop:~$ sudo gedit unmount.sh
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by Bushfire on 2007-04-12
I could be wrong of course, but try using the graphical sudo:

```

gksudo gedit unmount.sh

```

---

### Post by renzokuken on 2007-04-12
try 

```
gksudo gedit unmount.sh
``` and see if that gives any errors

---

### Post by gijsbrecht on 2007-04-12
You are doing nothing wrong, the messages are probably related to the input devices that have been installed by default in your X configuration, but which your machine doesn't actually have installed. (I had a wacom stylus, cursor and eraser in my default X configuration, while I don't actually have these devices)

---

### Post by mpooley on 2007-04-12
No that didnt work  in fact i got more errors!  ------
gijsbrecht how do i alter my x config?


mike@mike-desktop:~$ gksudo gedit unmount.sh
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by progprog on 2007-04-14
> No that didnt work in fact i got more errors! ------
gijsbrecht how do i alter my x config?


Hi mpooley,

gijsbrecht is correct.

I don't know the exact contents of your xorg.conf, but just follow the principles here
and you should be fine.

Remember to make a backup beforehand!
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then, to edit your xorg.conf file (assuming gedit is your favorite editor from your commands):

```
sudo gedit /etc/X11/xorg.conf
```


Ok first thing, look for a Section "ServerLayout" in the file.

It should have lines similar to:
```

	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
```

If you don't have Wacom hardware (or you have no idea what the above refers to), it is 
probably safe to remove those lines.

Now you should remove the lines corresponding to each of these.  Each InputDevice line
will have a corresponding Section "InputDevice" in the file.  You can tell which is which by
the identifier, ie Identifier "cursor" .  Remove each of these sections from the Section line
to the EndSection line (inclusive).

Restart X, and see if you get the same errors.


Hope that helps.

---

### Post by mpooley on 2007-04-15
Hi
Thanks very much!     That worked a treat!!:popcorn:

---

### Post by jaywee on 2007-05-04
hmm, works for me too!!

---

