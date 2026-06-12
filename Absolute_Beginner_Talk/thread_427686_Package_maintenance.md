---
title: "Package maintenance"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Rob2Kx on 2007-04-29
Hi, I have a few questions that are all related.  If anyone could answer any or all of them that would be great.

When I download some packages, other dependent packages are downloaded along with them.

1)  If I remove the original package, are the other ones removed as well?

2)  If not, is there a way to track which packages rely on which other packages?

3)  Is there a way to see which packages are being used and which aren't?

4)  And finally, what (if any) regular system maintenance is required in Ubuntu?  (ie:  In Windows it paid to diskcheck/defrag/regclean regularly)

Thanks in advance.  These forums are really helping me get to know Ubuntu.

---

### Post by oilchangeguy on 2007-04-29
quote:4) And finally, what (if any) regular system maintenance is required in Ubuntu? (ie: In Windows it paid to diskcheck/defrag/regclean regularly)

read this:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by starcraft.man on 2007-04-29
1) If you want to remove all the associated dependencies you uninstall the program with aptitude.

```
sudo aptitude remove "program"
```

If you want to leave them in, use apt-get

```
sudo apt-get remove "program"
```

2) I don't know of a specific way to search for dependencies...  You can always ...

```
sudo aptitude search "program"
```

in program, just use the beginning of the program, like acro and you will see a list of 3 programs for acroread and then the mozilla plugin acrobat uses. P means not installed, I means installed and v I believe is dependency. These are all lowercase letters and to the left.

3) not sure. Might try to use Package Manager (System -> Administration -> Synaptic Package Manager) and I believe if you look around you can find a program and search for its dependancies.

4) Nope, Ext3 requires no defrag its a journalling system.

PS: I wouldn't worry about dependencies... I don't think they will slow down your OS to any significant extent, unlike Windows >.<.

---

