---
title: "Installing printer"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by fenderjaguar on 2007-02-20
hi. i'm using xubuntu and i wanted to install my epson dx6000 printer. first, i clicked on >Applications > Settings > Printing. but i couldn't find my printer listed there. i noticed it said you could put a windows driver CD in for it, but my dad had it somewhere and he wasn't home. so then i went to epson.com and downloaded what they claimed to be the linux drivers (it went in to the temp folder). 

anyways, i'm not sure how to install them from there. so i just waited until my dad was home and he found me the CD. but now when i click on the little "Printing" program, it just loads up and shuts down a second later. please help.

thanks

---

### Post by ashmew2 on 2007-02-21
If you have the native Linux driver , why worry about bad old' WIndows Drivers ? 
What is the format in which your Linux Driver Setup is in ? .tar.gz ? .tar.bz2 ? 
Let me know!!

---

### Post by fenderjaguar on 2007-02-21
thanks, but i'll get back to this thread when i get xubuntu up and running again (i kind of messed up on my dual install)

---

### Post by fenderjaguar on 2007-02-21
ok, so i downloaded the linux files, and <[this happens](http://fenderjaguar.net/images/screenshot-1.png)>

that command line stuff was what it said to do in the readme of the files i downloaded

---

### Post by fenderjaguar on 2007-02-21
oh yeah, and the unextracted file was a tar.gz

---

### Post by Maestro23 on 2007-02-21
> **fenderjaguar said:**
> ok, so i downloaded the linux files, and <[this happens](http://fenderjaguar.net/images/screenshot-1.png)>

that command line stuff was what it said to do in the readme of the files i downloaded

Have you installed build-essential and checkinstall? If not, open a terminal:

> sudo aptitude update && sudo aptitude install build-essential checkinstall

You need this when installing from source.

---

### Post by fenderjaguar on 2007-02-21
ok thanks. i did what you said, and it seemed to install this 'buildessential'. btw, during the downloaded and installing it asked me to put the installation disk in for "ubuntu edge" or something. i'm actually running xubuntu, but i put the disk in for that and it seemed to do ok.

but now i ran the same commands again, and now [this happens](http://www.fenderjaguar.net/images/terminal.png)

---

### Post by fenderjaguar on 2007-02-22
anyone have any idea?

---

### Post by fenderjaguar on 2007-02-24
sorry to bump the thread again. but any ideas?

---

### Post by Maestro23 on 2007-02-24
> **fenderjaguar said:**
> sorry to bump the thread again. but any ideas?

Seems its looking for CUPS (Common Unix Printing System).  Open up Synaptic and search for "cups".  If not installed, go ahead and install.

---

### Post by fenderjaguar on 2007-02-25
thanks, but i've just checked it, and it's already installed...

---

