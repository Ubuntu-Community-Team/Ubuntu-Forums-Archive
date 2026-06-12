---
title: "Installing fluxbox: where are my programs?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by MikeMLP on 2006-08-20
Hi, I'm installing fluxbox following this tutorial: [https://help.ubuntu.com/community/Fluxbox]("https://help.ubuntu.com/community/Fluxbox")
and once I install the proper package, and then start a fluxbox session, when I right click the desktop to get my expanding menus, they don't seem to be there.  All I get is a single menu entry with the titlebar: fluxbox, and nothing underneath it.  Something seems to be missing.  Please help.

---

### Post by Kuraboy on 2006-08-20
there is a file in your home directory called .fluxbox

if you type 
ls -a

in a terminal you will se it in your home directory.

inside there is a file called menu open it and put there the programs you want it to list.

mine is something like this:
[begin] (Fluxbox-1.0rc2)
      [exec] (aterm) {aterm}
      [exec] (firefox) {firefox}
      [exec] (VMware) {vmware}
[submenu] (Terminals)
      [exec]   (xterm) {xterm}
      [exec]   (gnome-terminal) {gnome-terminal}
[end]

and so on...

hope this helped

---

### Post by MikeMLP on 2006-08-20
Thanks for the reply.  I knew fluxbox would involve a lot of editing of configuration files, and that certainly doesn't deter me, but I guess I just expected it to grab over some of the programs from my gnome install... live and learn.

---

### Post by crackseller on 2006-08-20
I'm sure there are menu generators for fluxbox, i.e. [http://gentoo-wiki.com/index.php?title=HOWTO_Fluxbox&redirect=no#menumaker](http://gentoo-wiki.com/index.php?title=HOWTO_Fluxbox&redirect=no#menumaker)

I can't tell you how good it is as I am using Openbox. But it should work fine.

---

