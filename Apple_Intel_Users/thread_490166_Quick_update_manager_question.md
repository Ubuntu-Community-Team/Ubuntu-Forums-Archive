---
title: "Quick update manager question"
date: 2007-07-02
forum: Apple Intel Users
---

### Post by russo.mic on 2007-07-02
so,  for about a week now, my update manager has always had an update available.  and everytime I click it to check for new updates, it comes up saying it wants to do a partial upgrade.  and compiz is always available for an upgrade.  usually if it has something else to upgrade, it will go ahead and install that.  but if there's nothing but compiz, it just quits, saying there are no updates available for my system.

I'm not really concerned, as I don't use compiz anyway, and my system seems to be running fine, but I would like to be able to update to gusty when the time is right, and this sounds like trouble brewing.  Also, it would be nice if my update manager didn't chime in everytime I started gnome.  any ideas anybody?

Thanks in advance for any assistance you can lend!

Russo

---

### Post by huzzak on 2007-07-10
I use Beryl to prettify my system, and I am experiencing the same problem as you.  I tried enabling Compiz to see if that would deal with the problem, but no dice.

---

### Post by benanzo on 2007-07-10
You can get rid of this issue by opening Synaptic and uninstalling anything with compiz in the name.  It seems to me that you might have conflicting versions or unmet dependencies.  After you uninstall you should reload your package list or do:
```
sudo apt-get update
```
And reinstall Compiz.  That should fix this for you.  APT wont allow you to automatically update a package if it will conflict with something that is currently installed.  I suspect that is what has happened.  It will, however, continue to offer that package as an update even though you can't install it, which is annoying.

Good Luck!

**NOTE:** Don't remove **ubuntu-desktop** (which it might ask you to do.)  That will remove almost everything on your system!

---

### Post by huzzak on 2007-07-11
Okay, thanks.  When I went to remove compiz the update manager told me that it'd have to remove ubuntu-desktop as well, which seemed like a bad idea, so instead I clicked on compiz-core and selected upgrade.  This removed compiz, left my desktop and seems to have done away with the annoying problem of having Ubuntu inform me that there are updates which can't, in actual fact, be updated.  Thanks for the tip.

---

### Post by benanzo on 2007-07-11
I forgot that **desktop-effects** (compiz)  is part of the **ubuntu-desktop** metapackage that if uninstalled would remove *everything*.  Thanks for not doing that...I would have felt bad.  I added a note to my post to prevent hasty noobs from destroying their system.

---

### Post by alephsmith on 2007-07-11
ubuntu-desktop is a meta package. You can safely remove it. It does not remove other packages.

---

### Post by benanzo on 2007-07-11
That's true but I seem to remember at one point doing:
```
sudo apt-get remove ubuntu-desktop
```
or using Synaptic and APT requesting to remove every other piece of my desktop along with it.  It is safer not to get rid of it unless you know what you're doing.

---

### Post by russo.mic on 2007-07-29
Yeah, I'm gonna err on the side of caution, let's not remove ubuntu-desktop from our systems, as it lists just about every think but the kitchen sink.  if it's really just a meta-package, then it's not like it's taking up a notable amount of hard-drive space.  and it might be used to refer to packages in the future.  why invite trouble?  

just my $0.02.

---

### Post by cyberdork33 on 2007-07-29
if you explicitly try to uninstall ubuntu-desktop you remove all the packages it refers to. I have removed the ubuntu=desktop metapackage several times getting compiz setup and it does not remove all the software. Besides, you should reinstall it after.

---

