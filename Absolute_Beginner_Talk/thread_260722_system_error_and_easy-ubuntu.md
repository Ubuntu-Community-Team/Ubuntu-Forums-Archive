---
title: "system error and easy-ubuntu"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by maneesh77 on 2006-09-19
I just installed easy-ubuntu it doesn't work so I thought of uninstalling it and reinstalling it, I couldn't uninstall it through the synaptic package manager and whenn i ran a check following system errors were also shown, How do I eliminate them and remove the software??

W: Duplicate sources.list entry [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)

since I don't know much about ubuntu , please if you can,give  a step by step guide


thanks from a newbie

---

### Post by deadgobby on 2006-09-19
You may have to edit your sources list to correct the error. Open up the terminal and copy and paste the following one at a time

[COLOR="Blue"]sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup[/COLOR]

[COLOR="Blue"]gksudo gedit /etc/apt/sources.list[/COLOR]

[COLOR="Black"]Look for the dublicate can edit it out. If you do not feel confy about it. Just copy and paste you source list and do not save when you exit out.[/COLOR]

---

