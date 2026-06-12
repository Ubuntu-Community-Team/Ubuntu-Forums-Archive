---
title: "Problem Installing Program"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Genotrius on 2007-02-15
I'm having a little bit of trouble installing the program Inkscape. 
I've navigated to the unzipped .tar.gz file as per the README file included, and I typed in the command ./configure, also as per instruction. Everything runs fine for a moment, looking like it's trying to install, but it all stops at this:
```
checking for png_read_info in -lpng... no
configure: error: libpng >= 1.2 is needed to compile inkscape

```

What should I do?

---

### Post by Bachstelze on 2007-02-15
Is there any reason whay you want to compile inkscape from source ? It is available from the repos, just do *sudo apt-get install inkscape*.

---

### Post by tronica on 2007-02-15
well you need the libpng package, but inkscape is in the repos.

> sudo apt-get install inkscape

---

### Post by RomeReactor on 2007-02-15
Hi. Open a terminal (Applications-->Accessories-->Terminal) and write

```
sudo apt-get install libpng12-0
```

and press ENTER. After it finishes installing, try to install Inkscape again.

**EDIT**: That's right, you can install Inkscape from Synaptic and that will take care of all the dependencies for you (unless for some reason you want a slightly more up-to-date version, from **0.44** to **0.45**).

---

### Post by Genotrius on 2007-02-16
Well, the reasn I'm installing it from source is because I don't currently have an internet connection on my Ubuntu computer because of another issue.

Is there any way I can get libpng12-0 on, say, a flash drive and put it on that computer?

---

### Post by energiya on 2007-02-16
try finding the .deb files: Inkscape or libpng12-0. You can then install those. Or just download the source. And to answer your question, yes, you can put it on a flash drive and copy it on your computer.

---

### Post by aysiu on 2007-02-16
Inkscape (marked in red) doesn't appear to have additional dependencies (besides what's already installed in Ubuntu), even though it has plenty of suggested/recommended packages (marked in orange).

So, really, all you have to do is download [this file](http://mirrors.kernel.org/ubuntu/pool/main/i/inkscape/inkscape_0.44-1ubuntu2_i386.deb), transfer it to the desktop of your non-connected computer, and then type these commands in the terminal: ```
cd ~/Desktop
sudo dpkg -i inkscape_0.44-1ubuntu2_i386.deb
``` Or double-click the .deb file.

---

