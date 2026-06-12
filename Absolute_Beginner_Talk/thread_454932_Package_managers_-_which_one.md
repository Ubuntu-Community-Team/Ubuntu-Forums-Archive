---
title: "Package managers - which one?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by linfidel on 2007-05-26
Ubuntu prompts me to use apt-get when I'm missing a program.  I've used synaptics on some occasions, and then I read about aptitude.  Then there's the add/remove...

Is it OK to use mixed managers?  I read somewhere that aptitude is better at handling dependencies, but only when you use it for both install and uninstall.

I've used them all, and now I'm wondering if I'm getting myself in trouble.

Thanks.

---

### Post by Outrunner on 2007-05-26
It doesn't matter, they all have their base in the same thing(APT).

---

### Post by Ek0nomik on 2007-05-26
Well, aptitude was the better one I believe until Feisty came along (or maybe it was Edgy, I don't really remember)

I think apt-get is just as good as aptitude these days, but I don't really know the nitty gritty of it all.

---

### Post by davahmet on 2007-05-26
They are all just interfaces for the same package manager, APT.  All of them use the same repositories and the same Debian-based method of handling dependencies and installations.  So, I guess the short answer is to use which ever one you're most comfortable with.

---

### Post by Tux Aubrey on 2007-05-26
And for the same reasons, I don't think mixing them makes any difference - I have installed things with Add/Remove, Synaptic and apt-get from the command line.  Apt-get has a few options that aren't obviously available with the gui front-ends - like clean and purge - but you don't usually need them.

---

### Post by OrangeCrate on 2007-05-26
> **Tux Aubrey said:**
> And for the same reasons, I don't think mixing them makes any difference - I have installed things with Add/Remove, Synaptic and apt-get from the command line.  Apt-get has a few options that aren't obviously available with the gui front-ends - like clean and purge - but you don't usually need them.

I've used everything above too, with no problems. I use these instructions to clean up everything once in a while:

[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

---

### Post by linfidel on 2007-05-26
> **OrangeCrate said:**
> I've used everything above too, with no problems. I use these instructions to clean up everything once in a while:

[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)
Thanks for that link - I'll be sure to bookmark it and pass it on to my buddies that I've led into Ubuntu-land.  Also, thanks for all the answers.  I think I'm probably too used to Windows where the registry becomes over-run with unused data, slowing down the system.  I suppose it's not really as big a deal to have extra files, what with the cost of disk space so low.  As long as it doesn't slow down the system (hmm, I guess it would slow down backups, though).

I can see where a command-line program is much easier to tell someone how to do a task than explaining all the various menus, etc.  That's what I thought the main difference was until a friend found some details that led me to believe Aptitude did more than the others.

Any other input is appreciated.

---

