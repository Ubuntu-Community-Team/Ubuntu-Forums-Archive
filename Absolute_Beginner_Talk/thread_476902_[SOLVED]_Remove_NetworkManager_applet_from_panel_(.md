---
title: "[SOLVED] Remove NetworkManager applet from panel (while keeping internet connection)"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-06-17
Hello,
The network manager applet is taking up valuable space on my applet. I would like to remove the applet from my sight, without removing whatever function that applet provides. I have wired internet on my desktop computer.

Is my desire possible?


Thanks!

---

### Post by Clay_Banger on 2007-06-17
exiting the network manager shouldn't have any effect on your network connection, as it only provides a graphical interface to other programs running. however it may be set to run on startup, so you may need to look through the options to see if it runs on startup, before closing it.

---

### Post by 5-HT on 2007-06-17
You can kill the applet with 'killall nm-applet'. It is set to autostart, so you should remove it or disable it from Systems -> Preferences -> Sessions as Clay_Banger mentioned. 
If you are only running a wired connection, networkmanager should default to that. Alternatively, do you really need to use networkmanager at all if you're only using a wired connection?

---

### Post by hanzj on 2007-06-17
5-HT:
NetworkManager _does_ default to wired connection.

Folks, I don't know why Network Manager starts automatically in the first place. I freshly installed Ubuntu 7.04 on my computer and that's what ubuntu decided to do.

---

### Post by 5-HT on 2007-06-17
> **hanzj said:**
> 
Folks, I don't know why Network Manager starts automatically in the first place. I freshly installed Ubuntu 7.04 on my computer and that's what ubuntu decided to do.

It's mostly intended for wireless users, especially notebook users who use multiple wireless networks depending on their current location. In that respect, it's a pretty sane default to use networkmanager and to have nm-applet automatically start. It's easy enough to prevent it from autostarting anyways. If you're just going to use a wired connection, doing away with networkmanager completely will save you from having to load an extra, unnecessary daemon (save some RAM and CPU cycles).

cheers,

---

### Post by hanzj on 2007-06-18
5-HT, ClayBanger.
Thanks for teaching how to remove applet. That's a few more pixel space freed up.

---

### Post by hanzj on 2007-06-18
> **5-HT said:**
>  If you're just going to use a wired connection, doing away with networkmanager completely will save you from having to load an extra, unnecessary daemon (save some RAM and CPU cycles).

Where can I make a suggestion for the Ubuntu Developers? I'd like to suggest that the computer either 
a) ask the user if he's on wired or wireless 
b) sense whether user is on wired

When the computer learns that the computer is on [ALWAYS] wired, it could remove applet from panel.

---

### Post by silverglade00 on 2007-06-18
Some people, like myself, have a laptop that is constantly moving between wired and wireless settings. I work in a university and take classes there as well. When at my job, I am able to use a wired connection if I am sitting in certain seats. When in class or not in one of those seats, I am on wireless. The tool is valuable for easily switching between the two with a simple click.

---

### Post by Clay_Banger on 2007-06-18
> **silverglade00 said:**
> Some people, like myself, have a laptop that is constantly moving between wired and wireless settings. I work in a university and take classes there as well. When at my job, I am able to use a wired connection if I am sitting in certain seats. When in class or not in one of those seats, I am on wireless. The tool is valuable for easily switching between the two with a simple click.
yeah, but what hanjz says above is correct, there is really no need for the applet to be there if there is only one network interface, however it is handy to refresh the network instead of restarting the comp.

---

### Post by hanzj on 2007-06-18
I made an edit in my previous post and added the word [always]. It will be nice if Ubuntu asks the user if he'll always be on a wired connection. Or maybe the computer can be smart and, after being on a wired connection for X days/weeks/months, computer could ask: "Dear User, it seems that you are always on wired connection. Would you like to save panel space and have me remove the NetworkManager applet?" or something like that.

---

### Post by Clay_Banger on 2007-06-18
cant you hide programs in the system tray in gnome? i know in kde any system tray program can be hidden automatically.
[IMG]http://img216.imageshack.us/img216/9316/desktopconfigure3ja7.jpg[/IMG]

[IMG]http://img140.imageshack.us/img140/5858/desktopconfigure4gz9.jpg[/IMG]

---

### Post by hanzj on 2007-07-05
Clay,
No. In gnome, you can't hide programs in the system tray.

---

### Post by coolen on 2007-07-05
I'd remove it, personlly. Network Manager is great for wireless connections: handles WPA, remembers network settings and keeps preferences, does automatic scanning...
Are any of these things useful for an ethernet connection? No. Cut it out.

---

