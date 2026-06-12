---
title: "Different Desktop Environments... Sessions... Eh??"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-06-16
*I don't really know where this should go... But felt that if it was out of place here, the moving of it will be a useful thing for me to note, so I know where to post in future.*

I was peering about the forums, and in a thread comparing Ubuntu to Kubuntu, Aysiu mentioned having all three (Ub, Kub, and Xub) installed, and choosing whichever (He?) felt like with sessions.

 Sessions is the bit at login, correct? I think I had to use it once when I #@!%ed something up royally to go in with a default sesh (thus the change I made was not loaded and could be removed.)

 So, before I go poking in the system, as I am prone to do, I'm here asking for help. I don't have any CDs to back up all my work, so I don't want to kill old Bernard (though she seems to have a new breath of life now that I installed those nifty nVidia drivers, thanks to the peeps that helped with that.)

 Anyhow, babbling over - do I just pop into the Synaptic and install 'Xubuntu Desktop' and 'Kubuntu Desktop'...?

 And I have 10GB free on my HD (I haven't figured out how to use my slave drive yet, which is 7GB) and this won't stuff my HD to the brim, will it?

(I want to play about and see what the other *buntu's are like, you see. I might flicker about from one to another depending on my mood, like with themes... :D)

---

### Post by aysiu on 2006-06-16
The proper way to install Xubuntu and Kubuntu involves a command called *aptitude*.

Do **not** install them with Synaptic or *apt-get*.

More details here:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by Raavea on 2006-06-16
Danke Aysiu~! You're always so helpful. :3

*showers you with skittles*

---

### Post by 23meg on 2006-06-16
xubuntu-desktop and kubuntu-desktop will install XFCE and KDE along with all the settings and applications that belong to Xubuntu and Kubuntu and likely clutter all your desktop environments with unwanted apps. If you just want to check out other desktop environments, just install them by their own:```
sudo aptitude install xfce4 kde
```

---

### Post by aysiu on 2006-06-16
23meg, *kde* is a metapackage that actually contains *more* (not fewer) applications than the *kubuntu-desktop* metapackage.

And *xfce4* by itself is not terribly useful. *xubuntu-desktop* is polished and creates an environment that won't be culture shock to someone who's used to Gnome.

Finally, as I said before, *apt-get* is not the way to go with desktop environments, especially if you just want to try them.

---

### Post by 23meg on 2006-06-16
I should confess I suggested this based on my own experience, which is a bit distorted: the -desktop metapackages caused major cluttering in my use when Dapper was in development and I ended up with a mixup of different GDM and usplash themes. When I installed KDE to take a look at it with Breezy though, I don't recall having any major problems.

Anyway, aysiu is more experienced with multiple desktop environments and you should take his word.

---

### Post by aysiu on 2006-06-16
I think you bring up a good point, though--menus do get a bit cluttered.

For the record, these are the KDE metapackages available in order based on size of installation:

kdebase
kde-core
kubuntu-desktop
kde

---

### Post by uzi09 on 2006-06-16
whats a metapackage?

---

### Post by aysiu on 2006-06-16
It's a pointer. It just points to other packages.

So when you say to the package manager, "Install Inkscape," Inkscape is a real package that gets installed, and it's a program you can use.

However, when you say to the package manager, "Install Kubuntu," Kubuntu is not a package. It's a pointer to all the other real packages that make up the Kubuntu default installation (AmaroK, Adept, Kopete, etc.).

It's sort of like going to a restaurant you frequent and ordering, "The usual," instead of ordering, "The artichoke dip, a strawberry lemonade, and the house lasagna."

---

### Post by Raavea on 2006-06-17
> It's sort of like going to a restaurant you frequent and ordering, "The usual," instead of ordering, "The artichoke dip, a strawberry lemonade, and the house lasagna."
 :lol: Very good analogy.

---

### Post by Raavea on 2006-06-17
Okay, that's not good. I'm in Kub, was installing Xub, and got this error about thirty times near the end of the installation;
> ** (process:11445): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failedShould I be worried?
It hasn't said the install failed, but all those errors. And is that MYSQL?? :shock:

---

### Post by bluevoodoo1 on 2006-06-17
[QUOTE=aysiu]The proper way to install Xubuntu and Kubuntu involves a command called *aptitude*.

Do **not** install them with Synaptic or *apt-get*.

More details here:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)[/QUOTE]

I'm curious to know about the aptitude method. Are there other benefits other than those previously mentioned in this thread?

---

### Post by aysiu on 2006-06-17
You mean the benefit of actually being able to remove the metapackage components later?

I don't know if there are other advantages. That's enough advantage for me.

---

### Post by bluevoodoo1 on 2006-06-17
[QUOTE=aysiu]You mean the benefit of actually being able to remove the metapackage components later?

I don't know if there are other advantages. That's enough advantage for me.[/QUOTE]

If using aptitude to remove a *-desktop meta-package are you given the ability to choose what packages stay and what go, or is it all or nothing?

---

### Post by aysiu on 2006-06-17
It's kind of all or nothing. If you want to, though, you have the option to uninstall with *apt-get* even if you installed with *aptitude*.

If you don't want to remove the full thing, you could do ```
sudo apt-get remove kubuntu-desktop
sudo aptitude update
sudo aptitude install gtkorphan gksu
gksudo gtkorphan
``` and then find all the packages individually that you want to get rid of.

---

### Post by bluevoodoo1 on 2006-06-17
[QUOTE=aysiu]It's kind of all or nothing. If you want to, though, you have the option to uninstall with *apt-get* even if you installed with *aptitude*.[/QUOTE]

Ok that's very good to know. 

(Occasionally I'll install kubuntu-desktop so i can fully indulge myself in the KDE. After I've had enough I find myself removing it [using your guide to remove the kubuntu-desktop meta-package], but there are always a few essential K applications that I want to stick around.)

---

### Post by Raavea on 2006-06-17
Well, despite the errors, Xub seems to be working. It don't seem much different from the Gnome in Ub though...

 I don't think I like Kub... It's got lots of cool little flickets, but its so... Windows-ey. *shudders*

...The Xub menu is a little wierd since I've only just adjusted to the Ub one, but Kub's is horrid.

 I'm going to be playing around a lot with the three, since I like fiddling. I usually fiddle with webpages, but I'm going away for a week in a few days, and don't want to get into anything... I'm sure any coders/programmers here understand. :lol:

Oooh, love the rat (shh..) for Xub! I have ratties~! They seem very impressed at your choice of mammal. :lol:

 ...Still. I don't think I'll be using Kub much. *shudders some more*

---

