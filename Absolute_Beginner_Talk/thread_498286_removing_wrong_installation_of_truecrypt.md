---
title: "removing wrong installation of truecrypt"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by girard on 2007-07-11
Hi. I made the stupid mistake of install truecrypt that was still for 6.10. I have 7.04 now. I was also going to install forcefield after i got the right version so i removed the old truecrypt. the problem is that the folder after installing the deb package is stuck on my Desktop. :)

i tried to rm it but it said i cannot access it because it's a directory. how should i go about this?

did i even have to remove the old version to install the new one? thanks.

---

### Post by shearn89 on 2007-07-11
you can "rm" it with the command "rm -r <folder>", which just makes it remove the folder recursively. I imagine you would have to install the old one, but you can always try to install the new one and see what happens. You may end up with some random unused files, but i don't think it would harm your system in any major way.

---

### Post by mali2297 on 2007-07-11
You can uninstall a deb package and remove all of its trace with
```

sudo dpkg --purge package_name

```
Another alternative is to use synaptic.

---

### Post by girard on 2007-07-11
oh you posted ahead of me... i was trying to save myself from the embarrassment that it was a basic linux command i needed to execute. got it off the Desktop now. 

but reading your post made think now. i believe i successfully uninstalled it. could it have been possible that the directory was a residue of some sort? or does its existence mean that the process of uninstallation was not successful. no errors, or unwanted messages were brought up during the uninstall process, so i thought all went well except for that dir.

is there a way to check for left-overs in linux. somewhat like how CCleaner functions in Windows?

EDIT: i know autoremove, autoclean, clean... but is that all there is to it?

---

### Post by girard on 2007-07-11
> **mali2297 said:**
> You can uninstall a deb package and remove all of its trace with
```

sudo dpkg --purge package_name

```
Another alternative is to use synaptic.

that's what i did. i wonder why that dir was left behind. oh i think i did dpkg -P

is there a difference there

found truecrypt in synaptic... boy that was much easier... although it feels good have been able to install from the terminal (albeit the wrong one... )

---

### Post by mali2297 on 2007-07-11
From the dpkg man page:
```

&#8722;P or &#8722;&#8722;purge removes everything, including configuration files

```
...so it should do the same.

By the way, is truecrypt working for you? 

I had to compile from source to get it to work, but it may have been unnecessary.

---

