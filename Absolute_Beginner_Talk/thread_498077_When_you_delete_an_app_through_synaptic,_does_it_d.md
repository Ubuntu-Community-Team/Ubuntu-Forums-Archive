---
title: "When you delete an app through synaptic, does it delete its dependent packages?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by forsberg on 2007-07-10
So I decided to try frostwire last night.  Went into synaptic, mark for installation, tells me I have to install about 5 other packages for this to work... ok, fine, click apply, and away we go.

Problem is frostwire is a POS.  Runs crazy slow on my 1.5mhz celeron laptop, so I want to delete it.

Went back into synaptic, mark for complete removal, and I noticed only the frostwire package is to be removed.  What about my other 5 packages it told me I needed before?

So the question is, when I delete something from synaptic, does it REALLY remove along with all the other packages that I don't need anymore?

---

### Post by Malibu Illusion on 2007-07-10
No.

This is why some people use the "Aptitude" frontend.  For example:

To install: 
```
sudo aptitude install frostwire
```

Remove package, and dependancies:
```
sudo aptitude remove frostwire
```

The apt-get frontend in Ubuntu only includes a similar function.

```
sudo apt-get autoremove
```

That attempts to remove dependencies of packages that no longer exist.

---

### Post by forsberg on 2007-07-10
> **Malibu Illusion said:**
> No.

```
sudo apt-get autoclean
```



I will give that a try.  Thanks!

Is it generally a good practice to use aptitude instead of apt-get to remove a package?

---

### Post by FuturePilot on 2007-07-10
```
sudo apt-get autoremove
```
That will remove any dependencies that are no longer needed.

---

### Post by forsberg on 2007-07-10
huh?  so is it autoremove or autoclean?

---

### Post by Papi-KB7VGW on 2007-07-10
I'm confused here.  I am under the impression that synaptic is the gui for aptitude and that they both look at dependencies.  Add-remove and apt-get are they same and don't keep track as well as they should.  How badly am I mistaken?     :confused:

---

### Post by regomodo on 2007-07-10
i use both autoremove and autoclean, in that order. Seems to be ok

@papi. That's how i see it

---

### Post by pistcivet on 2007-07-10
You can also click on "File" --> "History" in Synaptic.
There you can get the names of those 5 dependencies you installed,
and remove manually.  :)

Not a very elegant solution. Best you can do at this point.

---

### Post by FuturePilot on 2007-07-10
> **forsberg said:**
> huh?  so is it autoremove or autoclean?
autoclean will actually clear your apt cache out. It's a way to remove all the cached packages to free up some disk space. Doesn't have anything to do with dependencies.

> **Papi-KB7VGW said:**
> I'm confused here.  I am under the impression that synaptic is the gui for aptitude and that they both look at dependencies.  Add-remove and apt-get are they same and don't keep track as well as they should.  How badly am I mistaken?     :confused:

Synaptic is the front end to apt-get and so is Add-Remove. Neither use aptitude though. But they do handle dependencies, it's just that certain ones don't get removed with apt-get so you have to use the autoremove feature.

---

### Post by forsberg on 2007-07-10
> **Papi-KB7VGW said:**
> I'm confused here.  I am under the impression that synaptic is the gui for aptitude and that they both look at dependencies.  Add-remove and apt-get are they same and don't keep track as well as they should.  How badly am I mistaken?     :confused:

My understanding is (btw I am a total linux n00b) is that synaptics is the front-end to apt-get, which apparently is different than aptitude, but both just look at the same repositories

---

### Post by Papi-KB7VGW on 2007-07-10
thanks regomoto :)   hope i remembered to sp. correctly  CRS ya know

---

### Post by macogw on 2007-07-10
> **Malibu Illusion said:**
> No.

This is why some people use the "Aptitude" frontend.  For example:

To install: 
```
sudo aptitude install frostwire
```

Remove package, and dependancies:
```
sudo aptitude remove frostwire
```

The apt-get frontend in Ubuntu only includes a similar function.

```
sudo apt-get autoclean
```

That attempts to remove dependencies of packages that no longer exist.

I'm being told on #ubuntu that the thing about aptitude having better dependency handling is flat-out wrong, so could you please point me to a reliable (no blogs, official documentation only) source stating that this is the case?

EDIT: was just informed that back in 2005 you would've been right.  Back then, apt-get didn't handle dependencies on removal, only aptitude did.  This is no longer the case.

---

### Post by Malibu Illusion on 2007-07-10
Okay, firstly ignore autoclean.  I meant to put autoremove.  I've since corrected that.

Aptitude doesn't have "better dependancy handling", it just tracks which dependancies were installed for removal at a later time with aptitude remove, that's all.

apt-get doesn't "track" dependancies; it just removes the ones that are not required as determined by it.  Aptitude stores more information about what is installed during the install operation.

Suggest googling on the terms if you're looking for more information.

---

### Post by macogw on 2007-07-10
autoclean is for clearing out your /var/cache/apt/ to get rid of old debs taking up hard drive space, in case anyone is going to wonder what the reference to autoclean/autoremove was

sudo apt-get autoremove $package
behaves the same as 
sudo aptitude remove $package
nowadays

---

### Post by Papi-KB7VGW on 2007-07-10
searched on the wiki and found this:  //usr/share/synaptic/html/index.html  It states that synaptic is based on apt-get.  Aptitude is a totally separate pkg mgr...  That certainly helps clear up my muddy mind.

---

### Post by Malibu Illusion on 2007-07-11
I've Google'd myself.  [This](https://help.ubuntu.com/community/AptGetHowto) is the non-tech howto re: apt/package management.  This is all it has to say on Aptitude:

> aptitude - Curses viewer of packages installed or available. Aptitude can be used from the command-line in a similar way to apt-get, but only for some commands - install and remove being the most common. However, because aptitude keeps track of more information than apt-get does, it can be considered better at install and remove operations.

Aptitude is the official method of installation recommended by Debian developers; I've personally used it since the start.  apt-get has come a little way with its removal of redundant dependencies, admittedly, but Aptitude still has advantages in other areas.

Either way, both function in a similar fashion but go about things in different ways under the hood.  I'd personally use whichever is most comfortable, natural and works best for you.

---

### Post by regomodo on 2007-07-11
> **macogw said:**
> autoclean is for clearing out your /var/cache/apt/ to get rid of old debs taking up hard drive space, in case anyone is going to wonder what the reference to autoclean/autoremove was

sudo apt-get autoremove $package
behaves the same as 
sudo aptitude remove $package
nowadays

yep. I don't use aptitude so that's why i use autoremove

---

