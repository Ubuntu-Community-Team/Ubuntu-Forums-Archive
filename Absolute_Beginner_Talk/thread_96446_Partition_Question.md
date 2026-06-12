---
title: "Partition Question"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by myke on 2005-11-28
Hi.  I'm getting enough of a handle on things now where I think I'll want to resize the win partition on my drive to free up some space for ubuntu.  According to synaptic, I already have the package 'parted' installed which would do what I want.  Unfortunately, my novice abilities have failed me.  It doesn't appear anywhere under the applications, places, or systems drop-down menus so I tried to create a simple launcher.  Unfortunately, my simple little launcher didn't work.  I put the command in as simply 'parted' which should work if that's it's proper name.  What should I do to remedy the situation??? 

Thanks ... ever so much ... once again ... for any help.

PS -- I hope I don't wear out my welcome with all of the rather low level questions!

---

### Post by gord on 2005-11-28
you can't wear out your welcome here, everyone is allways welcome :)

parted is the command line application, what you want is gparted.

sudo apt-get install gparted

it will then show up in your system tools :)

---

### Post by myke on 2005-11-28
Thanks for the quick response.  I ran it in the terminal correctly but something must be up with part of the unbuntu archives as it couldn't find the package in there.  This is the same thing that happened when I tried to install gparted thru synaptic.

---

### Post by gord on 2005-11-28
sounds like youv managed to mess up your sources list, there should be a copy of gparted on your install disk so throw that in and try again in synaptic, if its still not working disable all the repositorys apart from your cd repository (you might have to go into the preferences of the repository manager thingy) and try again.

---

### Post by aysiu on 2005-11-28
What's the outout of this command? ```
cat /etc/apt/sources.list
```

---

