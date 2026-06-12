---
title: "Wireless networking questions"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by TheAnonymousx on 2005-12-25
Hey guys, I'm using Xfce as my window manager and I'm wondering if there is a way to determine WHICH wireless network I'm currently on or to show which ones are readily available.
Thankx folks.

---

### Post by noob_Lance on 2005-12-25
Hey, there is... sadly.. I dont remember what program it is that u need x_x

---

### Post by ubuntuuser on 2005-12-25
You can type ```
iwlist wlan0 scanning
``` to scan for available networks. Just replace wlan0 with the correct adapter.
When you type ```
iwgetid
``` you get the ESSID of the network you are currently on.

---

### Post by TheAnonymousx on 2005-12-25
[QUOTE=ubuntuuser]You can type ```
iwlist wlan0 scanning
``` to scan for available networks. Just replace wlan0 with the correct adapter.
When you type ```
iwgetid
``` you get the ESSID of the network you are currently on.[/QUOTE]

Kewl, iwgetid does show me which connection I am using, and that's kewl. But the first command gives me an error: eth0      Failed to read scan data : Operation not supported

Anything else I can try? Also, is there some way to determine WHICH wireless lan I'd like to connect to?

---

### Post by ubuntuuser on 2005-12-25
Enable your universe-repositories and install network-manager, that should do it.

---

### Post by TheAnonymousx on 2005-12-25
[QUOTE=ubuntuuser]Enable your universe-repositories and install network-manager, that should do it.[/QUOTE]

Pardon me for being stupid, but does that have a front-end I can interface with? I installed the package fine but can't find the thing to actually use it. (There's a thread on why I can't do "find" to readily).

---

### Post by ubuntuuser on 2005-12-25
I must admit I don't use this program but a lot of people here on the forum found it very useful.
[http://www.gnome.org/projects/NetworkManager/]("http://www.gnome.org/projects/NetworkManager/") will tell you more. What I can say is that there must be a programm called nm-aplett (be creative with the spelling of aplett, I don't know how it is spelled ;) ). That should give you a little system bar icon.

---

### Post by TheAnonymousx on 2005-12-25
Hmmm, so I've used Network manager for a bit here and I gotta say that it's doing something weird with my connection (read: making it unusable). So i've removed the package and am looking for another tool/program/util to browse the local connections in my area, choose a specific one, and monitor it.

---

### Post by Lambert on 2005-12-25
There are a couple others but not sure how well they work with xfce

netapplett is in the repositories
gtkwifi is a third part project you'll find here in the forums
wifiradar


Try the iwlist command like this instead to see if it works.

iwlist wlan0 scan

not all drivers support this command so you may get something saying not supported.

---

