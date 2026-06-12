---
title: "GRE and TOEFL s/w"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by hellmet on 2006-08-01
I have applies for the GRE & TOEFL dates,
and I got some cds along.
But to my dismay they needed to be
installed before they could be used.
Has anyone of you been successful in 
installing these cds either with Wine
or Cedega??
I really don't want to install Windows for
this thing.
But maybe I'd have to if its unavoidable!!

---

### Post by moma on 2006-08-01
Hello,
Try this

1) Copy the entire content of CD to your $HOME folder. Make a $HOME/lang/ folder and copy it there.

2) Install wine 
I have this "wine" repository in my /etc/apt/sources.list 
[COLOR="Indigo"]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/[/COLOR]

$ sudo apt-get update 
$ sudo apt-get install wine

3) Run setup.exe or equivalent program that comes with the CD. Does the CD need to be installed?
$ cd $HOME/lang
$ wine setup.exe 

Programs are installed under 
$HOME/.wine/drive_c/

4) Run it 
$ wine "c:\Program Files\path\anyprogram.exe"

---

### Post by hellmet on 2006-08-01
it does not run dude..
the hdd does something and then keeps quite..

---

### Post by srirammurali on 2006-08-09
yes sanju. both powerprep and kaplan don't run..  :confused:

---

### Post by davebgimp on 2006-08-09
Did you try running **winecfg** (to let wine find your cd drive)?

Then **wine path/to/cdrom/install.exe**

Don't know if it will work, but it's worth a try.

---

### Post by hellmet on 2006-08-11
nope .. doesn't work

---

### Post by srirammurali on 2006-08-11
sanju how about installing an old win98 using qemu.. am planning to install that way.. will tell u if it works

---

### Post by srirammurali on 2006-08-11
Princeton review is working fine now after mounting an image of the CD, and configuring drives in winecfg

---

