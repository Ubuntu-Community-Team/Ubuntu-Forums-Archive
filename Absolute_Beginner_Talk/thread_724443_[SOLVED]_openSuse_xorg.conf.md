---
title: "[SOLVED] openSuse xorg.conf"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-03-14
I just switched to openSuse from ubuntu and im having issues with the nVidia drivers.  I managed to install them just fine but when i run them im not able to save the xorg.conf file.  Obviosly its because i did not run it as root, but when i try to run nvidia-settings from root i get this:

```

titan@dungeon:~> sudo nvidia-settings

ERROR: The control display is undefined; please run `nvidia-settings --help`
       for usage information.

titan@dungeon:~>

```

Any help, im using KDE if that matters.

---

### Post by SOULRiDER on 2008-03-14
Not to flame or anything, but i think this thread would be better off in the openSuSE forums.

---

### Post by The Titan on 2008-03-14
> **SOULRiDER said:**
> Not to flame or anything, but i think this thread would be better off in the openSuSE forums.
thanks for the help.....

---

### Post by SOULRiDER on 2008-03-14
> **The Titan said:**
> thanks for the help.....

Dont get me wrong, Id like to help but Ubuntu and openSuSE are very different, they arent even based on the same distro!

Check this out:
[http://en.opensuse.org/NVIDIA](http://en.opensuse.org/NVIDIA)

---

### Post by Gepetto on 2008-03-14
try kdesu maybe?

---

### Post by The Titan on 2008-03-14
> **Gepetto said:**
> try kdesu maybe?
that did it thank you

---

### Post by xeth_delta on 2008-03-14
You could also try asking in this forum, but in the "Other OS -> OPenSuse" subforums. I am sure someone will be able to help you. By the other hand you might indeed get even more support in the OpenSuse forums, considering that is the distro you're using.

Good luck!

---

### Post by joshrobinson on 2008-03-14
in suse you want to use the su command alot

```
su
```
type in your root password
now you have a root terminal... i was a suse user for 3-4 years, i install it once and awhile to see how its developing, but its ususally got some issue that doesnt let it be my default system

---

### Post by The Titan on 2008-03-14
> **joshrobinson said:**
> in suse you want to use the su command alot

```
su
```
type in your root password
now you have a root terminal... i was a suse user for 3-4 years, i install it once and awhile to see how its developing, but its ususally got some issue that doesnt let it be my default system
i like it so far, its a little different lol.  Anyways its just that im trying to get used to KDE at the same time.

---

