---
title: "Minimal Xubuntu install from .iso"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by IainT on 2006-05-12
A while ago I tried to install Ubuntu on an old laptop with no internet connection. Didn't work for ages until I found that my motherboard has a conflict with apmd, so I did a server install and then sudo apt-get'd minimal gnome packages to get a useable GUI.

It worked, but the computer just is too weak for Gnome. Finally decided to try Xubuntu now I find that there is a beta Drake Xubuntu .iso available.

Question is - what do I need to sudo-apt get to install a minimal XFCE GUI and so avoid conflicts when the normal install tries to install apmd?

Thanks in advance for any answers.

For reference - machine is a 433mhz Celeron, 96mb RAM. If you think that Xubuntu will still be too heavy for it let me know.

---

### Post by aysiu on 2006-05-12
[QUOTE=IainT]
Question is - what do I need to sudo-apt get to install a minimal XFCE GUI and so avoid conflicts when the normal install tries to install apmd?[/QUOTE] I don't know what APMD is, but you can try this: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by IainT on 2006-05-12
If I just install the Xubuntu-desktop package I assume it will install this apmd program - [http://www.worldvisions.ca/~apenwarr/apmd/](http://www.worldvisions.ca/~apenwarr/apmd/) - and that will conflict with my motherboard.

I need to install from the server prompt the minimal packages to make XFCE useable but I can't use repositories because I have no internet connection. I assume that this is possible from the Xubuntu .iso

---

### Post by aysiu on 2006-05-12
You can't burn the .ISO to a disk?

I suppose you could mount the .ISO and then add it as a CD-ROM source. ```
apt-cdrom add
``` is the command, I think. I forget the command for mounting .ISO files.

If you're doing a Breezy server install, you would have to mount the .ISO, add it as a source, comment out all the other sources in your /etc/apt/sources.list, do an update and dist-upgrade, then install *xubuntu-desktop*, then remove *apmd*.

---

### Post by IainT on 2006-05-12
I have an .iso to burn, and I'm starting with an entirely blank drive.

Planned steps are:

1. Do server install
2. Install minimal XFCE packages to get useable GUI*
3. Expand from there as necessary

This needs to be done without an internet connection

* for instance, to do this with GNOME I did the following

sudo apt-get install x-window-system-core gnome-session gnome-applets nautilus metacity xscreensaver gdm gedit gnome-terminal

Some of that was probably unnecessary, but I got a useable GUI and could then install further packages. II hope I am clear now.

---

### Post by aysiu on 2006-05-12
You don't need a usable GUI. Just do ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
sudo apt-get remove apmd
``` Otherwise, this is a far lighter usable desktop: ```
sudo apt-get install x-window-system-core xterm gdm icewm menu firefox synaptic
```

---

### Post by IainT on 2006-05-13
Will your first suggestion install apmd and then remove it? The problem with Ubuntu was the install was failing as it was trying to install apmd, there is a known issue with this motherboard and apmd.

The second option - is IceWM on the Xubuntu install cd?

Thanks for your help.

---

### Post by aysiu on 2006-05-13
[QUOTE=IainT]Will your first suggestion install apmd and then remove it? The problem with Ubuntu was the install was failing as it was trying to install apmd, there is a known issue with this motherboard and apmd.[/quote] Okay, so not even *using* APMD--just *installing* it is the problem.

> 
The second option - is IceWM on the Xubuntu install cd?

Thanks for your help. Hm. It's probably not. 

Okay, so you have the Xubuntu install CD but no internet connection, right?

I wrote a script just for you--it installs *every* Xubuntu package *except* apmd.

Here's what you do.

Do a server install.

When you get to the prompt, log in, and type ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
``` Comment out every source except the first one (the CD-ROM repository). To "comment out" a line, you just put a # in front of it. So, after you're done, the only line that should *not* have a # in front of it is the CD-ROM source line.

Save (Control-X), confirm (Y), and exit (Enter).

Then type ```
wget -c http://www.psychocats.net/ubuntu/xubuntunoapmd.sh
chmod +x xubuntunoapmd.sh
./xubuntunoapmd.sh
``` The script will install every Xubuntu package except apmd.

---

### Post by IainT on 2006-05-16
I'm late to respond to this.

Thanks for your help, really appreciated. Right now I'm struggling to even install the server option, I knew the cd drive was a bit dodgy but it seems to have finally given up the ghost.

Again, thanks.

---

