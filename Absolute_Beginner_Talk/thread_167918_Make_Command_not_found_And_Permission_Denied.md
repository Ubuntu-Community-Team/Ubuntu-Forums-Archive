---
title: "Make: Command not found? And Permission Denied?"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-04-29
I tried to compile circle MUD and it tells me;
>  bash: make: command not found

 I also want to install avast!Linux Home Edition. But I get this happen when trying to integrate it with the desktop;

>  raavea@Bernard:~/Desktop/avast4workstation-1.0.5$ ./lib/avast4workstation/share/ avast/desktop/install-desktop-entries.sh install
ln: creating symbolic link `/usr/share/applications/avast.desktop' to `/home/raa vea/Desktop/avast4workstation-1.0.5/lib/avast4workstation/share/avast/desktop/av ast.desktop': Permission denied
ln: creating symbolic link `/usr/share/icons/hicolor/48x48/apps/avastgui.png' to  `/home/raavea/Desktop/avast4workstation-1.0.5/lib/avast4workstation/share/avast /desktop/../icons/avast-appicon.png': Permission denied
ln: creating symbolic link `/usr/share/icons/gnome/48x48/apps/avastgui.png' to ` /home/raavea/Desktop/avast4workstation-1.0.5/lib/avast4workstation/share/avast/d esktop/../icons/avast-appicon.png': Permission denied
ln: creating symbolic link `/usr/share/pixmaps/avastgui.png' to `/home/raavea/De sktop/avast4workstation-1.0.5/lib/avast4workstation/share/avast/desktop/../icons /avast-appicon.png': Permission denied
ln: creating symbolic link `/usr/share/icons/avastgui.png' to `/home/raavea/Desk top/avast4workstation-1.0.5/lib/avast4workstation/share/avast/desktop/../icons/a vast-appicon.png': Permission denied

 Can anyone help? I am totally new to this, so please talk to me like I am four. T___T

---

### Post by bluevoodoo1 on 2006-04-29
[QUOTE=Raavea]I tried to compile circle MUD and it tells me; "bash: make: command not found"
[/QUOTE]

try getting build-essential


```
sudo apt-get install build-essential
```

---

### Post by Kimm on 2006-04-29
For the make issue:

type this in terminal:
sudo apt-get install build-essential

*Edit: To slow...*

for the other thing, run the script as root, e.g:
sudo ./lib/avast4workstation/share/ avast/desktop/install-desktop-entries.sh install

---

### Post by Bloch on 2006-04-29
Raavea; 
You don't need anti-virus software for linux, at least not for a home computer. I presume you are a beginner. A beginner shouldn't be trying to compile software - that is what you are doing with make. It didn't work because ubuntu is intended chiefly for the non-technical user and so the packages for programmers are not installed by default.

Read up some information. Almost all the software you need can be installed using synaptic - or first check out what's on the menu in 
Applications --> Add Applications

A newbie should read a little about these three things:
1. Synaptic and the repositories of software
2. A bit about the termminal (also called the command line, CLI or bash shell)
3. easyubuntu - it installs the non-free codecs to play mp3s, mpegs, dvd,s etc etc.

Here's the general ubuntu help page. There is so much information that a beginner can fall down a hole learning tons of obscure stuff. Try to grasp the basics of the three above and you'll be on your way. Check out the first link below - it's very helpful

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

### Post by Raavea on 2006-04-29
For some reason, Bloch, I find your post insulting. I know you were only trying to help but... o.O *shrugs* Anyhow...

 I don't believe that just because an OS is more inhosiptable to viruses that I should not protect myself as much as I can. What if I do get nasty infectious bit of malware that I could have protected against, and it spreads to your PC? I design websites and browser-based mmorpgs - I need my system to be as safe and secure as possible. Another thing is: My computer is the head of my home network - the other two computers are both on XP and I should like to be sure they don't spread something to me, or visa versa.

 I learn only by doing things - it has made my life awkward. Now, I'm learning a new OS, to get away from the evil alien overlord. I am trying to further my enjoyment of various programming languages I've dabbled in, by fiddling with game code etc. I've already installed many things onto this system, and I have glanced over the tutorials. However, until I do these things, they do not stay in my memory.

 Thanks for all the help, and I already have those pages bookmarked, except EasyUbuntu, since I don't want that sort of stuff. I thought that the build kit and the sudo command were what to go for, but I'd hate to poke something and 'break' the system, and I thought I'd already added the build kit. Silly me. Goodness help anyone who relies on me to remember things!

---

