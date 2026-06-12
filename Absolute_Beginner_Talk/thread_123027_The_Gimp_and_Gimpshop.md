---
title: "The Gimp and Gimpshop"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by blud on 2006-01-29
Firstly I'm sorry if this is in the wrong forum couldn't decide whether to put it in here or Art and Imaging but as I am an absolute Beginner (Installed it yesterday) I figured this would be a great starting point.
Ok so I think the Gimp is a really good Image editing program have been using it for a little while in Windows however I still can't get my head around the interface so I thought it was great when I found a place that had changed the interface to look more like Photoshop
       [www.gimpshop.net](www.gimpshop.net) sorry not sure how to make it a clickable link
Am just wondering if anyone knows of a place to get gimpshop for Ubuntu as my understanding is Ubuntu requires Deb programs to install but on the gimpshop website I have only found an Rpm version.

---

### Post by Perfect Storm on 2006-01-29
You could try alien it.

```
sudo apt-get install alien
cd /where/the/.rpm/package/is
sudo alien XXXXXXXX.rpm
sudo dpkg -i XXXXXXXXXX.deb

```

But there's possibility it won't work.

---

### Post by blud on 2006-01-29
[QUOTE=Artificial Intelligence]You could try alien it.

```
sudo apt-get install alien
cd /where/the/.rpm/package/is
sudo alien XXXXXXXX.rpm
sudo dpkg -i XXXXXXXXXX.deb

```

But there's possibility it won't work.[/QUOTE]

I'm sorry don't realy understand this properly but please correct me if I'm wrong but I download the rpm version of gimpshop assuming the name of the file is gimpshop I would type the followiung into terminal

```
sudo apt-get install alien
cd /where/the/.rpm/package/is
sudo alien gimpshop.rpm
sudo dpkg -i gimpshop.deb

```

then theres a possibility that it may work

---

### Post by lemmy999 on 2006-01-29
Blud

You've nearly got it. line 2 means that you have to change directory (cd) to wherever you've downloaded the RPM file:)

---

### Post by timczer on 2006-01-29
There was a .deb made for gimshop and posted on this thread: [http://www.ubuntuforums.org/showthread.php?t=67525&highlight=gimpshop](http://www.ubuntuforums.org/showthread.php?t=67525&highlight=gimpshop)

I think what is availabe on RapidShare is the newest version of gimpshop.

---

