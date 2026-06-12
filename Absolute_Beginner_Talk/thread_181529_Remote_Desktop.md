---
title: "Remote Desktop"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-05-24
When i used to use XP and not know how much better ubuntu was, i used to use remote desktop all the time.  is there a real good+safe and secure way for remote desktop over the internet with ubuntu

---

### Post by ozPATT on 2006-05-24
i haven't seen one yet, but then i am a complete newbie, so nothing strange there... good question though. I used to use [www.logmein.com](www.logmein.com) a lot for remote access.. I hope you find something. :)

---

### Post by mlind on 2006-05-24
You're probably looking VNC. Go with TightVNC or FreeNX.

for windows you should use UltraVNC

---

### Post by youthforlinux on 2006-05-24
[QUOTE=ozPATT]i haven't seen one yet, but then i am a complete newbie, so nothing strange there... good question though. I used to use [www.logmein.com](www.logmein.com) a lot for remote access.. I hope you find something. :)[/QUOTE]

i've used that once in the past but i thought that it waz only for windows

---

### Post by ozPATT on 2006-05-24
[QUOTE=youthforlinux]i've used that once in the past but i thought that it waz only for windows[/QUOTE]

it probably is... i used it on windows, just mentioning it. :) i also, could do with a linux version... going to look for TightVNC :)

---

### Post by mlind on 2006-05-24
[QUOTE=ozPATT]it probably is... i used it on windows, just mentioning it. :) i also, could do with a linux version... going to look for TightVNC :)[/QUOTE]

```

$ apt-cache policy tightvncserver
tightvncserver:
  Installed: (none)
  Candidate: 1.2.9-8ubuntu2
  Version table:
     1.2.9-8ubuntu2 0
        500 http://fi.archive.ubuntu.com dapper/universe Packages

```

it's on universe repository. You should have vnc client already installed.
It's called 'vncviewer'.

---

### Post by youthforlinux on 2006-05-24
Does tightvnc work over the internet?
like logmein

---

### Post by mlind on 2006-05-24
[QUOTE=youthforlinux]Does tightvnc work over the internet?
like logmein[/QUOTE]

Yes, it's for remote access for X over the network (or locally why not).
try command *apt-cache show tightvncserver* for more info.

You can also access remotedly on windows from Ubuntu this way.

---

### Post by youthforlinux on 2006-05-24
[QUOTE=mlind]Yes, it's for remote access for X over the network (or locally why not).
try command *apt-cache show tightvncserver* for more info.[/QUOTE]

that is good to know

---

### Post by ozPATT on 2006-05-26
[QUOTE=mlind]

You can also access remotedly on windows from Ubuntu this way.[/QUOTE]

so i could access my computer from work (use windows), through that program somehow? do you access it through the browser or something? i have so much to learn :(

---

### Post by ProjectGod on 2006-05-26
hi all,

there's a tool that comes with breezy badger by default...

under **APPLICATIONS **... **INTERNET **... "**Terminal Server Client**"

it acts as a VNC viewer and RDP client which is niffty for connecting to windows xp / 2003 servers over the internet. 

on the other hand if you want others to view your machine you can use the tool under **SYSTEM ... PREFERENCES... REMOTE DESKTOP**... which allows incomming connections.

:)

---

### Post by youthforlinux on 2006-05-26
[QUOTE=ProjectGod]hi all,

there's a tool that comes with breezy badger by default...

under **APPLICATIONS **... **INTERNET **... "**Terminal Server Client**"

it acts as a VNC viewer and RDP client which is niffty for connecting to windows xp / 2003 servers over the internet. 

on the other hand if you want others to view your machine you can use the tool under **SYSTEM ... PREFERENCES... REMOTE DESKTOP**... which allows incomming connections.

:)[/QUOTE]
does that only work with ur home network?
how do u enable for it to broadcast over the net?

---

### Post by mlind on 2006-05-26
[QUOTE=ozPATT]so i could access my computer from work (use windows), through that program somehow? do you access it through the browser or something? i have so much to learn :([/QUOTE]

Yes, It's actually very easy thing to understand. One machine acts as VNC server
which multiple VNC clients can connect through client application.

For example, you install TightVNC or UltraVNC (which is faster) server application to
your windows machine, start the application and configure password for connecting
clients. (you have to also plug hole in your firewall for this).

On any client machine (which may be Ubuntu or another windows machine) you
start client application and give URL (and X session) of the server machine,
provide password and that's it.

Just try it yourself!

---

### Post by shanepardue on 2006-05-30
i know that with ultravnc, you have a server and a viewer.

what i don't understand is how you can view your linux desktop from a windows machine...any ideas or tutorials one can point me to?

thanks!


p.s. i really love this forum..you guys are a great help!!

---

### Post by shanepardue on 2006-05-30
wow ubuntu made that really easy to do..sorry for wasting a new topic over that.

---

