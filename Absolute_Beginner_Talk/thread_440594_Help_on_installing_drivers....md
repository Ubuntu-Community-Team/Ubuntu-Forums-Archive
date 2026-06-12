---
title: "Help on installing drivers..."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by phenomenon on 2007-05-11
Hey,

I've installed Ubuntu and am trying to install drivers for my wireless network card. I've found the drivers and downloaded them to the desktop, they are in a .tar.bz2 format but i don't know how to install them. 

Thanks in advance,
phenomenon

---

### Post by cymen on 2007-05-11
That's a compressed file, much like a zip file. You'll need to extract what's inside - try right clicking on them, and then selecting Extract Here. You should see some files come out, with any luck including further instructions to actually install them.

---

### Post by starcraft.man on 2007-05-11
You want to read and follow through either of these guides.

[Link!]("https://wiki.ubuntu.com/SetupNdiswrapperHowto")

And you may wanna read [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29") also before. 

I like Ubuntuguide.org but you should follow the official wiki first (the first link) :)

---

### Post by phenomenon on 2007-05-11
thanks, 

ive found a tutorial on how to install it via the terminal but when i install it i get a message saying that permission is denied. I am the only user on this system and i thought i was an administrator which meant i could do anything.

How do i gain the permission required to install applications etc.. ?

thanks in advance

---

### Post by cymen on 2007-05-11
The super user, or root user, has the power you're thinking of. You're not logged in automatically as that because of the potential for things to go wrong. ;) However, you can act as root easily enough in the terminal. Putting "sudo" before the commands that complain about permission should do the trick here.

Further reading: [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

