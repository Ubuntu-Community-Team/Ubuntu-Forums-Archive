---
title: "Virtalbox is possed by the devil"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by godd4242 on 2007-07-12
EDIT:
NO I DO NOT KNOW WHAT POSSED MEANS EITHER.

...In short, I can't install anything because my computer reads virtualbox is installed improperly.

```
dking@dking-laptop:~$ sudo apt-get install conky
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
dking@dking-laptop:~$ 

```

Delightful, of course.

However, here's the rub:

```
dking@dking-laptop:~$ sudo rm virtualbox
rm: cannot remove `virtualbox': No such file or directory
dking@dking-laptop:~$ rm virtualbox
rm: cannot remove `virtualbox': No such file or directory
dking@dking-laptop:~$ 

```

Exciting, I know.

And I try to open synaptic to remove it, and receive this :):):):):):):)

```
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

Well that's helpful.

I'm sure it is to someone more knowledgeable than I, but as it were, it's not very helpful for me.

PS: This makes it so I can't install anything, uninstall anything, update my computer, or use synaptic.

Now I've been fairly stable of late with my computer, but I feel as though its time to move from Beryl to Fusion, install conky, and stop being a wussy about messing with my computer again.

(I broke broke it a good 3 times after I just installed it. lawl @ accidentally destroying the x window system)


Anyways, thanks to all.

---

### Post by Seisen on 2007-07-12
Have you tried reinstalling VirtualBox?

---

### Post by SendDerek on 2007-07-12
I had some problems with the package manager acting up some time ago.  I don't know if you have the same issue as I did, but it might help:

[http://ubuntuforums.org/showpost.php?p=2381565&postcount=8](http://ubuntuforums.org/showpost.php?p=2381565&postcount=8)

That's the answer I got in my original thread.  Maybe it will help you.  


To save you a click:
> 
sudo dpkg --purge -r VirtualBox

and if that doesn't work try this: sudo dpkg --purge --force-remove-reinstreq -r VirtualBox


Also, just to point this out, virtualbox is the only app I know of on linux that actually uses a capitol V and B in it's name.  If you type in "virtualbox" instead of "VirtualBox", synaptic will have no idea what you're talking about in the first place.

---

### Post by SendDerek on 2007-07-19
What?  No followup?

---

