---
title: "Messed up graphics during install"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by panzerfaust on 2006-06-20
I keep on getting screens like this one when I tries to install ubuntu: [[IMG]http://img48.imageshack.us/img48/5975/dsc000619rg.jpg[/IMG]](http://imageshack.us)
The graphics are totally messed up, and I've tried with both the 5.10 install cd (ordered from shipit.ubuntu.com) and 6.06 (downloaded ISO)
I know there's nothing wrong with my graphics card, it works fine in WinXP and Win2k.
The first menu that appears when I boot from the 6.06 cd looks normal, just like the blue interface when I edit the Xserver, when I used the command prompt in v5.10
Anyone who knows what to do?
My system: (If it matters)
P4@3GHz HT
Radeon 9600 pro 256MB
2x512MB DDRAM@400MHz

---

### Post by taurus on 2006-06-20
Are you using the desktop version?  If you are, try using the alternate version and see if you can install it...  Otherwise, go for the server and then install Gnome after that.
```

sudo apt-get install ubuntu-desktop

```

---

### Post by doonium on 2006-06-20
what kind of video card do you have?

i had a similar problem when X starts with an nvidia card and the open source drivers that come by default.  i installed the closed source drivers, and the problem went away.  if you can get to a command line, i believe its the nvidia-glx package.

oops, just realized you had a radeon, i dont know about their drivers.

---

### Post by taurus on 2006-06-20
[QUOTE=doonium]what kind of video card do you have?

i had a similar problem when X starts with an nvidia card and the open source drivers that come by default.  i installed the closed source drivers, and the problem went away.  if you can get to a command line, i believe its the nvidia-glx package.

oops, just realized you had a radeon, i dont know about their drivers.[/QUOTE]
It says "Radeon 9600 pro 256MB" at the bottom of his post...

---

### Post by richbarna on 2006-06-20
I think this will get you up and running :-
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25")

---

### Post by doonium on 2006-06-20
[QUOTE=taurus]It says "Radeon 9600 pro 256MB" at the bottom of his post...[/QUOTE]
it says i noticed that at the bottom of mine :)  

just bringing up the fact that binary drivers may cure the problem

---

### Post by panzerfaust on 2006-06-21
[QUOTE=taurus]Are you using the desktop version?  If you are, try using the alternate version and see if you can install it...  Otherwise, go for the server and then install Gnome after that.
```

sudo apt-get install ubuntu-desktop

```[/QUOTE]
I managed to install it with the alternative cd, and the graphics was fine as long as it was the blue install interface, but I get similar messed-up graphics when i tries to start the installed ubuntu.


[QUOTE=richbarna]I think this will get you up and running :-
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25")[/QUOTE]

[QUOTE=BinaryDriverHowto/ATI]```
sudo apt-get install linux-restricted-modules-$(uname -r)
```[/quote]how do I write the "$"? altgr+4 doesn't work. [EDIT]It was my faulty keyboard[/EDIT]  Should I replace "uname" with my username?
I haven't used an linux/GNU OS before.

---

### Post by doonium on 2006-06-21
no, you type out 'uname' ... it is a command that prints system info, 'uname -r' will will print your kernel release

---

### Post by panzerfaust on 2006-06-21
ok, done. But the guide tells me to edit the xorg.conf file
```
sudo gedit /etc/X11/xorg.conf
```
but that code just gives me the message: "cannot open display: (null) Run 'gedit --help' to see available commands options"

And one other thing, does linux care if i type commands and filenames in small or  capital letters, like windows doesn't?

---

### Post by confused57 on 2006-06-21
[QUOTE=panzerfaust]ok, done. But the guide tells me to edit the xorg.conf file
```
sudo gedit /etc/X11/xorg.conf
```
but that code just gives me the message: "cannot open display: (null) Run 'gedit --help' to see available commands options"

And one other thing, does linux care if i type commands and filenames in small or  capital letters, like windows doesn't?[/QUOTE]

You can try:
```
sudo nano /etc/X11/xorg.conf
```

Yes, lowercase and uppercase makes a difference in Linux.

---

### Post by panzerfaust on 2006-06-21
ok, but now, how do I save the file and quit?
There's a bunch of commands in the bottom of the screen like: ^G Get Help ^X Exit ^O WriteOut. but I don't know how to use them.

---

### Post by Blitzace on 2006-06-21
You don't need to manually do anything, do this:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-xconfig

then restart.

---

### Post by confused57 on 2006-06-21
[QUOTE=panzerfaust]ok, but now, how do I save the file and quit?
There's a bunch of commands in the bottom of the screen like: ^G Get Help ^X Exit ^O WriteOut. but I don't know how to use them.[/QUOTE]

Sorry, I should have mentioned that,  the "^" symbol is for pressing "Ctrl"+X, for example to exit, which will ask you if you want to save or ^0 to save.

---

### Post by panzerfaust on 2006-06-22
[QUOTE=Blitzace]You don't need to manually do anything, do this:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-xconfig

then restart.[/QUOTE]
should I use the "sudo nvidia-xconfig" command even if I've got an ati card?

> Confirm it worked: 
```

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.8)

```
How do I use this command? writing "$ fglrxinfo" just gives an error message: "bash:$ command not found"
I still only can start ubuntu in the recovery mode, or I will nust get a screen of wierd graphics.

---

### Post by Blitzace on 2006-06-22
Lol I'm such a klutz, I didnt read that you had an ATI card.... Sorry can't help you there...

---

### Post by confused57 on 2006-06-22
See if there's anything in this thread that might help:
[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

Read further down on the first page of the thread, someone mentioned 3 simple
commands that might work for you.

---

### Post by panzerfaust on 2006-06-23
:) Thank you, I will see if that helps.

EDIT: Didn't help, but everything works nice now when I'm using an old hercules pci card instead. It's possible to install my ATI card later, right?

---

