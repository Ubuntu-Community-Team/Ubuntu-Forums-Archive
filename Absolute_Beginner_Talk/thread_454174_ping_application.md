---
title: "ping application"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-05-25
i need suggestion for a software application.

i need some sort of a pinger application which can continuosly ping a server showing me a graphical display. something that can be kept running from the taskbar....

something like Nullsoft NetMon which i used in Win OS...

[IMG]http://stuff.techwhack.com/stuff/netmon.png[/IMG]

---

### Post by starcraft.man on 2007-05-25
Ummm, there is a ping application easily run via the terminal. Just open it up (Applications > Accessories > Terminal), and type in:

```
ping site
```

where "site" is replaced by the url, no HTTP in front just ubuntu.com or [www.ubuntu.com](www.ubuntu.com).

You can further customize how it pings with modifiers, to do so, type in:

```
man ping
```

and you can read up on them. :)

That should be it, I don't think there are any graphical ping apps, the terminal one does it fine.

---

### Post by Sushubh on 2007-05-25
umm... yeah i can run ping in the terminal but i was hoping to find some GUI version of pinger which can alert me if the pings to a particular server are getting dropped... :P

---

### Post by starcraft.man on 2007-05-25
> **Sushubh said:**
> umm... yeah i can run ping in the terminal but i was hoping to find some GUI version of pinger which can alert me if the pings to a particular server are getting dropped... :P

I believe that you can get it to make an audible beep when X happens by putting it in the command, like I said look at man ping to see the modifiers. I don't know of a gui ping programs. Look at linuxappfinder maybe they have one somewhere, I didn't see one though.

---

### Post by dbott67 on 2007-05-25
Gnome has a built-in suite of tools under **SYSTEM > ADMINISTRATION > NETWORK TOOLS** that may do what you want (see attached screenshot).

-Dave

---

### Post by starcraft.man on 2007-05-25
> **dbott67 said:**
> Gnome has a built-in suite of tools under **SYSTEM > ADMINISTRATION > NETWORK TOOLS** that may do what you want (see attached screenshot).

-Dave

Ah, right... I forgot about the built in network tools pinger. I always use the terminal >.>.

---

