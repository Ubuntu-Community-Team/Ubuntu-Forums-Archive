---
title: "Easy way to find terminal command to execute ubuntu utilities?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by doktarr on 2007-08-27
Hi all,

I was wondering if there is an easy way to find the names of the ubuntu utilities that I would use to launch them through the terminal.  For example, I know that the text editor command is "gedit".

This is only needed when I want to sudo something - otherwise I can just launch things through the menu.

---

### Post by LaRoza on 2007-08-27
> **doktarr said:**
> Hi all,

I was wondering if there is an easy way to find the names of the ubuntu utilities that I would use to launch them through the terminal.  For example, I know that the text editor command is "gedit".

This is only needed when I want to sudo something - otherwise I can just launch things through the menu.

Usually it is just the name, almost always lowercase.

What do you want to run as root? This command is dangerous, but may be useful:

```

gksudo nautilus

```

It will open the file browser as root, BE CAREFUL!

---

### Post by kerry_s on 2007-08-27
generally the name of the application is used. most can be found in /usr/bin.

---

### Post by Perfect Storm on 2007-08-27
also when found the command, here's two good help command:

Eg. gedit

```
gedit --help
man gedit
```

They are priceless if you want to know their options and examples.

---

### Post by doktarr on 2007-08-27
> **LaRoza said:**
> Usually it is just the name, almost always lowercase.

What do you want to run as root?
Well, I've been running "sudo gedit" in order to edit xorg.conf, as part of my war against the evils of overscan.

I actually did want to run nautilus as root, simply to rename some directories ("600 GB volume" lacks a certain je ne sais quoi).  I'm aware I could use mv in the terminal but I want to know how to use the utilities in the long run.
> **LaRoza said:**
> This command is dangerous, but may be useful:

```

gksudo nautilus

```

It will open the file browser as root, BE CAREFUL!

Will do.  Thanks for the help (likewise to the rest of you).

What's the difference between sudo and gksudo?

---

### Post by Perfect Storm on 2007-08-27
gksudo is used when executing graphical/gui interface. If you use sudo instead you can mess up Ubuntu.

Also try **nano** when editing and it can also been used outside X if an accident happen.

---

### Post by kellemes on 2007-08-27
> **doktarr said:**
> 
What's the difference between sudo and gksudo?

gksudo pops-up a graphical dialogbox for when you need to open a graphical app. as root-user.
sudo is for starting terminal apps.

---

### Post by arvevans on 2007-08-27
Larosa

"gksudo nautilus" solved a problem for me...thanks for the tip.

I had downloaded and tried installing the Mozilla Flash Player plugin from my desktop (didn't work because it is for 32-bit systems and not my 64-bit dual-core CPU, but that's another story) and could not remove all the multiple sub-directories garbage it left behind in my Desktop directory.  I started "gksudo nautilus", changed to my Desktop directory and sent the whole unwanted flash-player mess to the trash folder.  Now my Desktop is clean again.  Thanks again for the tip.

Arv
_._

---

### Post by yellowband on 2007-08-27
there is also a neat little script on ubuntuguide.org that makes a "run as roolt" option available as a right click menu item. it comes in handy sometimes.

---

