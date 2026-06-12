---
title: "Server 6.06: Completely clueless"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by nxmedia on 2007-08-31
I have never used Linix before in my life, and I need it for a game server for an online game I am making.

I chose Ubuntu as it's the best Linux version I could find that was free...

I'm using Ubuntu Server 6.06 LTS, as it's a server edition (seems the best for a server), and has long-term support.

It installed fine from the CD I downloaded from the website.

But, all I've got is a command line. I haven't got a clue what to type in to it to make it work. I know that there are files on the CD that you can install, such as Gnome desktop, but I am completely clueless on how to install them.

I tried doing a command I found on the Internet, that was something like:
sudo apt-get install -s ubuntu-standard ubuntu-desktop

This was supposed to install the desktop.

I tried "startx" and it simply said the command could not be found.



I know exactly what I have to do once I have gnome (or something like) installed, have the network set up, and have an Internet connection. But until then I am completely stuck.

Tried the on-disk manual, and couldn't make heads or tails of it.

Please help if you can...
Thanks,
~Daniel




**Edit:** The Internet also said I'd get a graphical login screen, which I don't get. I just get a command line asking for my username, then for my password, then logging me in.

---

### Post by Perfect Storm on 2007-08-31
Well the pefect server runs without interface or have a remote interface (via another computer ofcause).

But I suggest if you want Desktop on your server that you go for Xubuntu, because it uses very little resources.


Back to your problem if you still insist using Gnome;

sudo aptitude install xserver-xorg-video-all xserver-xorg-input-all ubuntu-desktop gdm
startx

---

### Post by nxmedia on 2007-08-31
Hmm... I could try Xubuntu. But... any idea on how to uninstall Ubuntu so I can do that?

---

### Post by Perfect Storm on 2007-08-31
Just insert the xubuntu CD and erease the existing partitions (if you have a windows partition on it then don't erease that ofcause).

---

### Post by nxmedia on 2007-08-31
Well, I've put the CD in and restarted, but it just loads Ubuntu off the hard drive. I have bios set up to load from the CD first then the hard drive if there's no CD, but still it's loading Ubuntu.

Is there something I need to do in Ubuntu to uninstall it?

---

### Post by Perfect Storm on 2007-08-31
Usually you need to hit F8 or DEL to get the option to choose where to boot from  (the key is diffrent fom system to system).

---

### Post by kerry_s on 2007-08-31
you guy's are going in circles.

the server cd is fine, with that you can install anything. here's the minimal instructions so you get only what you need.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

at the command line login
type> sudo apt-get update
sudo apt-get install x-window-system-core gdm synaptic icewm menu
reboot(ctrl+alt+delete)
select your session in the menu and login
use synaptic to install what ever else you want.

---

### Post by nxmedia on 2007-08-31
I'm going with Xubuntu anyway I think.

A problem: Xubuntu wont let me install. It comes up with a message like "creating partition failed" half way through installing.

I tried deleting the partitions already on there; that doesn't do anything. It still has the same problem.

Is there any way possibly of erasing the hard drive completely?

---

