---
title: "Possible to install .bin and/or .run apps?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by benellard on 2007-05-18
The Linux driver for my Nvidia display comes in a file with a .run extension. Can this be installed? Similarly, Google earth for Linux comes with a .bin extension.  Ubuntu doesn't seem to recognize these files; am I doing something wrong or will these not work with Feisty 7.04. Any help?

---

### Post by dossjh on 2007-05-18
try:
```
./<filename>.bin
```

should also work for .run or any other executable file for that matter

---

### Post by benellard on 2007-05-18
Thanks for your response. Looks simple enough, but how do I get to a command line and how does the system know where the file is? Sorry to be so stupid, but this is a bit different from the DOS/Windows planet I come from.

---

### Post by Gen2ly on 2007-05-18
You could probably use a simple linux primer, as you'll be using it from time to time.  To open the terminal look in Accessories and you'll see it there.  Now you will likely need to changed directories "cd".  You start in you home folder.  List your files and folders with "ls".  Then "cd" into it.

---

### Post by jackmc on 2007-05-18
I think my .run file worked when I renamed it to .sh

---

### Post by benellard on 2007-05-19
After psyching out the syntax, I cd'd to Desktop and there were the two files. But when I tried to execute the files from the command line, I got the message "command not found." I assume that means the .bin and .run.  Also tried renaming .bin to .sh, but that evoked the same response from the system. 

I'm looking at a forum post from Nvidia that refers to items such as Xorg.7.x, make and gcc. How do I know if these are present?

Thanks for your patience.

---

### Post by Outrunner on 2007-05-19
[Where's the Terminal?]("http://www.psychocats.net/ubuntu/terminal")

[How to install ANYTHING in the Terminal!]("http://monkeyblog.org/ubuntu/installing/")

And also, here's an easier way to install your nvidia drivers:

```
sudo aptitude install nvidia-glx
```

And also, to enable the driver

```
sudo nvidia-xconfig
```

and then make sure you save any work you have open(like unsaved docs in OpenOffice) and press CTRL-ALT-BACKSPACE to restart the xserver.

---

### Post by benellard on 2007-05-19
Okay, did as suggested from the command line in terminal, then rebooted. Now I have a non-GUI error screen suggesting various Nvidia incompatibilities. But it does not suggest how six them or how to boot back up. I'm writing from a nearby XP machine. How do I revert to the earlier configuration which at least showed me a screen and allowed interaction?

---

### Post by Outrunner on 2007-05-19
hmmm... OK then, when you're at your linux machine, press CTRL+ALT+F2 and then type your username and passwd at the prompt. Then

```
sudo nano /etc/X11/xorg.conf
```

Notice the capital X in /X11/ , this is very important. Now, scroll down(using the down arrow) to a section that looks somewhat like this

Section "Device"
        Identifier      "NVIDIA Corporation NV40? [Unknown nVidia Card]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

now see the " Driver          "nvidia"" part? Well, you need to change "nvidia" to "nv" or "vesa", either should work. Now press CTRL+X , answer 'y' at the prompt and type startx to get to the GUI.

Unfortunately you're now at square one regarding the drivers... Hmm.

---

### Post by benellard on 2007-05-19
It worked. Curiously enough, when I used startx to launch the GUI, it came up in 1440x900, which worked beautifully. How did that happen? So I went to screen resolution preferences and clicked "make default" and then attempted to restart (to see if it would actually come back) by clicking on the icon at the top of the screen. The program froze, so I rebooted manually and now I  am back where I began with an 800x600 display and no idea of what to try next. 

Again, if I might ask about these items from the Nvidia support community: "If you wish to install Nvidia graphics driver on a system that ships with Xorg 7.x 9(what is that?), please ensure that your system meets the following requirements:

* development tools like make and gcc are installed (How do I check?)
* the linux-headers package matching the installed Linux kernel is installed (How do I check?)
* the nvidia-glx package has been installed with the purge option and the file /etc/int.d/invidia-glx does not exist. (Same as above)

...also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled.

Thanks for your patience so far. If this question is too long, you're forgiven for ignoring it and moving on.

---

