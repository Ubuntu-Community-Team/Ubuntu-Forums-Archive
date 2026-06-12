---
title: "What happend"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-06
Hi, when i started the computer to day i got some errors, here is pictures 
[http://bildr.no/view/73102]("http://bildr.no/view/73102")
[http://bildr.no/view/73103]("http://bildr.no/view/73103")
[http://bildr.no/view/73104]("http://bildr.no/view/73104")
PLZ HELP i need that computer for work NOW!

---

### Post by Inxsible on 2007-06-06
Seems like your NVidia drivers got screwed up. :(

---

### Post by ajmannen on 2007-06-06
I downloaded the Ubuntu studio files from synaptic to ubuntu......i like REALY need the comp NOW (big work task).
is there a simple comand to fix this

---

### Post by Inxsible on 2007-06-06
you can log into recovery mode, can you ?

---

### Post by ajmannen on 2007-06-06
no

---

### Post by jverkamp on 2007-06-06
I had a similar problem, but I have an ATI card so it may not be directly related (the errors refer to nVidia).

What were you doing before everything broke?  If you were recently editing the xorg.conf file (as I was) your best bet would be to roll it back to backup.  Otherwise, it might be easier to track down what happened if you could post what happened: did you just update any software, change any configuration settings, etc.

Posting your xorg.conf file might help as well, if you can get hold of it.

---

### Post by ajmannen on 2007-06-06
I downloaded the Ubuntu Studio Repo
I typed this in the terminal:
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
and then downloaded the ubuntu studio packs from synatpic

---

### Post by jverkamp on 2007-06-06
Why can't you log in to recovery mode?  Does the same error or a different one occur?

---

### Post by ajmannen on 2007-06-06
Nope, as smart as i am i only have 2 options to log on, Ubuntu studio and vista..................:(

---

### Post by ajmannen on 2007-06-06
Ok, f***** it. I need to work and i'll just download ubuntu studio from the web site and install it (my web conection has 17 Mb/s downoad speed so that won't take long)

Thanks for all the help

---

### Post by jverkamp on 2007-06-06
Could you use the install CD / a LiveCD to log in and get hold of the xorg.conf file?  It looks like something crazy is going on in there.

Just to check: you do have a nVidia graphics card?  If it's trying to load one (because of the new UbuntuStudio stuff) and you don't have one, that could be a problem.

---

### Post by jverkamp on 2007-06-06
Posted at basically the same time.  Sorry, I couldn't help more and good luck with the new install.  Awesome connection, by the way.  Where I work about 70 people share 3 Mb/s. :-(

---

