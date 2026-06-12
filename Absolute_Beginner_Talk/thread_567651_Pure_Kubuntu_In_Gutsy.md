---
title: "Pure Kubuntu In Gutsy"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-10-04
I was originally running Ubuntu Gutsy. I switched to Kubuntu and I love it. How can I remove all the Ubuntu packages. I removed ubuntu-desktop, but it didn't get rid of gnome programs. 

What can I do?

---

### Post by RomeReactor on 2007-10-04
Hi. You might [try this]("http://www.psychocats.net/ubuntu/purekde").

---

### Post by tdrusk on 2007-10-04
eh new programs in Gutsy.

---

### Post by RomeReactor on 2007-10-04
Did you try it, and if so, how many applications were left installed? if not many, I suggest you **completely uninstall** them through Adept--or Synaptic, if you wish to leave it installed--and then run:
```
sudo apt-get update
```
and
```
sudo apt-get autoremove
```

Although, since it's still a beta release, there *could* be some breakage.

---

### Post by tdrusk on 2007-10-04
Didn't work. It didn't remove anything.

If I go to aptitude, search for gnome, and remove them all will that work?

---

### Post by RomeReactor on 2007-10-04
I've never tried that approach; you could go for it, I don't think it will cause any problems--and it could be the solution you're looking for.

---

### Post by ravenwere on 2007-10-04
Also remember you will also have to remove your configuration files with the purge option eg```
 sudo aptitude purge *package name*
```

or

```
sudo apt-get --purge remove *package name*
```


Whether you can remove all the gnome libraries depends on what applications you want to run. eg Beagle will install many of the gnome libraries by default.

Running "pure" kubuntu sounds a little ideological to me. Gnome has a better reputation for applications to play media. K has the better burning application in K3b (my opinion). K is a little lighter on resources. I prefer the k environment but be prepared to be flexible. GParted is a good application to hang onto.

---

### Post by tdrusk on 2007-10-05
So does anyone know a command that can get me back to pure kde?

---

### Post by TeaSwigger on 2007-10-05
RomeReactor did post a link to psychocats.net, where you'll find the command. Not the short command on top of the page, odds are; the looooooooooooong one further down. It does work, I've used it myself.

---

### Post by tdrusk on 2007-10-05
> **TeaSwigger said:**
> RomeReactor did post a link to psychocats.net, where you'll find the command. Not the short command on top of the page, odds are; the looooooooooooong one further down. It does work, I've used it myself.

Yes, but that's for Feisty, not Gutsy.

---

### Post by rickycodie on 2007-10-05
try 
sudo apt-get autoremove --purge ubuntu-desktop

that shoud work i think

EDIT; the psychocats long command should work even though it's gusty.

---

### Post by tdrusk on 2007-10-07
> **rickycodie said:**
> try 
sudo apt-get autoremove --purge ubuntu-desktop

that shoud work i think

EDIT; the psychocats long command should work even though it's gusty.

It works. Awesome, thanks!

---

