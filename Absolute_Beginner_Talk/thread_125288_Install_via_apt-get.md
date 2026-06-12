---
title: "Install via apt-get"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-02-03
OK! I have a failure installing Opera following the wiki guide. The alternative is using the apt.sources list file.How do I go about this?
Thanks



*[size=1]Locked due to triple posting - Artificial Intelligence*[/size]

---

### Post by aysiu on 2006-02-03
Don't use the Breezy .deb from the Opera website. Use the static/other .deb.

---

### Post by e-blade on 2006-02-03
The sources.list is the place where your synaptic gets its repositories from.
You can find it in:

/etc/apt/sources.list

Editing it with appropriate sources for your country(or anywhere else for that matter), save it, open a terminal and type:

sudo apt-get update

After that type:

sudo apt-get install <insert-what-to-install-here>

---

### Post by Sbarton on 2006-02-03
I Do not see another file except the Breezy file! Do you?



[QUOTE=aysiu]Don't use the Breezy .deb from the Opera website. Use the static/other .deb.[/QUOTE]

---

### Post by aysiu on 2006-02-03
[QUOTE=Sbarton]I Do not see another file except the Breezy file! Do you?[/QUOTE] Yes. It's right here.

---

