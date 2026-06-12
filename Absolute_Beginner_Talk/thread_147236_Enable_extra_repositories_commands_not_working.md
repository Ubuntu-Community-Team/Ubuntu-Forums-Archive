---
title: "Enable extra repositories commands not working"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by phenix on 2006-03-19
I have been trying to enable some extra repositories, but for some reason the commands that I found on "http://www.psychocats.net/ubuntu/sources.php" have not been doing anything for me!!!

Enabling Extra Repositories
If you're using Ubuntu (Gnome):
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
/ubuntu/sources.php

any ideas?

---

### Post by az on 2006-03-19
Why not just use synaptic and point and click the new repositories in?

System- Administration- Synaptic - Configuration- Repositories.

---

### Post by TylerH on 2006-03-19
here's a good explanation for adding repositories

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by batholith on 2006-03-22
I'm not quite sure what you entered into your terminal, but it should have been:

$sudo cd /etc/apt/sources.list /etc/apt/sources.list_backup

-This provides a backup file just in case you really screw up...

The next command:

$sudo gedit /etc/apt/sources.list

you have an extra "/ubuntu/sources.php" attached on your post, drop that...

Also, rememeber after you cut and paste the new repository text, you must save the new "sources.list" file and do the following command (while connected to the internet).

$sudo apt-get update

Good luck

---

