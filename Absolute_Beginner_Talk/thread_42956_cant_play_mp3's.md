---
title: "cant play mp3's"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by TanKilleR on 2005-06-20
I used the meda plyer, thedefault one that comes with ubuntu and it did not play the mp3. So I read the online guide a little and did the command but I got this error:

tankiller@server:~$ sudo apt-get install w32codecs
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tankiller@server:~$

So now I am lost ](*,)

---

### Post by Knome_fan on 2005-06-20
To get the default music player to play mp3s you need to install gstreamer0.8-mad, which is in the universe repository.
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

About the error you are getting. You simply have an other process/program using the resources needed open. You probably had synaptic open and then tried to install something from the command line. Close synaptic and everything should be fine.

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=TanKilleR]I used the meda plyer, thedefault one that comes with ubuntu and it did not play the mp3. So I read the online guide a little and did the command but I got this error:

tankiller@server:~$ sudo apt-get install w32codecs
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tankiller@server:~$

So now I am lost ](*,)[/QUOTE]

You need to do this first:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

THEN please type in this command into the terminal:

> sudo apt-get update

Then you can install all those programs from the guide. If you need more help please ask.

---

### Post by TanKilleR on 2005-06-20
I'm looking at step4 now and well, do I just copy/paste step4's code over the sources file? Then save?

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=TanKilleR]I'm looking at step4 now and well, do I just copy/paste step4's code over the sources file? Then save?[/QUOTE]

yep

over everything

---

### Post by TanKilleR on 2005-06-20
I finshed that, but I still cant seem to beable to play the mp3 files.

---

### Post by poofyhairguy on 2005-06-20
Ok. You are not done yet. Put this line into the terminal:

> sudo apt-get install gstreamer0.8-plugins libdvdcss2 xmms

Now you can play mp3s with rhythmbox or xmmx.

And also many other things (dvd, windows media files) will work too.

---

### Post by TanKilleR on 2005-06-20
Thanks, worked 100% But could you tell me why this was needed, like howcome an update to this is not included into the os(auto update). Maby I just dont get it, haha I am still quite new :)

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=TanKilleR]Thanks, worked 100% But could you tell me why this was needed, like howcome an update to this is not included into the os(auto update). Maby I just dont get it, haha I am still quite new :)[/QUOTE]

Sure, I'll explain. MP3s, Windows Media Files, and other media files like that are covered by certain patents that make it illegal to distribute each without paying a pretty big fee (per person). Since Ubuntu is free, it can't afford to play these fees. Luckily (as you found out) its not to hard to do it yourself, but if Ubuntu made it any easier it would be legally liable. I would hate for Ubuntu to die because of a lawsuit because it could play Windows Media Files out of the box.

Luckily the company that holds the patent for MP3s has never sued users, so you are safe. If you want to have a 100% legal alternative, then the real player is THE legal MP3 player in Linux.

[http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)

The Ubuntu operating system tries to be made completely of open software and solutions. All of Ubuntu's apps are legally free to use and distribute. That way Ubuntu helps develops these pieces of software, and is legally in ok shape.

Any more questions?

---

### Post by TanKilleR on 2005-06-20
Nope. I undetstand that and know what your saying. I'll take my leave now, and end this thred with one of my most enjoyed quites when I used windows:

> I say we all get on a big pirate ship with the biggest dish availabe and roam the seas downloading files like true pirates

But with linux's open sorce, we have nothing to fear :)

---

