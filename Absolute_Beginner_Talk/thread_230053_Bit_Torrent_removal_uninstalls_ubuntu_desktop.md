---
title: "Bit Torrent removal uninstalls ubuntu desktop?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Stew2 on 2006-08-05
I was in Synaptic to uninstall bit torrent, however when I selected it for removal it also selected the ubuntu desktop. I tried to deselect the ubuntu desktop but it would not let me. Why are these two apps linked? :confused: 
Thanks for the help!

Regards,
Stew2

---

### Post by Indras on 2006-08-05
ubuntu-desktop is a meta package.  Basically, it just contains a list of programs that comes on a default install of Ubuntu.  All of these programs within the package are its dependancies, so removing any of the pieces of it requires that you remove the ubuntu-desktop meta package as well.  Since it is just a list of programs, and not a program itself, it can be removed without affecting your system at all.

---

### Post by Stew2 on 2006-08-05
> **Indras said:**
> ubuntu-desktop is a meta package.  Basically, it just contains a list of programs that comes on a default install of Ubuntu.  All of these programs within the package are its dependancies, so removing any of the pieces of it requires that you remove the ubuntu-desktop meta package as well.  Since it is just a list of programs, and not a program itself, it can be removed without affecting your system at all.

So bit torrent is a dependancy of the ubuntu desktop and can't be removed then? Kind of make sense as I don't recall installing bit torrent. But why is bit torrent so important?

Regards,
Stew2

---

### Post by Indras on 2006-08-05
It's not important, per se, it's just a dependency in order for you to have a complete ubuntu desktop (which is chosen by the developers).

You can remove bittorrent without affecting anything, since it will just remove the ubuntu-desktop package, which is empty anyway.  It won't remove all the other stuff that comes with ubuntu, since there aren't any packages that depend on ubuntu-desktop.

Let's put it this way: the ubuntu-desktop package is a blue print on how to build a ubuntu system.  If you choose to make a change to your system, by removing something that is in the blue print, then the blue print must be thrown out because it is no longer valid.  However, the process of throwing away that blue print does not affect your system any more than throwing away your owner's manual for your car would affect the car.

---

### Post by aysiu on 2006-08-05
*ubuntu-desktop* is safe to be removed. As Indras said, it's merely *defined* as the default programs.

So, by definition, if you remove one of the default programs, you remove the *ubuntu-desktop* pointer (it's not a real package--just a metapackage).

It's sort of like if you had a big label on a six-pack of beer that said, "Six-pack of beer." Well, if you remove one of those cans of beer, that label no longer applies, but you still can drink the beer just fine. All the cans are okay to use.

---

### Post by Stew2 on 2006-08-05
:D  Okay, I got it now :D  Thank you for the explanation. I just didn't understand that I could uninstall the ubuntu desktop and still have a desktop (as in the gui). Thanks! 

Regards,
Stew2

---

