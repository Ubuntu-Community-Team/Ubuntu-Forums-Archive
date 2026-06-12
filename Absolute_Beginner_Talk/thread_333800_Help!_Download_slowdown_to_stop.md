---
title: "Help! Download slowdown to stop"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by tordan on 2007-01-07
Help!

I'm having trouble with all programs that download.

Example: I open Automatix and choose a desired program, the download begins fine and then the Kb/ s begin to drop, until eventualy reaching zero. When left running the connection will sometime grab a hold and download a little then shut off again. 

The same accurs in frostwire, update manager, synaptic manager, etc..

The signal on the DSL modem appears to be fine according to the light indicators. Firefox operates at normal speed.

I suspect a software conflict, but I know very little.

I have no idea where to go on this.

---

### Post by justin whitaker on 2007-01-07
I don't think it has anything to do with you or your system. I am running an update on an fresh install, and its SLOW. Automatix, Synaptic, Update Manager, and apt all go to official repositories and mirrors....so I'm guessing a load issue on Cannonical's end.

---

### Post by riven0 on 2007-01-07
I heard the way to correct this was to take the us. out of the server list. Like changing this:

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

to this:

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

This won't help for automatix, but it could help for the update manager and synaptic.

---

### Post by justin whitaker on 2007-01-07
> **riven0 said:**
> I heard the way to correct this was to take the us. out of the server list. Like changing this:



to this:



This won't help for automatix, but it could help for the update manager and synaptic.

2 minutes, and solved. You guys and gals rock!

---

### Post by tordan on 2007-01-07
Where is this "Server List" located? I would gladly change it.

---

### Post by MkfIbK7a on 2007-01-07
well what riven says is true but the only reason is because more people are clogging the us servers so i suggest not spreading that solution around so as not to clog these servers as well....

---

### Post by tordan on 2007-01-07
So we simply have to wait?

---

### Post by tordan on 2007-01-08
I'm not sure if I understand our options? Do we have any?

---

### Post by MkfIbK7a on 2007-01-08
try to install something then just wait a while see what happens post any errors....

---

### Post by quartzy on 2007-01-08
> **tordan said:**
> I'm not sure if I understand our options? Do we have any?

Doing what riven said will most likely speed up your downloads, and what wert is saying is if to many people starting doing it those servers will slow down as well..

---

### Post by tordan on 2007-01-08
Will this problem be fixed if we continue on this server? Or is the only foreseeable solution to move to the alternate one?

---

