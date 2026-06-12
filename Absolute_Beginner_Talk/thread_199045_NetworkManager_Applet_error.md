---
title: "NetworkManager Applet error"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by babyboss on 2006-06-18
everytime I log in gnome with my account, i always get a error message "(error icon) The NetworkManager Applet could not find some required resources. It cannot continue." Has anyone experience this kind of problem before? I have been trying grep /var/log/(files) | less , however, haven't seen any relevent message yet.

---

### Post by u.b.u.n.t.u on 2006-06-18
Is this a new install or has it worked and then stopped working?

---

### Post by babyboss on 2006-06-18
this is a new install. I don't know if the new install has network manager or not. Immediately after new install, I do automatix. After that, the error message popped out. Actually, right now it's working. I apt-get remove network-manager, and then reinstall it again. It works. If in the future, a similar message pops out, and telling me a prograom can not find some required resource, what should I do to figure out what it needs, and what it lacks?

---

### Post by u.b.u.n.t.u on 2006-06-18
ubuntu is self contained for the most part, as an original install. Only after you start to add programs and customise it, will you need to to think about what software is installed.

The safest way is through synaptic. That way you can also uninstall.

"Immediately after new install, I do automatix."

Perhaps it is worthwhile seeing if a problem exists before doing that?

I don't know what this "Network Manager" program is that you are referring to.

The only thing I need to do to get on the internet is correctly set up:

System > Administration > Networking

---

### Post by woodsb02 on 2006-06-21
Run this:

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/

I found this here:

[https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/35662](https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/35662)

Goodluck!

---

