---
title: "Computer Diagnistic programs for Ubuntu"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-11-13
Can anyone advise if there are programs for Ubuntu similar to windows EverestHome and Belarc etc that give descriptions of your computer hardware and software installed.

---

### Post by wirelessmonkey on 2006-11-13
gnome and KDE have applications that do exactly this.  I don't know the gnome app names, but in KDE under the system option in the K menu there are System Monitor, Hardware Database, Package Management (software list), Time management, and the KinfoCenter... all of which do pretty much what you're describing.

---

### Post by argie on 2006-11-13
On Gnome, Synaptic is nice to browse all the packages, and Device Manager works fine to display all hardware.

Both are in System > Administration >

---

### Post by Marsolin on 2006-11-13
KInfoCenter is the program in KDE that has hardware information. [Device Manager]("http://linuxappfinder.com/package/hal-device-manager") is an option as well.

[Adept]("http://linuxappfinder.com/package/adept") in Kubuntu and [Synaptic]("http://linuxappfinder.com/package/synaptic") in Ubuntu can list the installed software.

---

### Post by steve.horsley on 2006-11-13
Try this in a command line:
1) prime sudo so it won't ask for a password in the next command...
**sudo ls**
2) View list of hardware (use 'q' to quit)
**sudo lshw | less**
3) output that hardware list to a file if you like:
**sudo lshw > hardware.txt**

I think lshw stands for list hardware.

---

### Post by Gerry Atric on 2006-11-13
Thanks all for the help much appreciated

---

