---
title: "how to uninstall programs/packages?"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by x5452 on 2006-04-08
I would like to know how to uninstall a few packages I have tried but either didnt like or couldnt get to work.  they are conky, gkrelm, and evolution mail, (im attempting to get thunderbird to work with aol now)  can someone tell me the proper way to uninstall these?  thank you

---

### Post by Landser on 2006-04-08
In a terminal, type:

**sudo apt-get remove <package_name>**

---

### Post by aysiu on 2006-04-08
If you say how you installed them, someone can help you uninstall them.

---

### Post by x5452 on 2006-04-08
ah my bad i didnt realize that part mattered, oops.  well evolution i installed by downloading through synaptic package manager and gkrel the same.  conky i used terminal apt-get

---

### Post by bionnaki on 2006-04-08
read this: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by aysiu on 2006-04-08
If you install it through Synaptic, you can uninstall it through Synaptic.

Right-click on the package and select "mark for uninstall."

Then click "Apply."

---

### Post by x5452 on 2006-04-08
thanks, just wanted to make sure it was the "proper" way to get rid of programs.  cool, thank you

---

### Post by x5452 on 2006-04-08
way curious here, I went into synaptic and went to evolution that I want to uninstall, i click mark for removal and I get a box that says it will remove all kinds of other stuff also, "the chosen action also affects other packages. The following changes are required in order to proceed." then theres a box, a down arrow next to [B]To be removed[B] and it lists things like gnome desktop, all my applets, ect...what is that about?

---

### Post by dvarsam on 2006-04-08
_Question_:

How could somebody remove a package with the "dpkg -i xxxx.deb" command?

Is there a "dpkg -remove xxx.deb" command?

Thanks

---

### Post by x5452 on 2006-04-08
ok so I cant take it anymore, stupid evolution is just sitting there, not even set up anymore, taking up all kinds of ram performance. I am going to uninstall it through synaptic the same way i installed it.  But it tells me its going to remove all kinds of other stuff too like gnome desktop stuff, gdesklets stuff, why does it do this?  Is there a way to save what i have set up now in case it ruins it?  It took days to get it all set up, (with the help of most of you) id hate to see it all go just because evolution is a ram hungry Bi$%$

---

### Post by Stranger678 on 2006-04-08
Well dude, I can't guarantee anything, but when I uninstalled a prog this morning, I got the same message about ubuntu desktop, I went with it anyway, and it didn't affect at all. System ran great afterwords, good luck.

---

### Post by x5452 on 2006-04-08
thanks, hope all is fine, spent too long learning how to do all my eye candy!  whats the word on uninstalling something, like evolution, while automatix is runing an install of frostbite?  any problems in doing the two at once?  I just dont want to wait around, eta for frostbite install is over 3 hours?  WTF

---

### Post by x5452 on 2006-04-09
:evil:  what the hell!!??!!  I just used synaptic to uninstall evolution and gnutella and install gtkpod, it said all changes made and you can close the box now.  Not only was evolution still in my process list taking up a lot of memory, but i rebooted to see if it would take effet, and after the ubuntu loading screen where it shows you whats loading ect.... it goes to a blank brown screen, with nothing but my damn penguin Icon hanging there waving at me!!!!??????  

what happened!!??:evil: :evil:

---

### Post by rama on 2006-04-25
[QUOTE=x5452]:evil:  what the hell!!??!!  I just used synaptic to uninstall evolution and gnutella and install gtkpod, it said all changes made and you can close the box now.  Not only was evolution still in my process list taking up a lot of memory, but i rebooted to see if it would take effet, and after the ubuntu loading screen where it shows you whats loading ect.... it goes to a blank brown screen, with nothing but my damn penguin Icon hanging there waving at me!!!!??????  

what happened!!??:evil: :evil:[/QUOTE]

Not sure but from the command line try 
sudo apt-get install ubuntu-desktop

---

### Post by gingermark on 2006-04-25
[QUOTE=dvarsam]_Question_:
How could somebody remove a package with the "dpkg -i xxxx.deb" command?
Is there a "dpkg -remove xxx.deb" command?
Thanks[/QUOTE]
The command is 'sudo dpkg -r xxx' I think.
But you can also use Synaptic to remove these packages.

---

### Post by user1397 on 2006-04-25
[quote=x5452]ok so I cant take it anymore, stupid evolution is just sitting there, not even set up anymore, taking up all kinds of ram performance. I am going to uninstall it through synaptic the same way i installed it.  But it tells me its going to remove all kinds of other stuff too like gnome desktop stuff, gdesklets stuff, why does it do this?  Is there a way to save what i have set up now in case it ruins it?  It took days to get it all set up, (with the help of most of you) id hate to see it all go just because evolution is a ram hungry Bi$%$[/quote]
It tells you that the ubuntu-desktop will be removed if you remove evolution, because evolution is one of the core packages that comes bundled with a fresh ubuntu install.  The ubuntu-desktop is dependent on all of the packages it contains, so remove one and it removes all! So my suggestion is- don't remove it!
Plus it's not gonna take up ram if it's not opened...

---

### Post by aysiu on 2006-04-25
[QUOTE=erik1397]It tells you that the ubuntu-desktop will be removed if you remove evolution, because evolution is one of the core packages that comes bundled with a fresh ubuntu install.  The ubuntu-desktop is dependent on all of the packages it contains, so remove one and it removes all! So my suggestion is- don't remove it![/QUOTE] Just to clarify a bit--removing a package *ubuntu-desktop* depends on does, in fact, remove *ubuntu-desktop* (which is nothing but a pointer, really). It does not, however, remove all the other packages *ubuntu-desktop* depends on... **unless** those packages all depend on the package you're trying to remove.

Let's look at some fake examples. Let's say *ubuntu-desktop* depends on packages A, B, and C being installed, and A and B themselves depend on C being installed.

If you remove A, only A and *ubuntu-desktop* will be uninstalled.

If you remove C, however, A, B, C, and *ubuntu-desktop* will all be removed.

Does that make sense or does it make it more confusing?

---

