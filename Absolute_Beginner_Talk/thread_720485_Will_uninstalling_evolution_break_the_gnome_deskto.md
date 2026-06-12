---
title: "Will uninstalling evolution break the gnome desktop?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Liet_Kynes on 2008-03-10
Okay there are quite a few of these threads around and I'm not sure which one to follow since a few of them claim to totally break the ubuntu-desktop

I would like to uninstall evolution from my system since i don't use it. Can someone please tell me the safe way to do it?

---

### Post by Cadmus on 2008-03-10
Can't remember off the top of my head, but I know it's possible to do it, is this under Feisty or Gutsy?

---

### Post by Liet_Kynes on 2008-03-10
I'm running Gutsy. The 64bit version if that makes a difference.

---

### Post by scramasax on 2008-03-10
Frankly, I'd leave well alone.

I know it's resource-heavy, but, AFAIK, it doesn't load if you don't start it, so where's the problem? -- unless your hard-disk is getting really full.

If you must, start the package manager:

System > Administration > Synaptic

Then click Search and type in "evolution".  Now find Evolution in the list and right-click and mark for removal.  Then click "Apply".

But, as I say, I'd leave well alone.  In any case, you may prefer something else now -- say, a lighter email-only client -- but further down the road you may want something Evolution does, like built-in GNUPG or calendaring.

---

### Post by Arkenzor on 2008-03-10
Try uninstalling it from Synaptic (see previous post), and if it is needed by other packages Synaptic will ask you if you want to remove them as well. You can safely cancel the uninstallation at that point.

Also, don't fret over Synaptic needing to remove the ubuntu-desktop package. Despite its important-looking name it's only a dummy package depending on all the packages in the standard Ubuntu installation (meaning that removing _any_ of the packages installed by default will remove ubuntu-desktop as well - but like I said it's not a problem because it's only a dummy).


As for the reason for this package, it allows people running another Ubuntu flavor (Xubuntu, Kubuntu, whatever) to install all the programs in the standard Ubuntu CD by installing ubuntu-desktop from Synaptic. Even though the package itself doesn't contain anything, Synaptic will install all the other base Ubuntu packages as its "dependencies".


I hope that was clear enough. At any rate: 

- You can safely try removing a package using Synaptic; if that would require other packages to be removed as well then Synaptic will warn you, and ask you wether you want to proceed. And actually, even if you realize later that you actually needed that package you can just install it again, through Synaptic as well. I *think* Synaptic will even backup your configuration for a program when removing it, and restore it when you reinstall it.

- There are a number of dummy packages such as ubuntu-desktop which can be safely removed because they don't contain _any_ data at all. You'll know by reading the package's description.

---

### Post by Liet_Kynes on 2008-03-10
Ok. I'm gonna try that now and let you guys know what happens .

EDIT: Just did it and rebooted (not necessary I think) but I guess it worked. Just panicing over nothing I guess :)

---

### Post by jordanmthomas on 2008-03-10
The reason people say it breaks Ubuntu is that it will cause future upgrades (not just updates) to not go right.
The reason for this is that a package called ubuntu-desktop relies on evolution.  ubuntu-desktop is just a package that relies on everything installed by default.  When hardy comes out, ubuntu-desktop will likely have more dependencies.  Since you don't have it installed, you won't get some of the new programs when they come out.

I personally wouldn't call this "breaking" anything since if you want to have everything later you can just reinstall ubuntu-desktop and then remove what you don't want.  

On a side note, this kind of stuff is exactly why I prefer rolling release distros.

Anyway, good to hear your system didn't die.

---

### Post by Liet_Kynes on 2008-03-10
Thanks for clarifying that Jordan.


Just one more thing. What do you mean by rolling release distros?

---

### Post by FuturePilot on 2008-03-10
I believe Evolution was removed from the ubuntu-desktop dependency. You should be able to remove it without removing the ubuntu-desktop package.

A rolling release distro is one that gets the new versions of software immediately. Ubuntu is not a rolling release since the repositories are frozen at release time.

---

### Post by Oldsoldier2003 on 2008-03-10
> **FuturePilot said:**
> I believe Evolution was removed from the ubuntu-desktop dependency. You should be able to remove it without removing the ubuntu-desktop package.

A rolling release distro is one that gets the new versions of software immediately. Ubuntu is not a rolling release since the repositories are frozen at release time.

yeah Ubuntu has a fast release cycle so freezing the repos isn't a big deal. besides it gives you and excuse to play around and compile apps :)

---

### Post by jordanmthomas on 2008-03-10
> **FuturePilot said:**
> I believe Evolution was removed from the ubuntu-desktop dependency.


Thanks, I didn't know that.  (Haven't used Ubuntu in a loooong time though, so it's only fair.  :) )

---

### Post by Oldsoldier2003 on 2008-03-10
> **jordanmthomas said:**
> The reason people say it breaks Ubuntu is that it will cause future upgrades (not just updates) to not go right.
The reason for this is that a package called ubuntu-desktop relies on evolution.  ubuntu-desktop is just a package that relies on everything installed by default.  When hardy comes out, ubuntu-desktop will likely have more dependencies.  Since you don't have it installed, you won't get some of the new programs when they come out.


if i was going to upgrade my distro i would probably opt for a clean install this time, since my /home is on a different drive.  But even with Ubuntu desktop uninstalled  you can just
```

sudo apt-get update
sudo apt-get upgrade
sudo apt get dist-upgrade
```

---

### Post by FuturePilot on 2008-03-10
> **jordanmthomas said:**
> Thanks, I didn't know that.  (Haven't used Ubuntu in a loooong time though, so it's only fair.  :) )
No problem ;)

---

### Post by jordanmthomas on 2008-03-10
> **Oldsoldier2003 said:**
> if i was going to upgrade my distro i would probably opt for a clean install this time, since my /home is on a different drive.  But even with Ubuntu desktop uninstalled  you can just
```

sudo apt-get update
sudo apt-get upgrade
sudo apt get dist-upgrade
```

I certainly believe you (no real reason not to), but if this is the case why do people always get so upset about removing ubuntu-desktop?

---

### Post by Oldsoldier2003 on 2008-03-10
> **jordanmthomas said:**
> I certainly believe you (no real reason not to), but if this is the case why do people always get so upset about removing ubuntu-desktop?

because of the misunderstanding about the meta package. I have to admit i was a bit concerned too until i understood more about how it works.

---

### Post by stchman on 2008-03-10
> **Liet_Kynes said:**
> Okay there are quite a few of these threads around and I'm not sure which one to follow since a few of them claim to totally break the ubuntu-desktop

I would like to uninstall evolution from my system since i don't use it. Can someone please tell me the safe way to do it?

I uninstalled Evolution on my laptop and nothing broke.

```
sudo apt-get autoremove evolution
```

After that remove the residual config in synaptic and you are set.  The autoremove command will remove all unused dependencies.

---

