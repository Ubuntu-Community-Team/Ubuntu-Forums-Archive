---
title: "&quot;remove xubunu-desktop&quot; doesn't totally undo &quot;install xubuntu-desktop&quot;. Why?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-06-15
"remove xubunu-desktop" doesn't totally undo "install xubuntu-desktop". 
When I did "sudo apt-get install xubuntu-desktop", it took a lot of time and installed a lot of packages adnd took up a lot of megabytes.


Later, I did "sudo apt-get remove xubuntu-desktop". It only remove that one package.

I didn't record all the packages installed when i did "install xubuntu-desktop" because i thought "remove xubuntu-desktop" would handle that intelligently.

What can i do now? How do you guys install things? Is there a better way to go about this, so that I don't have this problem of unneeded packages staying on my computer?

---

### Post by Jagot on 2006-06-15
You should use aptitude instead of apt-get, so when installing it would be:

```
sudo aptitude install xubuntu-desktop
```

and to remove:

```
sudo aptitude remove xubuntu-desktop
```

Aptitude handles dependencies better than apt-get, but removing packages with aptitude only works if you have installed them with aptitude, so you may want to bear that in mind in the future.

You could try in Synaptic clicking on the package and selecting 'mark for complete removal'.  Not sure if there is any other way than going through and removing the xubuntu packages manually if that doesn't work - someone may be able to enlighten you on that one.

---

### Post by hanzj on 2006-06-15
[QUOTE=Jagot]You should use aptitude instead of apt-get. Aptitude handles dependencies better than apt-get, but removing packages with aptitude only works if you have installed them with aptitude, so you may want to bear that in mind in the future.
[/QUOTE]

Thank you for your advice. If aptitude has such benefits, then why are all the instructions on this forum, and on irc, and elsewhere always using "apt-get" and not "aptitude"?

I wish I did all my previous installations with aptitude.

Are there any disadvantages to using aptitude?

---

### Post by glotz on 2006-06-15
aptitude is 8 letters
apt-get is only 7

:)

Just kidding. Probably aptitude is a newer thing around than apt-get. I think that there's no downside to aptitude and it should replace apt-get.

---

### Post by confused57 on 2006-06-15
Here's how to remove everything installed with Xubuntu-desktop:

[http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php)

---

### Post by aysiu on 2006-06-15
Actually, Jagot, in order for *aptitude* to work properly, you have to install it with these two commands: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` That update is very important to having *aptitude* work properly for uninstalling.

---

### Post by hanzj on 2006-06-15
aysiu,
in what instances should we do "sudo aptitude update"? Do we run that command before every time we do a "sudo aptitude install foo"?
or just when we are installing kubuntu-desktop, xubuntu-desktop, ubuntu-desktop?

---

### Post by aysiu on 2006-06-15
Every time you want a clump of packages to be remembered together (in case you might remove them later), you should do the update before the install.

---

