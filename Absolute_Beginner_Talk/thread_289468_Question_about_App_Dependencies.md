---
title: "Question about App Dependencies"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by anguste on 2006-10-31
I wanted to remove some applications which I never use, i.e. Ekiga Softphone, Evolution Mail, etc. 

But when I chose to "Remove" or "Complete Remove" them from the Synapatic Package Manager, the manager told me that I would have to remove also the "gnome", "gnome-desktop-environment" etc.

I think it's quite wierd to see this kind of "dependencies". How can I remove applications regardless of dependencies (simply gnome will not depend on Ekiga to run, I guess...) ?

Thanks in advance!

---

### Post by aysiu on 2006-10-31
Are you sure it's not trying to remove *ubuntu-desktop*?

That's just a metapackage (a package that points to other packages and is safe to remove) pointing to all the default packages in Ubuntu. Obviously, if you don't have the default packages installed any more, you can't have that pointer installed either.

---

### Post by anguste on 2006-10-31
> **aysiu said:**
> Are you sure it's not trying to remove *ubuntu-desktop*?

That's just a metapackage (a package that points to other packages and is safe to remove) pointing to all the default packages in Ubuntu. Obviously, if you don't have the default packages installed any more, you can't have that pointer installed either.

Does it mean that I'm not able to remove a single item if my Gnome is installed as a metapackage by default?

---

### Post by aysiu on 2006-10-31
> **anguste said:**
> Does it mean that I'm not able to remove a single item if my Gnome is installed as a metapackage by default?
No. It means you can't have the label "all default packages" if you want to remove one of those default packages. But *ubuntu-desktop* is just a label. It isn't a real package.

It'd be like having a box that said "Six-pack of beer." Once you remove one of those beer cans, it's no longer a six-pack of beer. It's a five-pack. But those other five cans are still completely valid.

Ubuntu will still function fine without that label, but it's recommended you keep it for easier upgrade transitions (from Dapper to Edgy or Edgy to Edgy+1). This is the Synaptic Package Manager description: > The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed. Are you hard-up on hard drive space?

---

### Post by anguste on 2006-10-31
Thanks for the reply. 

I'm a total rookie for Linux so there are some concepts which are not so easy for me to understand...

However a freaking fact is that, when I accept the "Complete Removal", the Synaptic Package Manager DOES remove gnome also... which means after restarting the computer I'm not able to see any GUI..

I'm not keen on saving disk space but some not-so-useful applications always remain in the gnome applications menu, which makes me uncomfortable... =P

---

### Post by aysiu on 2006-10-31
Try right-clicking the applications menu and then using the menu editor to remove those applications from the menu--they'll still be installed but won't be visible.

---

### Post by anguste on 2006-10-31
Surely it works but it's a cheat-myself way...

---

