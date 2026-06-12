---
title: "Networking (May seem very dim, bear with a confused newb)"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by Greyscalefox on 2005-08-29
How would I network a XP (shudders) home x86 computer to a kubuntu PPC?

With a 5 port hub. And cat 5's obviously.

  ](*,)  Been banging my head on the wall with this.

Can anyone explain how to setup samba.

(I prefer GUI, but can do command if you make it clear.)

---

### Post by npaladin2000 on 2005-08-29
You're right, you do seem dim. ;)  But that's OK, to admit one's dimness is the first step in overcoming it. :)  You'd be surprised at all the dim people around this forum who insist on remaining dim by refusing to see it ;)

Anyway, samba setup is a cinch.  It consists of 2 components: the samba client and samba server. You only need the server if you're sharing files that are on the Ubuntu box.  it's a good idea to install the client-end stuff no matter what. 

In Synaptic/Apt, the server is called simply "samba" so a "sudo apt-get install samba" will install it.  Then one can just go to the GNOME "System" Menu, Administration, Shared folders to configure what folders you're sharing on the machine. 

The client stuff is easy. it's called "smbclient" and is usually already installed.  Printers are installed through printer admin.  File shares are browsed by going into the Places menu, Network Servers.  On one of the remote shares, if you right-click and select "connect to server" it basically vfs-mounts the remote volume in the Places menu and the desktop.  It also puts them into some of the gnome load/save dialog boxes on the left-hand side (where all the physical volumes are) but not all of them (the app has to support gnome-vfs).

Incidentally it won't ACTUALLY connect permanently to the server. It only establishes the connection as needed, when you try to access something on that share.

Feel less dim yet? :)

---

