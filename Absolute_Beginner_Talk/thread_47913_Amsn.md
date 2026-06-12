---
title: "Amsn"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by Snitz on 2005-07-10
I, honestly didn't like the Gaim Internet Messenger
is there a version of AMSN that works with ubuntu?
I went to their site but didn't know which file to download
plz help!

---

### Post by Leif on 2005-07-10
Start synaptic, search for amsn and install it. Alternatively, type this into a terminal "sudo apt-get install amsn".

---

### Post by Snitz on 2005-07-10
[QUOTE=Leif]Start synaptic, search for amsn and install it. Alternatively, type this into a terminal "sudo apt-get install amsn".[/QUOTE]
 I tried the command u gave me and nothing happened
I searched for amsn on synaptic but it found nothing
that's why I made this topic

---

### Post by Leif on 2005-07-10
Have you enabled universe, multiverse etc ? [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Snitz on 2005-07-10
I didn't know i had to do this
I just did it, and it's downloading packages in a Terminal window
when it's done, i'll be able to download amsn and other stuff from synaptic?

---

### Post by Snitz on 2005-07-10
the download in the terminal has finished
I opened up synaptic and I got this error

```
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
```

but I searched for amsn and im downloading it now, it asked me to insert ubuntu CD, is this normal?

---

### Post by Leif on 2005-07-10
Are these the lines for the backports in your sources.list :

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

If so, it's probably a temporary problem. Try doing sudo apt-get update again. You can also try using a different mirror for the backports, they are listed at [http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php)

As for the CD, you can stop this by commenting out (with #s) the corresponding lines at the top of your sources.list file.

---

### Post by Williams477 on 2005-07-10
Or just update them in the Package manager, it's much easier.

---

### Post by imoas83 on 2005-07-13
I'm new in Linux...  :smile: 

I have correctly installed aMSN, but it Freeze when I log in...  ](*,) 

I'm under Firewall...   :-|  

If someone know how to fix this problem, please reply to me!!!

Thanks to all and sorry for my english...  :-#

---

### Post by SteExp on 2005-07-13
i try amsn, gaim, kopete, but... the best program is GAIM.
You can belive in me ;)

with kopete i can't send file... and sometimes... disconnect without reason...
amsn... don't like the skin...
GAIM is better

---

