---
title: "Antivirus - Firewall events"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Kersus on 2006-03-19
So... Now that i'm online, what antivirus program is easy to get and install in Ubuntu?  Anything in that synaptic package manager I should get?

Also I have Firestarter working now and within an hour I have 24 events and 3 are considered serious..........   All the serious ones are TCP.  DCOM-scm, SMB, and Microsoft-ds.  Should I be worried about these?  How do I make sure Ubuntu is secure while online?

---

### Post by mcduck on 2006-03-19
[QUOTE=Kersus]So... Now that i'm online, what antivirus program is easy to get and install in Ubuntu?  Anything in that synaptic package manager I should get?

Also I have Firestarter working now and within an hour I have 24 events and 3 are considered serious..........   All the serious ones are TCP.  DCOM-scm, SMB, and Microsoft-ds.  Should I be worried about these?  How do I make sure Ubuntu is secure while online?[/QUOTE]
Default install of ubuntu is pretty safe even without a firewall. But having one is ok too. If you want to test it, you could try some tests here: [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")

Don't worry about firewall events unless you get lots of hits from same address. They are just sign that your firewall is doing it's job.

I don't know about antivirus programs for linux, as there is usually no need for one in Linux :) You only need one if you want to scan for windows virii :D

edit: there's ClamAV in repositories. You could try that if you really want.

---

### Post by Perfect Storm on 2006-03-19
I agree with mcduck

Nevertheless here's some anti-virus usually used to scan for win-virus:

HOWTO: Install F-Prot with GTK frontend (anti-virus)
[http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)

HOWTO: Install AVG free anti-virus
[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

---

### Post by Kersus on 2006-03-19
Thanks for the reply.

I forgot about clamav... I use clamwin for my XP (along with Antivir).  I love clamwin.

Anyhow, I went to get it through synaptic but it says its dependant on libgmp3 and that cannot be installed.

I also found this happening with most games.  They needed something that couldn't be installed like libsdl-mixer1.2

What do I do with that?

---

### Post by Perfect Storm on 2006-03-19
Make sure to enable universe and multiverse in your sourcelist.

```
sudo gedit /etc/apt/sources.list 
```

remove the # from the lines (except where there's two of them in a row)

add:

[b]## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
[/b]

if you want stuff like codecs java the easy way add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

save and exit.

then
```
sudo apt-get update
```

Edit: what shown above only works if you're on breezy.

---

### Post by Kersus on 2006-03-19
I have 5.04 Hoary Hedgehog.

---

### Post by trent dillman on 2006-03-21
Use Firestarter for a firewall and try ClamAV for antivirus, but the antivirus isn't that important.  DEFINITELY get Firestarter, though!

```
sudo apt-get -y install firestarter
```

---

### Post by meborc on 2006-03-21
[QUOTE=trent dillman]Use Firestarter for a firewall and try ClamAV for antivirus, but the antivirus isn't that important.  DEFINITELY get Firestarter, though!

```
sudo apt-get -y install firestarter
```[/QUOTE]
he already has firestarter... read man :D ...

as for Kersus... i guess if you change all those breezys in Artificial Intelligencen post into hoaryes... then you should be fine...

that is: breezy -> hoary

offtopic - you should consider upgrading to breezy badger 5.10... or even to the new dapper 6-06 when it is out... it is easily done and they both work a little faster and have some nice new features... but BACKUP first!

---

