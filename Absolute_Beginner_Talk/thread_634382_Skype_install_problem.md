---
title: "Skype install problem"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by quantumdot on 2007-12-07
I have installed Ubuntu 7.10, and have downloaded the Ubuntu version of Skype. When I try to install, I get an error: Error: dependency is not satisfiable: libqt4-core (see attached for screenshot if I attached correctly.)

Any suggestions on what I should do? 

- Roger

---

### Post by wormser on 2007-12-07
That error is just telling you need to install libqt4-core before Skype can install.  It is usually best to install software threw the repositories either with Synaptic or with apt-get in the command line.  Dependant files will automatically be install this way.

System> Administration> Synaptic Package Manager and search for Skype.

or

Applications> Accessories> Terminal
```
sudo apt-get install skype
```

---

### Post by quantumdot on 2007-12-07
The sudo command can't find skype - I downloaded the debian package from the website and saved it in a folder - shoulkd that package be in a special location, or is there some way I should tell sudo where it is?

Sorry - I am entirely new at Linux....

- Roger

---

### Post by perce on 2007-12-07
It's strange because it should download the dependencies automaticly. Are you connected to the internet? if you are, you could install libqt4-core with:

sudo apt-get install libqt4-core 

in a terminal. If it doesn't work, a quick and dirty workaround is to download and install the skype tar.gz package with all library statically linked.

Btw, libqt4-core is in the repository, so if you're connected to the internet but you can't download it, then you should post your /etc/apt/source.list here.

---

### Post by wormser on 2007-12-07
> **perce said:**
> It's strange because it should download the dependencies automaticly. Are you connected to the internet? if you are, you could install libqt4-core with:

sudo apt-get install libqt4-core 

in a terminal. If it doesn't work, a quick and dirty workaround is to download and install the skype tar.gz package with all library statically linked.

That is strange it did not install the dependencies.  The only time I have seen that is when I am not online.

You probably need to open the repositories universe and multiverse.  System> Administration> Software Sources> Ubuntu Software tab and check universe and multiverse.  Now more software packages will be available to you.

---

### Post by quantumdot on 2007-12-07
Strange - I am connected to the Net - that's how I'm communicating with you folks. 

Your sudo command failed as well..." E: Couldn't find package skype" - to my untrained eye, looks like it is looking on a non-existent E drive.

I will go try to find the .gz for skype.

- Roger

---

### Post by wormser on 2007-12-07
> **quantumdot said:**
> Strange - I am connected to the Net - that's how I'm communicating with you folks. 

Your sudo command failed as well..." E: Couldn't find package skype" - to my untrained eye, looks like it is looking on a non-existent E drive.

I will go try to find the .gz for skype.

- Roger

Roger, I think it would be much easier for you to open the repositories then compiling Skype from source.  A repository is just a software library that installs the software for you.  It is the easiest way to install software I have ever seen.

System> Administration> Software Sources> Ubuntu Software tab and check universe and multiverse.  Now Synaptic should find the Skype package or you can run the apt-get command.

---

### Post by rsambuca on 2007-12-07
> **wormser said:**
> Roger, I think it would be much easier for you to open the repositories then compiling Skype from source.  A repository is just a software library that installs the software for you.  It is the easiest way to install software I have ever seen.

System> Administration> Software Sources> Ubuntu Software tab and check universe and multiverse.  Now Synaptic should find the Skype package or you can run the apt-get command.

Skype is NOT in the Ubuntu repositories.  It is not in multiverse, Universe, main, or restricted.

---

### Post by wormser on 2007-12-07
> **rsambuca said:**
> Skype is NOT in the Ubuntu repositories.  It is not in multiverse, Universe, main, or restricted.

My bad.  It is in the Medibuntu repository.  Directions to open it are [here]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f").

---

### Post by quantumdot on 2007-12-07
Added medibuntu link as described - it seems to have worked. Then ran sudo apt-get install skype, and it can't find skype. 

As a side note, the static package works, but it is ugly. Clearly not the right way to install an app. Shortcut is a launcher... etc. Not integrated. 

Side note 2: Synaptic still cannot see skype

I remain at a loss. Wait until I try to get gforth working! I'm sure I'll have more fun then too.

- Roger

---

### Post by wormser on 2007-12-07
You probably need to update apt-get.  Then search for the file.

```
sudo apt-get update
```

I recommend you browse threw this [site]("http://www.psychocats.net/ubuntu/index.php").  It will get you up to speed on the basics to Ubuntu.

---

### Post by quantumdot on 2007-12-08
OK, so I found the source of all of my problems.

When I first installed this version 7.10 off the CD, I did NOT have an internet connection. This morning I reinstalled 7.10 from scratch WITH a live network connection - big difference - had all sorts of immediate updates as part of the install, which I had NOT had before. 

I installed skype from the slype website (did not need to invoke medibuntu) and it worked like a charm.

SO: lesson learned - use a live connection when installing!

Thanks for all your help! Hopefully this will be helpful to others.

- Roger

---

### Post by perce on 2007-12-09
Probably you had the CD in sourse.list (this is why I asked you to post that file) it happened a couple of times to me. If that was the case, you could simply remove the disk from the source.list instead of reinstalling.

---

### Post by StephUb on 2007-12-09
I was running the 1.4 static but found recently the new version Beta 2.0
This version integrate and no more launcher...

I give here the link

[http://www.skype.com/download/skype/linux/beta/](http://www.skype.com/download/skype/linux/beta/)

---

