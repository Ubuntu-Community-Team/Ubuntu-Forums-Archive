---
title: "Problems Installing &quot;Head Over Heels&quot;... HELP"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by gyalakias on 2006-10-23
I am a great fan of "Head Over Heels" (and of retro gaming in general), so when I learned that there was a Linux port of "Head over Heels", I literally jumped though hoops.

I downloaded the linux installer from here:

[http://retrospec.sgn.net/download.php?link=hoh&url=http://retrospec.sgn.net/games/hoh/bin/hohlin-101.tar.bz2](http://retrospec.sgn.net/download.php?link=hoh&url=http://retrospec.sgn.net/games/hoh/bin/hohlin-101.tar.bz2)

Anyway, I downloaded and manually extracted it. The extracted folder's location is now at /home/myusername/Desktop/hoh-install-1.01

I read the readme file and it said that I should run the install.sh file

So, I typed:

```
sudo -s (to go into "root" mode)
/home/myusername/Desktop/hoh-install-1.01/install.sh
```

This is what followed:

```
Head-Over-Heels installer
-------------------------

Head Over Heels will be installed in the following directories
(You may need to be logged in as root for this to work.):

Program: /usr/local/bin/
Datafiles: /usr/local/share/games/HoH/
Documenatation: /usr/local/share/doc/HoH/

..if you want to change this, edit the install.sh file.


Press ENTER to continue, or Control-C to quit.


---------------------------


Installing..
cp: cannot stat `./data/*': &#916;&#949;&#957; &#965;&#960;&#940;&#961;&#967;&#949;&#953; &#964;&#941;&#964;&#959;&#953;&#959; &#945;&#961;&#967;&#949;&#943;&#959; &#942; &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959;&#962; 
(EDIT: This means that there is no such file or directory... yeah, it's all greek to me too)
Couldn't copy game data

You may need to be root for this to work
```

Seriously, WTF?

I thought I WAS in root mode.

Anyone knows how to install this or tell me what it is that I am doing wrong?

Thanks in Advance.

By the way, I highly suggest this game. I've played it in Windows and it's a great port. But I REALLY want to be able to play it in Linux as well.

---

### Post by podunk on 2006-10-23
In Ubuntu to be root without sudo I type

```
sudo su
```

---

### Post by gyalakias on 2006-10-23
I've just tried it...

I still get the same answer.

I've also tried manually copying over the Data file at the /usr/local/share/games/ directory and I get the message that the program can't get executed.

Has anyone in here managed to get this to run?

---

### Post by DouglasCaixeta on 2008-06-21
I'm having the same problem!
Even if I type sudo su before type the command to install, still get the same error!

---

