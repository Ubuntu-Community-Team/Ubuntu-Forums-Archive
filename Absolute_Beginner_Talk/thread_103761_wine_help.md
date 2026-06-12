---
title: "wine help"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by iand675@gmail.com on 2005-12-14
I'm trying to compile wine from source for my amd 64 k8 kernel, but i dont know how to do it exactly. can anyone help?
oh one other problem is that my dvd-rw cd rom drive doesn't show up anymore. any ideas how to fix that?

---

### Post by aysiu on 2005-12-14
Do you know how to compile anything from source, just not Wine? Or you need just the basics? If it's the latter, see the second link in my sig.

---

### Post by Hallavej on 2005-12-14
[QUOTE=iand675@gmail.com]I'm trying to compile wine from source for my amd 64 k8 kernel, but i dont know how to do it exactly. can anyone help?
oh one other problem is that my dvd-rw cd rom drive doesn't show up anymore. any ideas how to fix that?[/QUOTE]

Dont even try to compile wine on an amd64!!! instead:
download the .deb file, and in a terminal:
sudo dpkg -i --force-architecture the_.deb_file

and the dvd thing. Did you mount it?

---

### Post by iand675@gmail.com on 2005-12-15
ok, well i fixed the dvd problem, but i dont understnad the force architecture thing. care to explain that a little bit more in depth?

---

### Post by aysiu on 2005-12-15
Well, as I understand it, the .deb in the repositories is made for x86 architecture. "Force architecture" probably forces the .deb to install even if it's built for the wrong architecture.

---

### Post by iand675@gmail.com on 2005-12-15
right, well i got that it forced it to operate anyways, but what i meant was: Wouldnt that cause it to operate kind of oddly? You know, cause a bunch of compatibility issues and such? If it would be worth it to do force architecture, how do i do that exactly? I'm still very new to this.

Oh, and I'm also trying to install azureus, but I can't seem to get it to run. What do I do about that?
Heh, one final question: Is there any way to run exe files off of a cd or dvd?

---

