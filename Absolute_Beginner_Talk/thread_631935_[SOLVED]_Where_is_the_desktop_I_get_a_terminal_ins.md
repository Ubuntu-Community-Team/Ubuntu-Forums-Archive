---
title: "[SOLVED] Where is the desktop? I get a terminal instead!"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by agerfe on 2007-12-04
Hi! I just installed Ubuntu Studio 7.10. The installation went smoothly. I was very careful and make sure everything was installed. However, when I boot Ubuntu it takes me to the gnome terminal. 

Where's the desktop?

I'm positive it was installed because I selected it from the list, pressed enter and watched it get installed.

I know nothing of terminal commands. I'm all new to Linux.

I'll appreciate any help.

agerfe

---

### Post by Daveth on 2007-12-04
I think it may need re-loading.
Try

```
sudo /etc/init.d/gdm restart
```

---

### Post by markharding557 on 2007-12-04
when on the commandline startx may start the gui

---

### Post by agerfe on 2007-12-04
Instead of booting to the desktop Ubuntu boots to the gnome terminal! What's wrong?

I've just installed Ubuntu Studio 7.10 and I'm sure the installation was successful except it couldn't download the security update. However I don't think this has anything to do with my problem.

I was under the impression that after the installation my PC would reboot and that the GUI would appear. Instead Ubuntu asks me for my user name and password and takes me to the terminal.

What do I do now?

I'd appreciate any help.

agerfe

---

### Post by agerfe on 2007-12-04
I apologize for reposting but I'm desperate!

Instead of booting to the desktop Ubuntu boots to the gnome terminal! What's wrong? :confused:

I've just installed Ubuntu Studio 7.10 and I'm sure the installation was successful except it couldn't download the security update. However I don't think this has anything to do with my problem.

I was under the impression that after the installation my PC would reboot and that the GUI would appear. Instead Ubuntu asks me for my user name and password and takes me to the terminal.

What do I do now?

I'd appreciate any help.

agerfe

---

### Post by LaRoza on 2007-12-04
What happens if you type "startx"?

---

### Post by agerfe on 2007-12-04
It says startx is not installed and suggests a command line to install it but I'm hesitant to do it cause I don't know what this is! :confused:

---

### Post by LaRoza on 2007-12-04
> **agerfe said:**
> It says startx is not installed and suggests a command line to install it but I'm hesitant to do it cause I don't know what this is! :confused:

Did you install with a GUI? 

```

sudo aptitude install ubuntu-desktop

```

It may take a while....

---

### Post by Paqman on 2007-12-04
The command startx starts the x-windows system, btw, which is what gives Linux (and some other OSes) it's GUI. On top of that you have different desktop environments like Gnome or KDE.

---

### Post by agerfe on 2007-12-04
Not sure if I understand you but if you are asking if I installed a desktop the answer is yes. I did choose to install the desktop and remember the installer doing it.

What should I do with that command line? Should I type it at the terminal?

---

### Post by LaRoza on 2007-12-04
Before doing that, do you get any errors before the login prompt?

---

### Post by agerfe on 2007-12-04
No. The are no error messages....... not that I can see, at least.

---

### Post by LaRoza on 2007-12-05
Try running the command, I never used Ubuntu Studio, so maybe it didn't install the desktop.

---

### Post by agerfe on 2007-12-05
Thank you! I'll try it and post the results. (crossing fingers)

---

### Post by agerfe on 2007-12-05
Yes! It worked..... although I had to change "ubuntu" for "ubuntustudio" (just followed a hunch)

Apparently the installer had only installed the kernel and nothing more.

However, now I face a second problem. I chose ubuntustudio because it comes with a plethora of graphics & multimedia applications..... and none of them has been installed.

How do I do this?

Any ideas?

---

### Post by oeolycus on 2007-12-05
Login with your username and password and try:

```
sudo dpkg-reconfigure xserver-xorg
```

That will setup xorg for you, and then you can try:

```
sudo /etc/init.d/gdm start
```

I don't know much about UbuntuStudio, but this is what I would do in vanilla 'buntu.

EDIT: Ignore my post...there was some massive delay in its posting and I missed all of the conversation between the OP and mine.

---

### Post by Paqman on 2007-12-05
> **agerfe said:**
> 
However, now I face a second problem. I chose ubuntustudio because it comes with a plethora of graphics & multimedia applications..... and none of them has been installed.

How do I do this?

Any ideas?

I don't know much about Ubuntustudio, is all their extra gubbins in the normal Ubuntu repos, or do they have their own? Either way, if you know what packages you want, Synaptic should be able to sort you out.

---

### Post by fenian on 2007-12-05
Try this open a terminal and enter...
> 
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-menu ubuntustdudio-video ubuntustudio-default-settings ubuntustudio-launcher 

---

### Post by agerfe on 2007-12-05
Finally! That did it! Thank you!

I had to type each command separately tho, but it worked. The only command that didn't work was the one for the launcher. It said it no such package could be found. Maybe ubuntustudio has no launcher. Don't know what this is anyway. :)

Thanks to all of you guys!

---

### Post by agerfe on 2007-12-05
Just one more thing...... apparently the cause was that the installer installed only the kernel but can't figure out why. I'm absolutely sure I selected each package to be installed. Don't know what I did wrong!

---

