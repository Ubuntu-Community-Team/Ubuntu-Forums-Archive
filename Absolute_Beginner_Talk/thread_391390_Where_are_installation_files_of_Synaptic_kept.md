---
title: "Where are installation files of Synaptic kept"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Lightik on 2007-03-23
Can you help me. Once I download a packege from ubuntu repository with Synaptic, where does it put them. I want to use these downloaded files to install next time rather then to download a package again.

---

### Post by Bachstelze on 2007-03-23
/var/cache/apt/archives

But you shouldn't need to go see in there, since apt will automagically detect if a package is already in there when you want to install it and will reinstall from it instead of downloading it again.

---

### Post by Lightik on 2007-03-23
I use liveCD

---

### Post by az on 2007-03-23
Are you downloading them onto the live cd from a computer that has  a faster network connection?  A quick and easy way to do what you want is to save all of the .deb files in /var/cache/apt/archives/ and then install them on the other computer with

sudo dpkg -i *.deb

Running from the live cd, this should work fine.  If you do this from another ubuntu install it may not work, since the dependencies of one ubuntu install will differ from another which has different packages installed on it.  There are projects in work which are meant to help someone, say, running windows to download a package and all it's dependencies so that they can be installed on a non-networked Ubuntu machine.

---

### Post by Lightik on 2007-03-23
Thanks a lot for the advice, I'll try. Oh and I've got one more question then. What if download a package and all its dependencies with synaptic, then save all .deb files from /var/cache/apt/archives/ to flashstick for example, then reload PC. After that put all the saved files back to /var/cache/apt/archives/ and will try to find that program with synaptic. Will it find these saved files and install then or download files again.

If what HymnToLife said is true: "But you shouldn't need to go see in there, since apt will automagically detect if a package is already in there when you want to install it and will reinstall from it instead of downloading it again."

It should work. What do you say?

The reason of doing this: I don&#8217;t want to use console, it's easier to use graphical interface of synaptic.

---

### Post by zvacet on 2007-03-23
This can help you 
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

You are wrong.It is not easyer to use GUI,not in this case.First of all,how will you know from synaptic what is in your var/cache/apt/archives?Terminal is much easyer in this case,because you have to type just two commands:
1.cd /var/cache/apt/archives
2. sudo dpkg -i *deb

---

### Post by rabbi1337 on 2007-03-23
On a side note, does 'sudo apt-get remove XXXXX' remove it frome the cache folder?

---

### Post by kinematic on 2007-03-23
> **rabbi1337 said:**
> On a side note, does 'sudo apt-get remove XXXXX' remove it frome the cache folder?

no.
if you want to clear /var/cache/apt/archives use this command:
```
sudo rm /var/cache/apt/archives/*.deb
```

---

### Post by az on 2007-03-23
> **Lightik said:**
> After that put all the saved files back to /var/cache/apt/archives/ and will try to find that program with synaptic. Will it find these saved files and install then or download files again.

If what HymnToLife said is true: "But you shouldn't need to go see in there, since apt will automagically detect if a package is already in there when you want to install it and will reinstall from it instead of downloading it again."

It should work. What do you say?

.

Yes and no.  It will need to be connected to the repositories and get the dependency information there.  It will not re-download files which are already there, but it will not detect all the files in that folder and use them as if they were ready to go.  Apt (and synaptic) only use the repositories for that.

You can create a repository out of thoes efiles and add the local repo to your list:

[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)
[https://help.ubuntu.com/community/AptMoveHowto/simple](https://help.ubuntu.com/community/AptMoveHowto/simple)

> **rabbi1337 said:**
> On a side note, does 'sudo apt-get remove XXXXX' remove it frome the cache folder?

No.

---

### Post by tubasoldier on 2007-03-24
> **kinematic said:**
> no.
if you want to clear /var/cache/apt/archives use this command:
```
sudo rm /var/cache/apt/archives/*.deb
```

or the much easier and more efficient way is 
```
sudo apt-get clean
```

---

### Post by Lightik on 2007-03-25
Thanks for help!

---

