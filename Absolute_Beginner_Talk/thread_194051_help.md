---
title: "help"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Andenium on 2006-06-10
ok so i have a few questions
1 is there like a task manager where i can close non responding tasks??
2 is there some way i can up the resolution on the desktop????

im using ubuntu

---

### Post by aysiu on 2006-06-10
Are you using Kubuntu or Ubuntu?

---

### Post by Andenium on 2006-06-10
ubuntu -.-!

---

### Post by aysiu on 2006-06-10
I don't know if there's a keyboard shortcut for this (you can create one), but press Alt-F2 and type ```
gnome-system-monitor
``` and you've got your task manager.

For screen resolution issues, go [here](http://ubuntuforums.org/showpost.php?p=129379&postcount=21).

---

### Post by grsing on 2006-06-10
2. Hopefully, just System-Preferences-Screen Resolution.  If your desired resolution isn't listed there, post back and we'll see what can be done to fix it.

---

### Post by Andenium on 2006-06-10
ok so i went there and it said some stuff about xorg so what is that?

---

### Post by aysiu on 2006-06-10
The /etc/X11/xorg.conf file controls your display properties. It's a text file that you can modify to adjust for your video card and monitor.

Can we assume that grsing's proposal didn't suit your needs? That would, of course, be the first thing you try.

---

### Post by Andenium on 2006-06-10
yes u asume right but i still dont know how to do it :S

---

### Post by aysiu on 2006-06-10
[QUOTE=Andenium]yes u asume right but i still dont know how to do it :S[/QUOTE] Well, as you can see from that link, there are various approaches, depending on what hardware you have. We'll start with the most simple.

First, log out of Gnome and press Control-Alt-F1.
You'll see a black screen with white text.
Log in.
Then, you'll get a prompt that say ```
andenium@ubuntu:~$
``` This is where you type commands.

The first command to try is ```
sudo dpkg-reconfigure xserver-xorg
``` This will give you a little text-mode "wizard" to answer questions about your video card and monitor.

If you don't know the answer to a particular question, just go with the default and press Enter.

When you're done, press Control-Alt-F7 and then Control-Alt-Backspace. Log in again, and see if you can change the screen resolution to be higher.

---

