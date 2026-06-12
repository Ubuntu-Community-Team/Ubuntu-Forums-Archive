---
title: "Ubuntu has decided to be irksome."
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-03-05
Okay. This is how it's going:

Gaim doesn't work. It completely exits after a second of signing in. AMSN does the exact same thing. So, somebody suggested I use kopete instead. So I downloaded kopete. I try to compile it. but I didn't have gcc installed, or kde. So I install both of these things, and it gets quite far, but after a while, it tells me that "in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!"
So, I posted here to see what could be done, and so I was told to try installing "kubuntu-desktop" and see if that helped. So, I go to System > Administration > Synaptic Package manager, but for some absolutely tiresome and stupid reason that I can not figure out, I click on "Synaptic package manger" but absolutely nothing happens. It just does nothing. I've tried restarting.

So, I want to be able to run Synaptic package manager, so I can install "kubuntu-desktop" so I can compile Kopete, so I can then install Kopete, because Gaim doesn't want to work, AMSN doesn't want to work, and frankly so far I'm disappointed in Ubuntu. Maybe I should go back to the dreaded "Windows" with it's painfully long startup and annoying error messages. Because Ubuntu has so far just given me a headache becasue absolutely NOTHING IS WORKING!!!

Okay, how do I get Synaptic package manager to work?

Any help would be appreciated.

---

### Post by taurus on 2007-03-05
Open a terminal, Applications -> Accessories -> Terminal, and run these two commands.  Post the outputs here.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Neon_Knight on 2007-03-05
```

david@david-desktop:~/Desktop/Random_junk/kopete-0.12.2$ sudo aptitude update
sudo: must be setuid root
david@david-desktop:~/Desktop/Random_junk/kopete-0.12.2$ sudo aptitude upgrade
sudo: must be setuid root

```

---

### Post by taurus on 2007-03-05
What's the output of this command from a terminal?

```
id
```

---

### Post by Neon_Knight on 2007-03-05
```

david@david-desktop:~$ id
uid=1000(david) gid=1000(david) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(david)

```

---

### Post by Neon_Knight on 2007-03-05
>_>
<_<

---

### Post by j.miller565 on 2007-03-05
try:

```
sudo -H -s
```

Then try:

```

sudo aptitude update
sudo aptitude upgrade
```

hopefully it works now

---

### Post by Neon_Knight on 2007-03-05
```

david@david-desktop:~$ sudo -H -s
sudo: must be setuid root

```

this doesn't seem to be going well...do I have to reinstall Ubuntu AGAIN?

It doesn't appear to like "sudo".

---

### Post by taurus on 2007-03-05
Did you play around with either permissions or make changes to /etc/sudoers?

---

