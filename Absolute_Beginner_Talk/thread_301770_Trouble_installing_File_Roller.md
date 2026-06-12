---
title: "Trouble installing File Roller"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Halfling Rogue on 2006-11-17
I keep getting an error saying that there's no makefile to be found. Is there a different command I'm supposed to use instead or something?

---

### Post by localuser on 2006-11-17
I believe that File Roller is a standard install with Ubuntu.  Are you sure its not already installed on your system?

Are you trying to install it from a tarball (.gz) file?  You may have better luck installing it with Synaptic Package Manager:

System | Administration | Synaptic Package Manager

Then search for file-roller

---

### Post by kerry_s on 2006-11-17
Are you compiling the latest? Did you install build-essential? I hope your going to use checkinstall and maybe upload the completed deb for others, if it's not to big. ;)

---

### Post by Halfling Rogue on 2006-11-17
I do have it installed, but it apparently doesn't have the plugin for unwrapping .rars, which is what I need. Synap Pack says I've already got 2.10 installed and won't show me anything else; I'm pretty sure I need 2.12, which is what I've downloaded and am having trouble with.

---

### Post by Halfling Rogue on 2006-11-17
Yeah, I'm compiling the latest, and I have no idea about build-essential. When I compile it it says I don't have g77, and I'm just hoping that's not a problem . . . 

Well, if I get it to work, I'll give the deb a shot!

---

### Post by localuser on 2006-11-17
> **Halfling Rogue said:**
> Synap Pack says I've already got 2.10 installed and won't show me anything else; I'm pretty sure I need 2.12, which is what I've downloaded and am having trouble with.

Not that it helps, since you obviously want to be on Ubuntu 5.04, but I'm on Ubuntu 6.10 and it has version 2.16.1 in its repos.  I don't know what version 6.06 has.

---

### Post by kerry_s on 2006-11-17
Umm, why not just use unrar? It's a heck of a lot easier. It's in the multiverse repo.

---

### Post by Halfling Rogue on 2006-11-17
> **localuser said:**
> Not that it helps, since you obviously want to be on Ubuntu 5.04, but I'm on Ubuntu 6.10 and it has version 2.16.1 in its repos.  I don't know what version 6.06 has.

Not quite. I actually want Dapper, but my burner isn't working so I can't make my own install disk, and the ones I ordered via snail mail won't come in for a while yet. Thanks anyway, hopefully when Dapper gets here it'll have it. In the meantime, I have a bunch of files from my old system that I can't get to. ](*,)

---

### Post by Halfling Rogue on 2006-11-17
> **kerry_s said:**
> Umm, why not just use unrar? It's a heck of a lot easier. It's in the multiverse repo.

Apparently my SynPac can't find it. Is there another way to get it?

---

### Post by localuser on 2006-11-17
> **Halfling Rogue said:**
> Apparently my SynPac can't find it. Is there another way to get it?

Haven't tried it myself, but see if this helps...

[http://ubuntuforums.org/archive/index.php/t-1070.html](http://ubuntuforums.org/archive/index.php/t-1070.html)

[Edit] Be sure to specify your version

---

### Post by kerry_s on 2006-11-17
> **Halfling Rogue said:**
> Apparently my SynPac can't find it. Is there another way to get it?

Do you got multivers enabled? It should look like this at the end-> main restricted universe multiverse

Here's a link to the free version-> [http://rpm.rutgers.edu/repository/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.5.4-0.1_i386.deb](http://rpm.rutgers.edu/repository/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.5.4-0.1_i386.deb)

Here's non-free-> [http://rpm.rutgers.edu/repository/ubuntu/pool/multiverse/u/unrar-nonfree/unrar-nonfree_3.3.6-2_i386.deb](http://rpm.rutgers.edu/repository/ubuntu/pool/multiverse/u/unrar-nonfree/unrar-nonfree_3.3.6-2_i386.deb)

---

### Post by Halfling Rogue on 2006-11-17
> **localuser said:**
> Haven't tried it myself, but see if this helps...

[http://ubuntuforums.org/archive/index.php/t-1070.html](http://ubuntuforums.org/archive/index.php/t-1070.html)

[Edit] Be sure to specify your version

A-ha, got it! Or at least, it says I've got it. I'll figure out how to use it in a second.

---

### Post by Halfling Rogue on 2006-11-17
. . . Or not. I've got it as a text in completion-contrib and I have no idea how to use it.

---

### Post by kerry_s on 2006-11-17
From the man pages it looks like you use it like any other extracter-> [http://www.edenwaith.com/support/untar/help/unrar.html](http://www.edenwaith.com/support/untar/help/unrar.html)

unrar -e (your rar)

---

### Post by Halfling Rogue on 2006-11-17
> **kerry_s said:**
> From the man pages it looks like you use it like any other extracter-> [http://www.edenwaith.com/support/untar/help/unrar.html](http://www.edenwaith.com/support/untar/help/unrar.html)

unrar -e (your rar)


Okay, it was actually --extract, but it's working. Well, sort of. It starts and then it's failed to open each and every file in the rar. *sigh*

---

### Post by kerry_s on 2006-11-17
Oh well, it was worth a try. Sorry it didn't work.

---

### Post by Halfling Rogue on 2006-11-17
> **kerry_s said:**
> Oh well, it was worth a try. Sorry it didn't work.

That's okay, thanks for all your help. I saw somewhere that it doesn't work on 3.0 version rars, maybe that's the problem.

---

### Post by CatKiller on 2006-11-18
> **Halfling Rogue said:**
> That's okay, thanks for all your help. I saw somewhere that it doesn't work on 3.0 version rars, maybe that's the problem.

Some people have reported problems getting things unrarred with **unrar**. You could try installing **rar** instead - it's in the Multiverse repository too. It **should** integrate with File Roller so that you can stay in the GUI.

---

### Post by Halfling Rogue on 2006-11-18
> **CatKiller said:**
> Some people have reported problems getting things unrarred with **unrar**. You could try installing **rar** instead - it's in the Multiverse repository too. It **should** integrate with File Roller so that you can stay in the GUI.

Awesome; thank you! If all fails, I've got some friends who are willing to convert them to zips for me, but I hope it works.

---

