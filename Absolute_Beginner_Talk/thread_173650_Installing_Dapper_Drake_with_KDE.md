---
title: "Installing Dapper Drake with KDE"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by brady618 on 2006-05-10
Okay, I'm a true n00b, so bear with me.  Currently I'm using Breezy, and I want to upgrade to Dapper.  I know there are risks, but the system I'm trying this out on is a piece of crap anyway, and not my main computer.  I also want to try KDE once I upgrade.  Now for the ?'s  Be nice, and please don't mind if they're stupid. :D 

1. Will I have to reinstall Opera or Firefox 1.5 when I upgrade or when I switch to KDE?  From what I've read, Automatix doesn't work in Dapper, and that's what I used to install both of them.  I also read that KDE doesn't install firefox by default, but I'm curious if it will still allow it to run if it was previously installed.
2. Would it be better to go to KDE before upgrading to Dapper or vice versa?  Or does it not matter?
3.  How exactly do I go about doing either of these things?  (KDE/Dapper)
4.  Since the computer I'm putting it on is a p.o.s., will the upgrade utilize my system resources better (700 mhz cpu 256 mb ram), or would I be better staying with what I have?

Thank you in advance for any advice or instructions you'd be willing to give me.

---

### Post by brady618 on 2006-05-10
What I meant by "will Opera/Firefox still be installed" is will it still be available in my applications menu, or will I have to find it in the folders and put it in the menu.

Thanks again for any help.

---

### Post by manicka on 2006-05-10
I think it would be best to upgrade first before adding kde

Just change your sources.list to dapper repos then,

```
sudo apt-get update
sudo apt-get upgrade
```

Lot's of people find that the upgrade breaks X. To fix this run 

```
sudo dpkg-reconfigure xserver-xorg
```

restart gdm

```
sudo /etc/init.d/gdm start
```

then
```
sudo apt-get install kubuntu-desktop
```

I also think it would be a good idea to uninstall Firefox 1.5 before the upgrade process and let the Dapper version take over from 1.07

---

### Post by brady618 on 2006-05-10
Thanks for the advice.  How do you uninstall programs, as I've never done it before?  Can I keep Opera or should I uninstall that as well?  Since Dapper comes with the older version of firefox, I can still upgrade back to 1.5 once it's all said and done, right?

---

### Post by cyracks on 2006-05-10
[QUOTE=brady618]
What I meant by "will Opera/Firefox still be installed" is will it still be available in my applications menu, or will I have to find it in the folders and put it in the menu.
[/QUOTE]
It will be there, but dapper uses 1.5.0.3 so it would be better if you remove the old one.

[QUOTE=brady618]
2. Would it be better to go to KDE before upgrading to Dapper or vice versa?  Or does it not matter?
[/QUOTE]
I think it doesn't matter, but I would rather upgrade to dapper and then install kde.

[QUOTE=brady618]
3.  How exactly do I go about doing either of these things?  (KDE/Dapper)
[/QUOTE]
After you upgrade the system install **kubuntu-desktop** package
$apt-get install kubuntu-desktop (or with synaptic)

[QUOTE=brady618]
4.  Since the computer I'm putting it on is a p.o.s., will the upgrade utilize my system resources better (700 mhz cpu 256 mb ram), or would I be better staying with what I have?
[/QUOTE]
In my case system is much faster then before.

---

### Post by manicka on 2006-05-10
You can probably just remove Opera with Synaptic. I'm not sure how Automatix installs Firefox but I imagine it's similar to the process on this wiki page. Uninstall directions are at the bottom.

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

I've also heard the Automatix can cause problems for the upgrade. Good luck with it :)

If all goes well you might find Bumps as a handy replacement for Automatix

[http://www.ubuntuforums.org/showthread.php?t=138889](http://www.ubuntuforums.org/showthread.php?t=138889)

---

### Post by brady618 on 2006-05-10
So you're saying I SHOULD remove Opera before I upgrade?  Will it mess up the upgrade or something?

---

### Post by manicka on 2006-05-10
[QUOTE=brady618]So you're saying I SHOULD remove Opera before I upgrade?  Will it mess up the upgrade or something?[/QUOTE]

I don't use Opera so I'm not sure what the upgrade prcoess will do to it

---

