---
title: "Help required"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Minuteman on 2006-11-05
I'm a total noob to UB. How do install:
 Drivers for netgear WG311 
 Teamspeak
 GAIM

---

### Post by LLRNR on 2006-11-05
Hi ! You can find GAIM under Applications -> Internet -> Gaim Internet Messenger, it's already there after a clean install. In general, when you want to install something, you must open a terminal (you can do this by choosing Applications -> Accessories -> Terminal) and typing: ```
sudo apt-get install *packagename*
``` You issue sudo, so this means that you run the command following "sudo" as the root user, so it prompts you for the root password (you won't see echo on the screen, just type it and press enter).

Good luck! (I'm a n00b myself, so I don't know anything about the drivers you need and about Teamspeak... :) )

---

### Post by Minuteman on 2006-11-05
Thanks, but that still doesn't get me the internet.

---

### Post by apjone on 2006-11-05
have you checked your wirelss cards compatability with linux?

---

### Post by jpeddicord on 2006-11-05
The drivers *should* be there out of the box. Try going to System > Administration > Networking to configure your card.

---

### Post by bulldog on 2006-11-05
> **Minuteman said:**
> I'm a total noob to UB. How do install:
 Drivers for netgear WG311 
 Teamspeak
 GAIM
 Did you have internet connection on the live cd?

---

### Post by Minuteman on 2006-11-05
OK, here's what I've been able to ascertain: I have run iwconfig and, having set the ESSID, it appears to have connected, since it says that signal level=14/100. There just isn't any internet.

---

