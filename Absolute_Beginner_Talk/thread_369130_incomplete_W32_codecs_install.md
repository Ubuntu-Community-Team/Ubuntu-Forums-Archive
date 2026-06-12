---
title: "incomplete W32 codecs install"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-02-24
I installed the following W32 codec package :

wget -c [http://www.debian-multimedia.org/poo...2-0.0_i386.deb](http://www.debian-multimedia.org/poo...2-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb

and it just stopped during the install.  It stopped short and returned me to the terminal prompt.  I tried to play a video in firefox and it still doesn't work.  I have already added mplayer.  How can I uninstall w32 and try to reinstall it??:confused:

---

### Post by TonKi on 2007-02-24
Add this line to your sources.list
```
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
```
and then run
```
sudo apt-get update
sudo apt-get install w32codecs
```

for feisty, replace edgy with it ;)

---

### Post by HadroLepton on 2007-02-24
are you sure that it stopped short? did it give any error messages?
note that when dpkg is done installing correctly it will also drop you to the prompt, without error messages.

do you have pitfdll installed?

also read this
[http://ubuntuforums.org/showthread.php?t=282344](http://ubuntuforums.org/showthread.php?t=282344)

---

### Post by rggavubt on 2007-02-24
> **HadroLepton said:**
> are you sure that it stopped short? did it give any error messages?
note that when dpkg is done installing correctly it will also drop you to the prompt, without error messages.

do you have pitfdll installed?

also read this
[http://ubuntuforums.org/showthread.php?t=282344](http://ubuntuforums.org/showthread.php?t=282344)

No error message...just returned to the prompt very fast.  I searched synaptic and only found gstreamer0.10(0.8)-pitfall which were both uninstalled...is this what you are talking about?

---

### Post by rggavubt on 2007-02-24
> **TonKi said:**
> Add this line to your sources.list
```
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
```
and then run
```
sudo apt-get update
sudo apt-get install w32codecs
```

for feisty, replace edgy with it ;)

How do I add that line to my sources list?

---

### Post by Maestro23 on 2007-02-24
> **rggavubt said:**
> How do I add that line to my sources list?

Use an editor(nano, gedit, etc..) and edit the sources.list 

> Ex: sudo nano -B /etc/apt/sources.list

You can type or copy/past the line in the file.  Save and exit.  Then:

> sudo apt-get update.

---

### Post by rggavubt on 2007-02-24
> **Maestro23 said:**
> Use an editor(nano, gedit, etc..) and edit the sources.list 



You can type or copy/past the line in the file.  Save and exit.  Then:

Where do I insert it in the file...under distributions?

---

### Post by Maestro23 on 2007-02-24
> **rggavubt said:**
> Where do I insert it in the file...under distributions?

Anywhere you want.  I would put it at the end.  Make a comment line like:

> #Win32 codecs
deb.....


Save and exit

---

### Post by rggavubt on 2007-02-24
> **Maestro23 said:**
> Anywhere you want.  I would put it at the end.  Make a comment line like:



Save and exit

Thanks...will do.

---

### Post by rggavubt on 2007-02-24
I want to thank everyone for all the help....I finally can watch trailers in firefox!!:popcorn:

---

### Post by Maestro23 on 2007-02-24
> **rggavubt said:**
> I want to thank everyone for all the help....I finally can watch trailers in firefox!!:popcorn:

:guitar:

---

### Post by asnd16 on 2007-03-10
I have another mirror site if needed - can be found here: 

[http://asnd16.com/****/w32codecs_20061022-0.0_i386.deb]("http://asnd16.com/****/w32codecs_20061022-0.0_i386.deb")

okok bad work in the folder that is it is located sooooo replace the **** with shi*  then it should work sorry . .

---

