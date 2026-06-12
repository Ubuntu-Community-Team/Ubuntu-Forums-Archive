---
title: "MP3 Support?"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by -=Raven=- on 2006-03-15
Arrgh! Now ive got my music ive just found out that Rythmbox wont play mp3s :confused: can i get a player or something to convert them? i dunno how it works on linux, i just used to use sound forge and save them as mp3s if they was a wav file.

---

### Post by Brunellus on 2006-03-15
please consult the RestrictedFormats page on the wiki for mp3 help.

Mp3 is a patent-encumbered and non-free codec;  Ubuntu does not include it by default for legal reasons.

---

### Post by icyisamu on 2006-03-15
Have you used Winamp before?

If so, you might want to do this in Terminal :

```

sudo apt-get update
sudo apt-get install xmms

```

Just answer Y(es) to the questions.

Installing it will get you a player that resembles Winamp. :)

---

### Post by Gimbo on 2006-03-15
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by meborc on 2006-03-15
[QUOTE=-=Raven=-]Arrgh! Now ive got my music ive just found out that Rythmbox wont play mp3s :confused: can i get a player or something to convert them? i dunno how it works on linux, i just used to use sound forge and save them as mp3s if they was a wav file.[/QUOTE]
a little search in the forums would have shown you the answer... :rolleyes: just to keep the threadcount down

---

### Post by -=Raven=- on 2006-03-15
Woohoo! Thank you!!!

---

### Post by exod40 on 2006-04-09
When i paste "sudo apt-get update
sudo apt-get install xmms" to the console happend this thing at the end of isntallin xmms:
'Unpacking xmms (from .../xmms_1.2.10+cvs20050209-2ubuntu2_i386.deb) ...
Setting up libgtk1.2-common (1.2.10-17build1) ...

Setting up libglib1.2 (1.2.10-10ubuntu1) ...

Setting up libgtk1.2 (1.2.10-17build1) ...

Setting up xmms (1.2.10+cvs20050209-2ubuntu2) ...

W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
Whan should i do to get xmms?

---

### Post by Bloch on 2006-04-09
I think you might already have it!
Type 
xmms
on a command line to check. The warnings about wine might be because you added an extra source to your list of repositories (did you do this yourself, or did you install wine using automatix?)
Anyway, check first to see if xmmx is in the menu, and then try to run it on the command line

---

### Post by nalmeth on 2006-04-09
W: Couldn't stat source package list [http://wine.sourceforge.net]("http://wine.sourceforge.net/") binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
 W: You may want to run apt-get update to correct these problems

Don't worry about this too much. Just a problem getting the package list from this mirror.
Will only affect wine updates/upgrades.

---

### Post by exod40 on 2006-04-09
You're right. I've xmms:)))

---

### Post by derjames on 2006-04-14
or use PuppyLINUX, it comes ready to play MP3 and many more media files...

---

