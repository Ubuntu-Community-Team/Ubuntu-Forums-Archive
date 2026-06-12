---
title: "how to install k3b or kde software on gnoe?"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by shifan on 2006-10-22
hi guys its me again. i wanna know is thare a way to install k3b on gnome? im using 5.10. the cd creater is giving me trouble. it says to insert an empty cd even when do put an empty cd. couldnt burn any thing. so thats why im thinking of installing k3b. i got the deb for it but when i "dpkg -i" it gives me error. i have heard that some softwares are designed for specific desktops. so i need to know what else i should do to get k3b installed and running? thanks.:)

---

### Post by d3v1ant_0n3 on 2006-10-22
If you're running gnome, you'll need lots of KDE libraries for running KDE software.

I *think* the best way of doing it would be to install using the terminal using aptitude:

Open a terminal and type 'sudo aptitude install k3b'

This *should* install k3b and it's dependencies.

I might be wrong tho'.

---

### Post by Delkster on 2006-10-22
Yes, K3b is available in the repositories (and in Add/Remove Applications), so if you want it, you should install it from there.

---

### Post by insub2 on 2006-10-22
i got k3d installed using synaptic.  search for it, mark for install, it will select the other things you need, click apply, wait for it...and you're set.

easy.

---

### Post by shifan on 2006-10-24
:-D thanks for your suggestions but the thing is i dont have any internet. i downloaded an add on cd for breezy it dont contain that things. so i m hoping if you could help me do it off line.

---

### Post by insub2 on 2006-10-29
oooo.  i don't think i could do linux offline.

i am not sure exactly how to do this, but what you need to do is go somewhere with access and download a .tar.bz2 file for kd3 (check here: [http://www.k3b.org/]("http://www.k3b.org/")) and put it on a disk.  bring that disk home and install is manually (see this page for instructions [http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually]("http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually"))

i hope that helps.

---

### Post by Bachstelze on 2006-10-29
shifan > download a Kubuntu CD from somewhere and install k3b with it :)

---

