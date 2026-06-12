---
title: "Downloading Source Programs"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by kane_666 on 2006-01-09
hey, I was wondering who here downloads the source of programs? like the programs you have to ./configure then make then make install. because at the moment thats all i can do until i get my wireless network card. and its **hell** i was going to download gparted so i could dual boot. so first i download the acutal program, then i go for the needed files. then i realise those needed files have needed files. and the needed files for the needed files have needed files. its a neverending visouce loop lol and it seems that every program i try to download is the same way. i am yet to install 1 application! lol

---

### Post by rooster on 2006-01-09
[QUOTE=kane_666]. so first i download the acutal program, then i go for the needed files. then i realise those needed files have needed files. and the needed files for the needed files have needed files. its a neverending visouce loop lol and it seems that every program i try to download is the same way. i am yet to install 1 application! lol[/QUOTE]

Hi,

just try the application Synaptic which is part of your Ubuntu-distribution (or Kynaptic if you have Kubuntu) and search for your application. If there are dependencies, they are downloades, too.

Or simply use ```
sudo apt-get install <programname>
``` and use the right <programname>. But the graphical applications are easier and you can search inside for the needed apps.

Hope it helps. If not, post the name of the application you are trying to install.

Ah, and you can download the sources via apt, if they are published and packaged, too.

Rooster

---

### Post by kane_666 on 2006-01-09
thanks for the help, but i've already installed all the apps from synaptic. thanks though ;)

---

### Post by estel on 2006-01-09
Yes, quite a few people build from source, but only when necessary. The dependencies are annoying, but most dependencies can usually be (eventually) ironed out using synaptic. The worst string of builds for me was trying to build some transcode stuff on AMD64.

But, tbh, it isn't too hard. As long as you've got everything that it needs (you'd still need to install all of these if you used Synaptic) then it is nothing more complicated than ./configure; make; sudo make install.

---

### Post by rooster on 2006-01-09
Hi estel,

just have a look at your link to your website - at least for me the link isn't working...

Rooster

---

### Post by Arktis on 2006-01-09
I build from source quite often.  Sometimes it's just a matter of personal preference.  But I do ./configure, make, checkinstall instead of using make install.  Packages are nice, after all.
Just stick with it and you'll get the hang of things.

---

