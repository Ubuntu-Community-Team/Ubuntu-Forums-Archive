---
title: "[SOLVED] Running a command as root"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-10-24
I have a program, called avidownload, that someone else wrote to download videos from a CVS one-time use camcorder.  Because it uses calls to libusb, it has to run as root.  From a command line I can "sudo" it, but how do I create a launcher to run this as root from a normal user account?  I tried putting sudo avidownload in the launcher, but it bombs out because it wants the super user password (that's what I'm guessing anyway, as it opens a terminal window and closes it super fast).

Ideally, I would like to put something in the code (I have the source) that would go super user only for the libusb calls, and leave everything else in the users' normal access.

Any help would be greatly appreciated!!:)

---

### Post by realvz on 2007-10-24
gksu

---

### Post by aysiu on 2007-10-24
You shouldn't be using *sudo* for graphical applicatiosn anyway. ```
gksudo avidownload
``` should do the trick.

---

### Post by anewguy on 2007-10-24
> **aysiu said:**
> You shouldn't be using *sudo* for graphical applicatiosn anyway. ```
gksudo avidownload
``` should do the trick.

Well, it's not graphical - I'm just tired of opening a terminal window and typing in sudo avidownload.  It is purely a text based line-by-line application.

I'll give gksudo a try!

Thanks!:)

EDIT:  gksudo did no good either - it prompts for the su password, but still nothing happens beyond that.  I can do this all in a terminal window with sudo avidownload.  I was really hoping there was a way to it from the desktop.  The launcher is defined with the terminal window type of application.

---

### Post by aysiu on 2007-10-24
I think there's a way to have a launcher launch a terminal command in the terminal. Let me poke around and see...

---

### Post by aysiu on 2007-10-24
Okay.

Right-click on the panel.

Select **Add to Panel**.

Click on **Custom Application Launcher**

Under the *Type* drop-down menu, select **Application in Terminal**
Under *Command*, type ```
sudo avidownload
```

---

### Post by Rui Pais on 2007-10-24
> **anewguy said:**
> 

EDIT:  gksudo did no good either - it prompts for the su password, but still nothing happens beyond that.  I can do this all in a terminal window with sudo avidownload.  I was really hoping there was a way to it from the desktop.  The launcher is defined with the terminal window type of application.

Hi, 
you must set your appt with visudo to run with administrative powers:
```
sudo visudo
```

and then add:
```
*yourusernamehere* ALL=NOPASSWD: /path/to/avidownload
```
save, exit and login again.
Try then from console if it runs ok.

---

### Post by anewguy on 2007-10-24
I don't mean to sound stupid :), but since I just have a command (the program is loaded in /usr/bin) how do I do the above?  I'm not really following......

---

### Post by anewguy on 2007-10-25
Okay, this was a little deeper than what you might expect.  I checked the /etc/udev/rules.d/40-permissions.rules (?) file and found that USB devices are mounted with a default mode of 0664.  While I know it opens things up, I changed that to 0666 and everything works great!:)

---

### Post by Rui Pais on 2007-10-25
> **anewguy said:**
> I don't mean to sound stupid :), but since I just have a command (the program is loaded in /usr/bin) how do I do the above?  I'm not really following......

hi, 
i assume by "above" you mean my suggestion :)
Nothing special, it's just a way to define to your system commands that user can launch with administrative powers, without need for password. In your case, saying your username would be anewguy, then if you run
```
sudo visudo
``` from a terminal and add a line on the opened file like thid:
```
anewguy ALL=NOPASSWD: /usr/bin/avidownload
```
(changing anewguy for your username on your computer)
you can then run from terminal 'sudo avidownload' or click a launcher with that command and it should run without ask you the password.

---

### Post by Rui Pais on 2007-10-25
> **anewguy said:**
> Okay, this was a little deeper than what you might expect.  I checked the /etc/udev/rules.d/40-permissions.rules (?) file and found that USB devices are mounted with a default mode of 0664.  While I know it opens things up, I changed that to 0666 and everything works great!:)

sorry, i didn't see that post of yours while i'm typing mine...

are you sure it's a sensate thing change used rules? i don't know, but an update can put back that to the original form?... again just ask, not sure about udev rules or how to change them securely...

---

### Post by eldepeche on 2007-10-25
> **anewguy said:**
> Okay, this was a little deeper than what you might expect.  I checked the /etc/udev/rules.d/40-permissions.rules (?) file and found that USB devices are mounted with a default mode of 0664.  While I know it opens things up, I changed that to 0666 and everything works great!:)

Can't you just add yourself to the "usb" group? Giving specific access to specific users is kind of the point of Unix-style permissions.

Although I guess I'm just a hardass about that, since I made a special group to get access to my second HDD which contains movies and music, on my desktop that only I ever use.

---

