---
title: "Uninstalling Thunderbird"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Majin Zero on 2007-03-16
I'd like to get rid of Thunderbird and use sylpheed as my mail client, however when I go to uninstall thunderbird...

Xubuntu Desktop


under the "needs to be removed"


uh...so...I can't get rid of thunderbird?

---

### Post by aysiu on 2007-03-16
You can remove *xubuntu-desktop* if you're planning to do a fresh reinstall of the next Xubuntu release.

If you're planning to upgrade to the next release, however, you should keep *xubuntu-desktop* installed.

---

### Post by Majin Zero on 2007-03-16
hmm. Ok.

But as of right now I'd like to uninstall Thunderbird, but keep the Xubuntu Desktop. Anyway to do that?

---

### Post by aysiu on 2007-03-17
Removing Thunderbird doesn't remove XFCE. You will still have a functional desktop.

*xubuntu-desktop* isn't anything substantial. All it is is a pointer to other *real* packages. *xubuntu-desktop* is defined as the default set of packages in Xubuntu. Once you remove one of those default packages, you no longer have that definition.

It'd be just like if I defined a "package" called *coolstuff* and had it point to AmaroK, VLC, KRename, and TagTool. Removing AmaroK would then remove *coolstuff*, since one of the four packages would be gone, but I'd still have VLC, KRename, and TagTool.

Another way to think about it--let's say you have a six-pack of beer. There's a big label on it that says "Six-pack of beer." Then someone takes one of those cans of beer out. Well, it's no longer a six-pack, is it? It's now a five-pack. Same deal with *xubuntu-desktop*. Everything else will function just fine without Thunderbird. You just won't have the label--*xubuntu-desktop*.

It is recommended, however, that you keep *xubuntu-desktop* for smoother upgrades. But, as I said before, if you're planning to do a clean reinstall of Xubuntu Feisty next month, smooth upgrades won't matter.

---

### Post by Majin Zero on 2007-03-17
Hmmm, Ok I understand that removing the meta package won't damage my system, but you said removing it would cause issues when upgrading. That's my only concern. It isn't imperative that I remove Thunderbird. Mostly just wanted to learn a bit more about the whole package system and dependencies and what not. Thanks for all your info and help.

---

### Post by aysiu on 2007-03-17
> **Majin Zero said:**
> Hmmm, Ok I understand that removing the meta package won't damage my system, but you said removing it would cause issues when upgrading. That's my only concern. It isn't imperative that I remove Thunderbird. Mostly just wanted to learn a bit more about the whole package system and dependencies and what not. Thanks for all your info and help.
If you're planning on upgrading, you should keep *xubuntu-desktop* installed.

I tend to opt for clean reinstalls, but that's a choice we all make.

---

