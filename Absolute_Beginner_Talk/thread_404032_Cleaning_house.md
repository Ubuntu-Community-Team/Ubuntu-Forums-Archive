---
title: "Cleaning house"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by TehSnarf on 2007-04-07
I'm curious if there's a simple (or reasonable) way to find all the dependencies that are no longer needed and remove them? I've been messing around a bit with various packages, and I notice that when I remove some of them, it says that there're some that are no longer needed, but doesn't remove them. Just a pet peeve of mine... I mean if I'm not using them, why are they still on the machine?

Not too worried about it, I'll live another day since I got Edgy working like a champ just the way I want it... so it's about time to screw it up so I've got something else to do! Hints, tips, pointing me to reading material, anything will work.

Thanks in advance!

---

### Post by Happy_Man on 2007-04-07
Well, if you used aptitude to install, that would take care of the dependencies. But you obviously didn't, otherwise you wouldn't be here! :D Try 

```

sudo apt-get autoremove

```

Hope this helps!

---

### Post by Michaelt74 on 2007-04-07
I'm not sure if this helps, but this command cleans out the archives:

sudo aptitude clean

---

### Post by ardchoille42 on 2007-04-08
You can do "sudo apt-get autoremove" to remove unused deps as Happy_Man suggested, but that only works on Ubuntu releases **after** Dapper, Dapper does not have the "autoremove" option to apt-get.. it was added for Edgy after myself and a few others filed bug reports regarding unused dependencies. Alternatively, you can use aptitude for package management as it has had "Remove unused dependencies automatically" for a while.

---

### Post by Happy_Man on 2007-04-08
> **ardchoille42 said:**
> You can do "sudo apt-get autoremove" to remove unused deps as Happy_Man suggested, but that only works on Ubuntu releases **after** Dapper, Dapper does not have the "autoremove" option to apt-get.. it was added for Edgy after myself and a few others filed bug reports regarding unused dependencies. Alternatively, you can use aptitude for package management as it has had "Remove unused dependencies automatically" for a while.

Ah, so this would explain why every time I go to install/uninstall something via terminal, it pops up with "use sudo apt-get autoremove"? Hm...learn something new every day! :)

---

### Post by brennydoogles on 2007-04-08
> **TehSnarf said:**
> I'm curious if there's a simple (or reasonable) way to find all the dependencies that are no longer needed and remove them? I've been messing around a bit with various packages, and I notice that when I remove some of them, it says that there're some that are no longer needed, but doesn't remove them. Just a pet peeve of mine... I mean if I'm not using them, why are they still on the machine?

Not too worried about it, I'll live another day since I got Edgy working like a champ just the way I want it... so it's about time to screw it up so I've got something else to do! Hints, tips, pointing me to reading material, anything will work.

Thanks in advance!

There is a wonderful HOWTO by WackToMack on this very subject [HERE]("http://ubuntuforums.org/showthread.php?t=140920"). It will show you all kinds of tips and tricks for removing unused files from your system. Make sure to read the entire thread before you do anything, because there are a few minor issues that can occur if you are not careful. Good luck, and have a great day!!

---

