---
title: "How do I get widescreen resolutions?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by pdxuser on 2007-03-16
I've just installed Xubuntu 6.10.  I have a widescreen LCD TV with computer inputs that I've used on this computer when it had Windows.  Its native resolution is 1280 x 800.  Yet the only available resolutions in Display Preferences are 1024x768, 800x600, and down.  Is there some way to get a widescreen video card driver?  I don't even know where to go to manage drivers or devices like video cards.

Thanks to everyone who has helped get me started!

---

### Post by mahy on 2007-03-16
You don't need another driver. Just edit your /etc/X11/xorg.conf
Find a line with monitor resolutions specified and put the desired resolution there. For me it's 1280x800. Then  you'll have to restart the X server by means of Ctrl+Alt+Backspace.

---

### Post by pdxuser on 2007-03-16
Cool.  When I go to save, though, I get the error, "Can't open file to write."  I'm guesing this has something to do with user permissions, but I'm the only user on here so far.  I also had this problem trying to save a new background into the background folder.

---

### Post by Aliarse on 2007-03-16
in a terminal, type ```
gksudo gedit /etc/X11/xorg.conf
``` and re-do the steps you just did.

---

### Post by pdxuser on 2007-03-16
I copied and pasted that line, it asked me for the Administrator password, I gave it, then hit enter again for the command and nothing happened, I just got to the next prompt.  So, seeing the instructions on the terminal that said I should use sudo <command> to run something as an administrator, I tried that.  Command not found.  Now even if I type "gksudo gedit /etc/X11/xorg.conf" again, I get "sudo: gedit: command not found".  How do I get out of this sudo mode?  I don't even know what sudo or gksudo is.

---

### Post by aysiu on 2007-03-16
Xubuntu doesn't have Gedit. It has Mousepad.

What you want is this: ```
gksudo mousepad /etc/X11/xorg.conf
```

By the way, when you say "I just got to the next prompt," are you saying this is what happened? ```
pdxuser@ubuntu:~$ gksudo gedit /etc/X11/xorg.conf
pdxuser@ubuntu:~$ 
``` No errors or anything?

And if that's the case, why do you then get that the command is not found also?

---

### Post by pdxuser on 2007-03-16
That's exactly what happend, Aysiu.  But your command worked!  Thanks.  The only problem is, after I changed all the 1024x768's to 1280x800 and pressed Ctrl-Alt-Backspace, I got an "out of range" error on my monitor and now I can't use my computer because I can't see.  I'm currently on a different computer.  Is there something akin to Windows Safe Mode I can use to fix it?

---

### Post by aysiu on 2007-03-16
> **pdxuser said:**
> That's exactly what happend, Aysiu.  But your command worked!  Thanks.  The only problem is, after I changed all the 1024x768's to 1280x800 and pressed Ctrl-Alt-Backspace, I got an "out of range" error on my monitor and now I can't use my computer because I can't see.  I'm currently on a different computer.  Is there something akin to Windows Safe Mode I can use to fix it?
Press Control-Alt-F1

This will bring you to a virtual terminal (hopefully)

If it does, go ahead and log in.

Then type ```
sudo nano /etc/X11/xorg.conf
``` and change the file back (ideally, you would have a backup copy you could just restore--not sure if you made one). When you're done making your changes, press Control-X, Y, and Enter to save.

Then press Control-Alt-F7 to get back to graphical mode and then Control-Alt-Backspace to reset the X server (to have your changes take effect).

By the way, this problem is supposed to be fixed as of the next Ubuntu release (out next month) with a new feature called "bullet-proof X":
[https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x](https://blueprints.launchpad.net/ubuntu/+spec/bullet-proof-x)

---

### Post by pdxuser on 2007-03-16
Unfortunately, I had already turned the computer off, but I restarted in recovery mode, typed in what you said, and I'm back in business.  I used 1280 x 764, which was the best available option Windows gave me before.  Phew!

---

### Post by Pugwash on 2007-03-16
Maybe you haven't got the correct drivers. I don't get  widescreen resolution on my laptop until I install the ati drivers.

---

### Post by wazesz on 2007-03-16
Im new to linux and i have the same problem.  I tried changing the xorg.conf like mentioned, and restarted server x also restarted pc just to make sure..it didnt change..none of the possible settings are widescreen.  I then installed 915resolution like mention in other threads.  it gave me some kind of error like this:

"
Intel 800/900 Series VBIOS Hack : version 0.5.2

Intel chipset detected.  However, 915resolution was unable to determine the chipset type.
Chipset Id: 29a08086
Please report this problem to [email]stomljen@yahoo.com[/email]
"


i'm new at this and have been browsing for answers all day.  the computer im using is an HP A1640N with intel GMA 3000+ graphic card.  Can someone help me, im ready to give up windows for good but looking at the a screen that is stretched out is giving me a headache..

help this super linux noob.

---

