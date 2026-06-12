---
title: "Program List Archiving"
date: 2013-05-26
forum: Assistive Technology &amp; Accessibility
---

### Post by cmb271 on 2013-05-26
My proposed idea isn't very resource intensive at most it would take about a dozen servers.

If for whatever reason a user wants to do a fresh install on a different computer and doesn't have a copy of each program name, the sources, and libraries this service I'm proposing would solve that. It will be linked with the Ubuntu Software Center and the user can optionally op in for a chance for a list of all there programs they have installed a copy of there version and name will be taken and stored on a server and the user will have a Login and Password, this makes life abit easier if they want to mass install all there old programs if the hardware goes Dx and they loose them and don't want to reinstall them one at a time. This also works if they have two or more computers and they want to have the exact same programs on both computer.

This doesn't save the program but it saves the name, version, dependencies names, sources, and libraries needed to run it and will auto install it when they are connected to the internet and they log in.

---

### Post by MG&amp;TL on 2013-05-26
> My proposed idea isn't very resource intensive at most it would take about a dozen servers.

I can't speak for anyone else, but that is what I would call resource-intensive. :P

> If for whatever reason a user wants to do a fresh install on a different computer and doesn't have a copy of each program name, the sources, and libraries this service I'm proposing would solve that.

It's a good idea, but I'm not sure why Canonical (I think this is who you're aiming this at) would need to support this: you can already do this manually yourself with a little bit of command-line (no doubt there is a GUI program somewhere to do it if you look hard enough):

```
dpkg --get-selections > some_file.txt
```

On the machine before a reinstall will produce a file you can backup with a list of installed packages.

After a catastrophic failure, you could then restore your backup of your list of installed packages, then install them all at once.

```
sudo dpkg --set-selections < some_file.txt
sudo apt-get -u dselect-upgrade
```

Although I can see where you're coming from, it would be handy if this got implemented.

---

