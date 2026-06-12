---
title: "Control+Alt+Backspace doesn't restart Gnome...?"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by bigcletus on 2005-06-27
When I use this key combo, it kills the X server and drops me to a login prompt.  How can I fix this so it restarts the X server like it should?  THanks.

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=bigcletus]When I use this key combo, it kills the X server and drops me to a login prompt.  How can I fix this so it restarts the X server like it should?  THanks.[/QUOTE]


That command kills the xserver than restarts it only sometimes. I don't know why its sometimes. When it doesn't work...type this command:

> startx

---

### Post by bigcletus on 2005-06-27
[QUOTE=poofyhairguy]That command kills the xserver than restarts it only sometimes. I don't know why its sometimes. When it doesn't work...type this command:[/QUOTE]

Thanks for the reply.  However, maybe the better question is how can I restart gdm when this happens?

---

### Post by rockmusic88 on 2005-06-27
> Thanks for the reply. However, maybe the better question is how can I restart gdm when this happens? 

It's startx

---

### Post by bluevoodoo1 on 2005-12-09
How can one make ctrl+alt+backspace restart the session rather than leaving me at the prompt? (I know I use "startx" at the prompt, but today, all of the sudden, I'm staring at a prompt, rather than a login)

---

### Post by codejunkie on 2005-12-09
[quote=bigcletus]Thanks for the reply.  However, maybe the better question is how can I restart gdm when this happens?[/quote]
to restart gdm you can use this command
```
sudo /etc/init.d/gdm restart
```
also i don't now if this works the same for everyone, but i've noticed that if i logout first. and then press ctrl+alt+backspace to reload the xserver it dosen't drop me to a terminal and kill gdm.

---

### Post by codejunkie on 2005-12-09
[quote=bluevoodoo1]How can one make ctrl+alt+backspace restart the session rather than leaving me at the prompt? (I know I use "startx" at the prompt, but today, all of the sudden, I'm staring at a prompt, rather than a login)[/quote] have you removed any packages recently or changed any runlevels/services, that can cause this can happen. the first thing i would check is if you've recently used bum in hoary or breezy, or the **[SIZE=2]Services administration tool[/SIZE]**[SIZE=2] in breezy, check and make sure that gdm is checked else it will not start at bootup. if gdm is still checked or not listed try reinstalling the gdm package in synaptic.[/SIZE]

---

### Post by bluevoodoo1 on 2005-12-09
[QUOTE=codejunkie]have you removed any packages recently or changed any runlevels/services, that can cause this can happen. the first thing i would check is if you've recently used bum in hoary or breezy, or the **[SIZE=2]Services administration tool[/SIZE]**[SIZE=2] in breezy, check and make sure that gdm is checked else it will not start at bootup. if gdm is still checked or not listed try reinstalling the gdm package in synaptic.[/SIZE][/QUOTE]

the gdm is there in the services and checked off. I have reinstalled gdm though Synaptic (where it asked for my install CD), but it did not solve the problem. It seems that I cannot restart or shutdown graphically anymore either. forced to use 'sudo shutdown -r now'

I don't know what 'bum' is, so I don't think I have used it.

Yesterday I had installed a new greeter theme, messed around the background color/image, and turned off the opening sound, could that have done something? Seemed harmless...

when I hit ctl-alt-backspace, if I want to restart gnome I get an error message (can't recall it), but only when i use 'startx' will the session return.

EDIT: this is the warning i receive when trying to start gnome-panel from the prompt...

(gnome-panel :8960): Gtk-WARNING **:cannot open display:

EDIT 2:
```
sudo /etc/init.d/gdm restart
```
works to bring me back to gnome... but how do I work around that so I don't have to type that everytime I want to restart gnome?

the restarting/shutting down still brings me to the prompt, and ctl+alt+F1 seems to be the same as ctl+alt+backspace

---

### Post by siorai on 2005-12-09
Have you tried actually restarting your computer? I was doing some stuff with OpenGL libraries last night and ran into the same problem. Hit ctrl-alt-backspace and it just dumped me to the console. Startx would jsut put me right back into Gnome without ever seeing gdm. So I did a shutdown -r now and everything was back to normal again.

---

### Post by bluevoodoo1 on 2005-12-09
[QUOTE=siorai]Have you tried actually restarting your computer? I was doing some stuff with OpenGL libraries last night and ran into the same problem. Hit ctrl-alt-backspace and it just dumped me to the console. Startx would jsut put me right back into Gnome without ever seeing gdm. So I did a shutdown -r now and everything was back to normal again.[/QUOTE]

yes are you are correct. I did a restart via System>Log out>restart and it restarted perfectly. I tried it a few times and it worked without a hitch. It seems that ctrl-alt-backspace kills gdm, without restarting it, so I'll have to steer clear of that for now... thanks!

i'm thinking this might have all started when i wrote 'gnome-panel killall' instead of 'killall gnome-panel'... after that it seems this started acting up. I dunno, I've only been using Linux/Ubuntu for about a month.

---

