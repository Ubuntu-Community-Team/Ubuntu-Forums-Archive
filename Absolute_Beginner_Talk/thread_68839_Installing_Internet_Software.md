---
title: "Installing Internet Software"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by mpr67 on 2005-09-24
How do you install software available on the internet? As an example Bitdefender offers an antivirus package for Linux. I have had no success in installing this program. I have tried "apt-get" and "wget" and nothing seems to work. I did actually download the .rpm file but can't seem to do anything with it. I was hoping that installing web software not in a repository would not be so difficult. Any help would be appreciated.

---

### Post by aysiu on 2005-09-24
There's actually [a .deb for BitDefender](http://download.bitdefender.com/linux/free/bitdefender-console/en/BitDefender-Console-Antivirus-7.1-3.linux-gcc3x.i586.deb). Download that to your desktop, then type in these commands ```
cd Desktop
sudo dpkg -i BitDefender-Console-Antivirus-7.1-3.linux-gcc3x.i586.deb
``` Always try to find a .deb for something (that's Ubuntu/Debian's native format), but if you have to do an .rpm, you can also ```
sudo alien -i BitDefender-Console-Antivirus-7.1-3.linux-gcc3x.i586.rpm
``` That's less than ideal, though.

I usually try this order:

1. Synaptic/apt-get
2. .deb
3. .rpm
4. .tar.gz

---

### Post by mpr67 on 2005-09-24
I tried the deb business and it appeared to work, but where did it install it?

---

### Post by aysiu on 2005-09-24
[QUOTE=mpr67]I tried the deb business and it appeared to work, but where did it install it?[/QUOTE] A whole bunch of different places. Try launching the "run" command and typing *bit*, then press tab to see what fills in.

---

### Post by mpr67 on 2005-09-24
This is absolutely no fun. Went into synaptic and bitdefender is listed as installed in the antivirus (system) folder, but I can't get a "shortcut" into any of the menu items (or even run the program for that matter). I have spent a whole day on this and have accomplished very little. This is the very reason people stick with Microsoft and Apple! I probably will also.

---

### Post by cwaldbieser on 2005-09-24
[QUOTE=mpr67]This is absolutely no fun. Went into synaptic and bitdefender is listed as installed in the antivirus (system) folder, but I can't get a "shortcut" into any of the menu items (or even run the program for that matter). I have spent a whole day on this and have accomplished very little. This is the very reason people stick with Microsoft and Apple! I probably will also.[/QUOTE]
Posting such a sentiment is not going to make others want to help you with your problems.  The key is to relax, take you time, and ask for help when you don't understand something.  If you think something ought to be easy, but it is taking you a long time to figure it out, it may just be that you are taking the wrong approach.

For example, the easiest way to add programs to your start menu with Ubuntu is to use the SMEG menu editor.  There is a whole forum devoted to SMEG here:
[http://ubuntuforums.org/showthread.php?t=38183](http://ubuntuforums.org/showthread.php?t=38183) 
and there are installation instructions in the beginner's guide here: [http://www.ubuntuguide.org/#menu-editor](http://www.ubuntuguide.org/#menu-editor) 

You can be sure that there are people who have the same kind of frustration with their Windows and Mac computers.  When something doesn't work the way you would expect, that doesn't mean that the solution is difficult.  Sometimes a simple change in perspective is all that is needed.

There was some reason you decided to try out Ubuntu.  Maybe you were just curious and wanted to give it a go.  The folks on this forum are happy to help you with whatever problems you may encounter along the way.  If you decide you would be more comfortable with a computer system you are more familiar with, that's OK, too.

---

### Post by aysiu on 2005-09-24
[QUOTE=mpr67]This is absolutely no fun. Went into synaptic and bitdefender is listed as installed in the antivirus (system) folder, but I can't get a "shortcut" into any of the menu items (or even run the program for that matter). I have spent a whole day on this and have accomplished very little. This is the very reason people stick with Microsoft and Apple! I probably will also.[/QUOTE] It would have taken you less time to create a shortcut to the application than to type this worthless message. I'm sorry I even bothered to help you out. Have fun sticking with whatever OS works for you. No one's twisting your arm to use Ubuntu.

---

### Post by Perfect Storm on 2005-09-25
[QUOTE=mpr67]This is absolutely no fun. Went into synaptic and bitdefender is listed as installed in the antivirus (system) folder, but I can't get a "shortcut" into any of the menu items (or even run the program for that matter). I have spent a whole day on this and have accomplished very little. This is the very reason people stick with Microsoft and Apple! I probably will also.[/QUOTE]

Relax...take a deep breath ;) It takes some times to get familiar with new stuff. Patience is a virtue ;)

Though a Linux OS do not need an Anti-virus program they can be a great tool for dual booting, servers and share network. Take a look at my thread here: [http://ubuntuforums.org/showthread.php?t=25421](http://ubuntuforums.org/showthread.php?t=25421) It also recommend a good anti-virus application.

Also take a look for HOWTOs: [http://ubuntuforums.org/showthread.php?t=53050](http://ubuntuforums.org/showthread.php?t=53050) and the unofficial ubuntu guide can help with some stuff: [http://ubuntuguide.org/](http://ubuntuguide.org/)


.:=The AI Dude=:.

---

