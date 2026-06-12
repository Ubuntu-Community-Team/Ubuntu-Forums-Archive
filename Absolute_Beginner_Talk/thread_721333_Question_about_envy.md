---
title: "Question about envy"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-03-11
I already have my ati card running in gutsy by using restriced drivers management.

Compiz fusion runs good, but gaming is impossbile, the 3d games aren't running good, lines everywhere.

If I use envy, will this get sorted? Will I be able to play 3d games?

The card was able to play half life 2 when I had vista installed.

---

### Post by glennric on 2008-03-11
I have never used envy myself, but if I understand correctly, envy will just install the same drivers that the restricted manager installs.  You could try it though.

---

### Post by ibizatunes on 2008-03-11
i used envy on my g.f machine, it has an ATI card and it fixed some 3d issue!
hope this helps

---

### Post by billgoldberg on 2008-03-11
Ok, i'll give it a try.

---

### Post by forrestcupp on 2008-03-11
Envy does not use the same drivers as the Restricted Drivers Manager.  The RDM uses what was out when Gutsy was released, and Envy uses the latest drivers from ATI.

Installing drivers with Envy will sort out a lot of problems and give you much better performance.  But you will still not be able to play 3D games if Compiz is running.  If you have Compiz running, you will still get flickering.  But with Compiz turned off, you shouldn't have any major issues.

Just remember, if you use Envy, you'll have to uninstall the drivers when you upgrade to Hardy, then reinstall them afterward because of the kernel upgrade.  Envy makes that easy, though.

---

### Post by glennric on 2008-03-11
I have an nvidia card and not an ati, but I didn't use envy and have the restricted modules installed.   With this I do have the latest nvidia drivers installed.  They are the same as the latest ones on the nvidia website -- version 169.12.

---

### Post by forrestcupp on 2008-03-11
I see.  With ATI drivers there is a huge difference.  There have been a lot of major advancements since the drivers that the RDM has.

---

### Post by billgoldberg on 2008-03-11
> **forrestcupp said:**
> Envy does not use the same drivers as the Restricted Drivers Manager.  The RDM uses what was out when Gutsy was released, and Envy uses the latest drivers from ATI.

Installing drivers with Envy will sort out a lot of problems and give you much better performance.  But you will still not be able to play 3D games if Compiz is running.  If you have Compiz running, you will still get flickering.  But with Compiz turned off, you shouldn't have any major issues.

Just remember, if you use Envy, you'll have to uninstall the drivers when you upgrade to Hardy, then reinstall them afterward because of the kernel upgrade.  Envy makes that easy, though.

Thanks for the clarification.

I don't upgrade, I do clean installs.

The installation was easier than expected. Download the deb, open the program, let it install the missing dependencies, install the ati card (it automatically picks the right driver) and reboot.

Compiz fusion seems to run a bit smoother and the reflection plugin actually works now (without slowing everything down to unusable proportions).

I'm downloading nexuiz right now (removed it because it wasn't playable).

---

### Post by kpkeerthi on 2008-03-11
> **glennric said:**
> I have an nvidia card and not an ati, but I didn't use envy and have the restricted modules installed.   With this I do have the latest nvidia drivers installed.  They are the same as the latest ones on the nvidia website -- version 169.12.
The version in the [repository]("http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new") is only 100.14.19 :confused:

---

### Post by billgoldberg on 2008-03-11
> **kpkeerthi said:**
> The version in the [repository]("http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new") is only 100.14.19 :confused:

From what I know about the official repositories is that they only include tested and stable software.

I guess the latest version haven't been tested enough.

I'm sure that the hardy release will have the latest stable version in its repo's.

---

### Post by kpkeerthi on 2008-03-11
Yes.. I understand that. But I was wondering how come glennric was using 169.12 from the repository if the latest available is only 100.14.
>  Originally Posted by glennric  View Post
I have an nvidia card and not an ati, but I didn't use envy and have the restricted modules installed. With this I do have the latest nvidia drivers installed. They are the same as the latest ones on the nvidia website -- version 169.12.

---

### Post by glennric on 2008-03-11
I am being a bit of a dork.  I compiled my own restricted modules and included the latest nvidia drivers in my compilation.  I compile my own kernel, and so I can't use the default restricted modules anyway.

---

### Post by billgoldberg on 2008-03-11
I just tried to run nexuiz after disabling compiz fusion.

There are no more lines but the game is slow as hell. Unplayable.

I have a 384mb full 3d ati card (hell it plays half life 2 and counterstrike source without any problems on high settings).

I hope the linux ati drivers will be improved alot in the future.

---

### Post by billgoldberg on 2008-03-11
> **kpkeerthi said:**
> Yes.. I understand that. But I was wondering how come glennric was using 169.12 from the repository if the latest available is only 100.14.

Who knows from what repository he was downloading, there are hundreds.

Maybe from the hardy repo?

---

