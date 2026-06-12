---
title: "Installing KDE in Ubuntu"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by milad on 2006-12-27
I've been using Ubuntu for a few months and I totally like it. But I have this wrong/right impression that Gnome programs are very basic and i've heard that KDE programs are more advanced and customizable in many ways. So how should i install KDE in Ubuntu? Is it going to mess my current system or i can uninstall it later?

Generally, do you recommend installing KDE over ubuntu or should i think of a clean installation of Kubuntu?

---

### Post by highneko on 2006-12-27
You can install them both. I like to install gnome then install the kde apps I like. Kde is kinda buggy compared to gnome imo, so I would not suggest installing it from a package, but if you really want to, then I suggest 'sudo apt-get install kde-core'. Try just installing apps if you can, like 'sudo apt-get install konqueror' and 'sudo apt-get install kate'.

---

### Post by BarfBag on 2006-12-27
You don't even have to download the KDE dependencies by yourself.  When you install the package through aptitude, it grabs them automatically.  For example, if you want to install K3B (highly recommended), just fire up a terminal and type:

> sudo aptitude install k3b

It downloads and installs everything the program requires to run as well as the program.

---

### Post by Vorian on 2006-12-27
> **milad said:**
> 
Generally, do you recommend installing KDE over ubuntu or should i think of a clean installation of Kubuntu?

You can have multiple desktop environments, and choose your session when you login. (gnome/kde/xfce)

sudo aptitude install kubuntu-desktop

---

### Post by fuscia on 2006-12-27
you can even install less than kde-core by installing kdebase plus whichever programs you want to try. the other option is to install the kubuntu-desktop package (the only conflict you would have is that you would be asked to choose between gdm and kdm. stick with gdm for now).

---

### Post by milad on 2006-12-27
well, I think it includes at least 400 MB of downloading. 

So, can I somehow download and save it somewhere and then install it? So that I can use the installation file again and again on other computers without downloading the whole thing again .. ?

---

### Post by hyper_ch on 2006-12-27
I think the download is not 400 MB... the extracted files will use 400 MB... I think download is about 120MB... but not sure

---

