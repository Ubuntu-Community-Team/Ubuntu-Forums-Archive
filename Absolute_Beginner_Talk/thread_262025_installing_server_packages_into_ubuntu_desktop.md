---
title: "installing server packages into ubuntu desktop"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Th3N@tive on 2006-09-21
ok i got told this is possible but how can i do it and what upgrades must i install in order to have it act as a fully functional server

---

### Post by benfindlay on 2006-09-21
It depends what you want to do with your server. For all intents and purposes the server and desktop are the same OS, except for a few things (desktop has X ane gnome/kde/xubuntu etc installed, and server has things like apache/ftp etc installed).

If you want various programs installed just bring up the terminal and type ```
sudo aptitude install [program name]
```

So say for example you want to install samba server, just type ```
sudo aptitude install samba
```

A quick note: If you dont know the exact name of a package, type the first few letters in and press the tab key and it will display a list of packages that match what you have typed so far

So for samba we type: ```
sudo aptitude install sam
```
Now press```
TAB
```

You will get a list with something like the following :
> samba
samba-common
samba-dbg
samba-doc
damba-doc-pdf
not at my pc now, so doubt this list will be fully correct, but I hope it gives you a good idea of what to expect

So you just pick the one you want, "samba" in this case. And it will deal with all dependencies automatically! :D

You will then of course need to configure the programs you install, but there are plenty of guides in the How-to section of this site!

HTH

---

### Post by Th3N@tive on 2006-09-21
what about using synaptic package manager can i do it that way?

---

### Post by benfindlay on 2006-09-21
You CAN, but you will still need to edit the config files for things like user access, workgroup names etc. Essentially customising to your system is done via terminal and .conf files. There are various programs out there which allow you to edit things via a GUI, but you have a much more reliable system if you do it via CLI. You also have the added advantage of knowing EXACTLY what changes are being made if you do it manually.

Trust me, just follow one of the numerous How-Tos on this site and you can't go wrong!

HTH

---

