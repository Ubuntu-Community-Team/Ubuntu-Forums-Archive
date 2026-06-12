---
title: "samba installed... what next?"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by guitarded on 2006-05-18
ok, i installed samba so i can access a windows machine.  i used synaptic.  i also installed the available clients.  how do i get to the client or a tool to use samba.  after the install, i did not notice anything in my menus to use as a tool.

---

### Post by slazh on 2006-05-18
Open nautilus (file browser) and type CTRL-L (it show's the location). 
There you can type smb://someIPadress

For example, if you want to browse to a PC with ip 10.0.0.1 type smb://10.0.0.1

---

### Post by guitarded on 2006-05-18
excellent! thank you!

---

### Post by user1397 on 2006-05-18
from the windows machine, go to start->run, and type in 
```
\\IPaddressofubuntucomputer\
```
or
```
//IPaddressofubuntucomputer/
```
(i forgot which one it is)

this lets you access your specified ubuntu shared folder

---

### Post by user1397 on 2006-05-18
[quote=slazh]Open nautilus (file browser) and type CTRL-L (it show's the location). 
There you can type smb://someIPadress

For example, if you want to browse to a PC with ip 10.0.0.1 type smb://10.0.0.1[/quote]
i hate how this never works for me and that i don't understand why!!!!!!:confused:

---

### Post by guitarded on 2006-05-18
actually under "Places"/"Network Servers" i can see my entire networks and access my shares.

---

### Post by user1397 on 2006-05-18
[quote=guitarded]actually under "Places"/"Network Servers" i can see my entire networks and access my shares.[/quote]
in the same place, i see "Windows Network", but there's nothing in it!

---

### Post by guitarded on 2006-05-18
i can see see my windows network and my one and only windows machine.  when i open my machine up i can see the folders that i set up as shares.

---

### Post by jn1167 on 2006-05-18
I have all working but when I try to browse the shares on my Windows XP comp, it asks for a password.  I use the admin pass but it doesnt let me browse the share.

I set up a share in ubuntu also and I get the same prob when I try to browse.  It asks for a pass.

Anyone know what Im doing wrong?

---

### Post by guitarded on 2006-05-18
on both linux and windows, right click the folder you want to share and check the share properties.  btw, you can drag you folder to the default share folder on your xp machine and this should allow you to see it from your linux box.

---

### Post by jn1167 on 2006-05-19
My linux box see the windows share and Im able to transfer files from the Windows to linux while Im on the linux box but when Im on the windows comp I can only see the linux comp.  Once I try to browse the linux share, it asks me for a password and I use the pass but it doesnt work.

Any I dea why?

---

