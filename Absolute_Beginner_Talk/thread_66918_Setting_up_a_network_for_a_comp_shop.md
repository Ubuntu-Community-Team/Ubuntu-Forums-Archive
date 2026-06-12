---
title: "Setting up a network for a comp shop"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by energeist on 2005-09-18
ok i have change all my computers to UBUNTU LINUX,
now the problem is how can i create a network so that
all computers have a certain workgroup like in windows.
can anyone teach me the step by step process.

---

### Post by jeffreyvergara.NET on 2005-09-18
[QUOTE=energeist]ok i have change all my computers to UBUNTU LINUX,
now the problem is how can i create a network so that
all computers have a certain workgroup like in windows.
can anyone teach me the step by step process.[/QUOTE]
 I would like to learn this also. like Setting up the server

---

### Post by skirkpatrick on 2005-09-18
Why do they need to be in a workgroup?

---

### Post by jeffreyvergara.NET on 2005-09-19
[QUOTE=skirkpatrick]Why do they need to be in a workgroup?[/QUOTE]
 i think to separate the gaming pc to the Internet/Browsing only Pc... imo

---

### Post by oragon on 2005-09-19
im newbie to ubuntu, heres some ideas... setup your local network with none-routable ip, point to your IP gateway in order to browse internet, to set up workgroup-like network, like in Micro$oft install your ubuntu with NFS or SMB. this allows you to have "file-n-print" sharing. with gaming, you can run Window$-ba$ed games on ubuntu, just install cedega *free* emulator to run games.

---

### Post by skirkpatrick on 2005-09-19
Ok, if by "workgroup like in windows" you mean be able to share files, then you need to setup Samba.

The easy way is to go into System->Administration->Synaptic Package Manager and search for samba and smbfs and install both of those.  You'll want to edit the Samba configuration file to name your workgroup by using "sudo gedit /etc/samba/smb.conf" from a terminal and looking for and changing the line for Workgroup.  To get Ubuntu to start using the new workgroup name, execute "sudo /etc/init.d/samba restart" from the terminal.  You should now be able to share directories by going to System->Administration->Shared folders and access other computers shared directories by going to Places->Network Servers and browsing them just like you did in Windows.  If you want to make a shared directory from another computer permanent, you can right-click on the directory and select Connect To This Server.

---

### Post by aragorn2909 on 2005-09-19
If your network will consist of nothing but Ubuntu boxes, might I suggest NFS.  Easy setup/configuration, with a very easy howto [here](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#INTRO) .  This is what I use for my home network.

---

### Post by skirkpatrick on 2005-09-19
True, if it's a pure Linux network, you'll probably be better off with NFS.  I currently have Samba and NFS setup here at home because of a mix of Linux and Windows.

---

### Post by wabble on 2005-10-10
[QUOTE=aragorn2909]If your network will consist of nothing but Ubuntu boxes, might I suggest NFS.  Easy setup/configuration, with a very easy howto [here](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#INTRO) .  This is what I use for my home network.[/QUOTE]

Well.. This helped me out, thanks ;)

---

