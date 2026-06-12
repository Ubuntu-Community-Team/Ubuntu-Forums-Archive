---
title: "[SOLVED] mounting an ISO as a CD"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by DingsBumps on 2007-12-17
Hi there, 
What I need help with is not mounting the iso, but mounting it (as a cd?). In other words, I want to be able to run my game without my cd.
What I've done so far is to:
-Make an iso using the "create copy" command from the right click menu
-make a directory to mount the iso in ```
sude mkdir /media/isoimage/
```
-use mount to mount the iso ```
sudo mount /home/editedout-myname/EXPANSION.iso/ /media/isoimage/ -t iso9660 -o loop

```

Now is when I have a problem. What I get from those commands is a virtual drive with the files that were on my cd. What I want is a virtual cd-drive with the iso mounted on it (a la Alcohol 52/daemon tools)
Thanks in advance.

---

### Post by brennydoogles on 2007-12-17
> **DingsBumps said:**
> Hi there, 
What I need help with is not mounting the iso, but mounting it (as a cd?). In other words, I want to be able to run my game without my cd.
What I've done so far is to:
-Make an iso using the "create copy" command from the right click menu
-make a directory to mount the iso in ```
sude mkdir /media/isoimage/
```
-use mount to mount the iso ```
sudo mount /home/editedout-myname/EXPANSION.iso/ /media/isoimage/ -t iso9660 -o loop

```

Now is when I have a problem. What I get from those commands is a virtual drive with the files that were on my cd. What I want is a virtual cd-drive with the iso mounted on it (a la Alcohol 52/daemon tools)
Thanks in advance.

I have not yet seen a way to do that on Linux. Which game are you running that requires a cd??

---

### Post by CatKiller on 2007-12-18
> **DingsBumps said:**
> What I get from those commands is a virtual drive with the files that were on my cd. What I want is a virtual cd-drive with the iso mounted on it (a la Alcohol 52/daemon tools)

These two things are exactly the same. If you want it to appear as a cd drive with a letter in Wine, you would point Wine to the folder you mounted your image and tell it to pretend that that folder is a cd.

What other problem are you having?

---

### Post by DingsBumps on 2007-12-18
> **CatKiller said:**
> If you want it to appear as a cd drive with a letter in Wine, you would point Wine to the folder you mounted your image and tell it to pretend that that folder is a cd.

That is exactly what I want to do. I didn't realize that you could do that. However, my game doesn't seem to be recognizing the folder I mapped to D: as a cd. This is what I did:
-Went into the wine config
-hit add new drive and browsed to /media/isoimage/  (is this right? or should it be somewhere else?)
-mounted my cd
-started the program, and then it said the cd was not in the drive. If I actually put the cd in the drive it works fine though. I don't think the problem is copy protection, but I might be wrong. But I really don't think so.

@brennydoogles- the game is diablo 2 LOD  :)

---

### Post by Niniel on 2007-12-18
The internets are your friend:

[http://www.latte.ca/D2LOD/]("http://www.latte.ca/D2LOD/")

---

### Post by DingsBumps on 2007-12-18
> **Niniel said:**
> The internets are your friend:

[http://www.latte.ca/D2LOD/]("http://www.latte.ca/D2LOD/")

I've followed the instructions and set the drive as d: in my config, but it still doesn't see a cd when it starts.

I know there isn't much to work from here, but if anyone has any ideas, I'd love to hear them.

---

### Post by DingsBumps on 2007-12-18
Well, I didn't really want to do it this way, but I just semi-gave up and followed[ this guide]("http://ubuntuforums.org/showthread.php?t=362457"). It's not what I would have ideally done as it is against the EULA, but eh, it works.
Thanks for the help anyways

---

### Post by CatKiller on 2007-12-19
> **DingsBumps said:**
> 
-mounted my cd
-started the program, and then it said the cd was not in the drive.

Is that the drive that you installed the game from? I recall that Windows games are really finicky about which drive you use - often you can't install from one drive and later play from another if you have two drives in your computer. Possibly that's what's happened here. Or perhaps it's some lame copy-protection interfering with the running of the game - that happens quite often, too.

---

### Post by DingsBumps on 2007-12-19
> **CatKiller said:**
> Is that the drive that you installed the game from? I recall that Windows games are really finicky about which drive you use - often you can't install from one drive and later play from another if you have two drives in your computer. Possibly that's what's happened here

Ya, that's a definite possibility. However, now that I do have the loader I won't go through the trouble of re-installing. If I do reinstall ill make sure to re-install from the same drive as I'll be mounting on. Thanks for all your help.

---

