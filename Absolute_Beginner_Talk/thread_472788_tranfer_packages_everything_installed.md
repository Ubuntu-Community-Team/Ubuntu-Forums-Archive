---
title: "tranfer packages everything installed"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by stonerrob420 on 2007-06-13
Hi! im building an ubuntu dapper system for a friend of mine who wants to give it a try....How can I transfer all the packages and dependencies that goes with them to a freshly installed ubuntu 6.06 LTS....basicly what I want to do is be able to_ transfer eveything I have installed on my system to his_...such as desktop managers games and applications....that way the system will be similar to mine and I can help them learn to use the system  That way wont have to do any downloading to get what they need. I've looked into harddrive cloning or mirroring but that seems to be to complex. :p

---

### Post by shearn89 on 2007-06-13
I have a feeling that if you open up synaptic, you can export the current state to a file, so then you could install dapper on his machine, and import the state from your synaptic...
I'll just check on my laptop.

edit:

just had a look. If you open synaptic, then click the "status" button and go to "installed". Then just mark all of them for reinstallation, and go [ file -> save markings ], and put it on a USB pen or something. You can then install dapper on his system, and go [ file -> read markings ] to copy on all of your packages. He'll then have almost exactly the same packages as you...

---

### Post by zvacet on 2007-06-13
[http://aptoncd.sourceforge.net/develop.html]("http://aptoncd.sourceforge.net/develop.html")

---

### Post by stonerrob420 on 2007-06-13
I took a different route in trying to solve my problem. I copied /var/cache/apt/archives/ from my computer too his but none of the applications showed up in the menus or seem to be installed....in sysnaptic they are listed...how do I get the applications to show up in the menus. how do I get the computer to use them? shouldn't that file have all the upgrades, updates and etc installed in it when i copied the folder?

---

### Post by zvacet on 2007-06-14
> I copied /var/cache/apt/archives/ from my computer too his

That is exactly what APTonCD do.You have packages in /var/cache/apt/archives/ but they are not installed.Before you start to install them put every Java package outside of  /var/cache/apt/archives/.Put them in any other directory(home for example).When you do that install packages

```
cd /var/cache/apt/archives/
```

and when you are inside

```
sudo dpkg -i *deb
```

Where all packages are installed put back Java packages in /var/cache/apt/archives/ and install them from synaptic.

---

### Post by stonerrob420 on 2007-06-14
Thank you for the help. I greatly appreciate it. I was wondering what I was missing or over looking. I looked all over the place to find a solution to this problem...... I'll post back if things go good or bad. Anyway its a learning experience I guess

---

### Post by stonerrob420 on 2007-06-14
It turned out good I guess......What I got was a edubuntu desktop with installed applications but not all of them. The kubuntu desktop didnt install and only Half of the desktop managers installed. They are not fully functional. The Xubuntu desktop works. The sysnaptic package manager says I have 248 updates to do..... I thought all the updates where stored in that file.. The system I coppied it out of was up to date. But at least i'm headed in the right direction with it. I guess its gonna be trial and error until I get it all figured out on how to do it. Is there any post in the forums that would show how to do this? Thanks for everybodies help. I'm gonna put this project on the back burner for a day or two until I do a little more reasearch on the subject.

---

