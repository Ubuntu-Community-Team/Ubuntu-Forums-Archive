---
title: "recommendation please"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-15
Hey people. I just built my first Ubuntu running PC (no dual boot), and would like your recommendations on some applications. 
Well I got Beryl working :) (even though I can't get it to install themes ;( )
I have installed VLC Player, Inkscape, amule, azureus and gdesklets.

I'm looking for a good mp3 player, and an antivirus program if it's necessary to have one. 
Any other application that you might think are good to have.

thanks

---

### Post by Rocket2DMn on 2007-06-15
Anti-virus not necessary.
I use Rhythmbox for my music, but everybody has their preferences.  I suggest just trying some built-in programs for yourself.

---

### Post by PartisanEntity on 2007-06-15
I like Amarok, it is not only an mp3 player but a music manager and it also displays helpful info from wikis, it also plays streaming radio etc..

As far as antivirus, I am one of those who are of the opinion that even though you do not need it to protect your Ubuntu machine, it is good to have in order to catch windows viruses from windows users and to prevent them from being sent to other windows users.

I view it as something one would do to help keep friends and relatives who use Windows safe. Opinions differ on this :)

avg is a good antivirus software.

---

### Post by Golyadkin on 2007-06-15
I vote for Rhythmbox as a music player. It has a Last.fm plugin, downloads album covers on the fly and allows me to search my 10,000+ songs library very quickly.

---

### Post by HotShotDJ on 2007-06-15
As far as AV is concerned, you don't need it.  It is a waste of your computer's resources.  Unless you are running a mail server for windows clients, don't bother.

(One could argue for using AV to prevent your forwarding viruses unknowingly -- I reject that argument.  If they want to run an insecure OS, let them use their own system resources to run AV protection.)

---

### Post by ROUBOS on 2007-06-15
Thanks people. 
Is the a .rar archive program????

---

### Post by H.E. Pennypacker on 2007-06-15
Audacious audio player.

> **ROUBOS said:**
>  
Is the a .rar archive program????

What are you asking here?  This question is not clear.

---

### Post by ROUBOS on 2007-06-15
I just downloaded an archive and it's not a ZIP file but a RAR file.
Winrar in windows extracted them. In Ubuntu now I cannot extract the rar archive

---

### Post by Rocket2DMn on 2007-06-15
To extract a rar file:
```
tar -xvf filename.tar /path/to/extraction
```
More details can be checked out with
```
man tar
```

also, if you ever end up with tar.gz (or .tgz) files, you can unzip the file by running:
```
gunzip filename.tar.gz
```
However, this may not be necessary if you are just extracting the tarball.

---

### Post by ROUBOS on 2007-06-15
thanks.
found this on another thread

sudo aptitude install p7zip p7zip-full rar unrar

works fine now :)

---

### Post by machoo02 on 2007-06-15
> **Rocket2DMn said:**
> To extract a rar file:
```
tar -xvf filename.tar /path/to/extraction
```
More details can be checked out with
```
man tar
```

also, if you ever end up with tar.gz (or .tgz) files, you can unzip the file by running:
```
gunzip filename.tar.gz
```
However, this may not be necessary if you are just extracting the tarball.

This will not extract things from a **.rar** archive...it is diffferent from a .tar archive.  What you are looking for is either unrar or unrar-free (to extract things from the archive) or rar (to create .rar archives), all of which are available in the repositories.

---

### Post by Rocket2DMn on 2007-06-15
LOL my bad.  Details details!  It's Friday, please forgive me!

---

