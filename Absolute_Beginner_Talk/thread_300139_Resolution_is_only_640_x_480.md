---
title: "Resolution is only 640 x 480"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Jdanniel on 2006-11-15
Hello.

I just installed Ubuntu 6.06 LTS (Dapper) on my older computer, which I custom-built.  (It has an AMD Athlon 1.0 Gigahertz processor, and only a 16 MB video card.  It is NOT connected to the Internet, nor will it be.)

The resolution is currently only 640 x 480, and there is no other option.  When I ran Ubuntu briefly as a Live CD, the resolution was higher.  I've run Windows XP on this computer for a long time, and even installed the beta of Vista on it, and the resolution was higher.

Is there anything I can do to change the resolution?  Thank you!

J. Danniel (Call me Jd)

PS:  If you need more information about this computer, please let me know.

---

### Post by BarfBag on 2006-11-15
What kind of video card does it have?

---

### Post by jd65pl on 2006-11-15
try running

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

From the terminal, select the resolutions you require then reconfigure with the screen resolution gui

---

### Post by Jdanniel on 2006-11-15
Honestly, it's been so long since I built the computer (7 years), I don't remember exactly what make/model card it is, but it only ha 16 MB of video ram.  I'm pretty sure it's an NVIDIA but beyond that, I can't tell you.

---

### Post by Jdanniel on 2006-11-15
"From the terminal, select the resolutions you require then reconfigure with the screen resolution gui"

I'm brand new to Linux and don't yet understand this.  Can you guide me through it in a little more detail?  Thank you.

---

### Post by jd65pl on 2006-11-15
Appologies....
Copy this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Go to APPLICATIONS > ACCESSORIES > TERMINAL

Paste in the command using ctr+shift+v

press return, when prompted for a password type the password you use to log on.

You will then be presented with a series of choices regarding your graphics set up. Choose the driver "vesa" and choose the relevant resolutions on the subsequent menus.

Once you have been through all of the setup you will return to the terminal. do:

```
exit
```

to close the terminal then go to SYSTEM>PREFERENCES>SCREEN RESOLUTION

Choose the resolution required.

---

### Post by Jdanniel on 2006-11-15
"sudo dpkg-reconfigure -phigh xserver-xorg"

Terminal is not accepting this code.  I am typing it manually because I'm using two different computers that are not connected.

When I type it manually, Terminal says something like BASH command not found.

---

### Post by jd65pl on 2006-11-15
> **Jdanniel said:**
> "sudo dpkg-reconfigure -phigh xserver-xorg"

Terminal is not accepting this code.  I am typing it manually because I'm using two different computers that are not connected.

When I type it manually, Terminal says something like BASH command not found.

Check for typing errors and case type. The command should work

---

