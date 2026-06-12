---
title: "Downloading"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by danl9x on 2007-07-29
Is there an art to installing a download? Can't seem to figure this one out. Says it's for Ubuntu but can't do anything with it. Any suggestions?

---

### Post by Moop on 2007-07-29
It would help if you told us what you were trying to install. Here is a good guide to installing programs in Ubuntu. 

[http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware")

---

### Post by danl9x on 2007-07-29
Does it really matter what I've downloaded to install it? A dl is a dl.

---

### Post by Atomic Dog on 2007-07-29
> **danl9x said:**
> Does it really matter what I've downloaded to install it? A dl is a dl.

That kind of unhelpful response will not gain you any favors.  How about answering the question so we can help you?  Like I went here:  [www.site..com](www.site..com) and downloaded blabla.deb or fooprog.tar.gz or whatever so we can look at it.

---

### Post by danl9x on 2007-07-29
Not being a smartass like the last post, but I don't want to ask about a dl everytime I want to install something.

---

### Post by Raptor45 on 2007-07-29
> **danl9x said:**
> Not being a smartass like the last post, but I don't want to ask about a dl everytime I want to install something.

Are you trying to start a flamewar or something? Jeez...

Its hard to help if we don't know what you're trying to do. Did you download a .deb? .rpm? The source code?

---

### Post by panther_sn on 2007-07-29
Ok well I will see if I can help with no details, if it is a .deb file so something like program.deb, just open nautilis or what ever your computer browser is find where you put the file and double click the file. Should install.

Now if it is something like program.tar.gz that is more difficult I do this by righ clicking on the file and selecting Extract here. then see if there is a readme file and I read these instructions, but for any program I always try 
```

sudo apt-get install programname 

```
first anyway. 
 Hope that helps, also sometimes it is worth just searching the forums here for the program name, to see if any1 else has asked for help regarding that program

---

### Post by Atomic Dog on 2007-07-29
> **Raptor45 said:**
> Are you trying to start a flamewar or something? Jeez...


I suspect this might be his goal.  Being a bit too evasive.  plonk: on

---

### Post by danl9x on 2007-07-29
Yes, when I extract the dl a bunch of files open and I can't do anything with them. If it's this difficult I'm giving up on ubuntu , sorry for the inconveinance. Just disregard this post I'm over it.

---

### Post by chewearn on 2007-07-29
Most of the time, installing software in Ubuntu means:
If you like GUI:
Applications > Add/Remove
or
System > Administration > Synaptic Package Manager

If you don't mind CLI:
sudo aptitude install [I]somestuff
[/I]

On rare occasions, the application you like does not exist in the repositories, then you download the .deb file, which must specifically be for Ubuntu.  (Note: I have no experience what will happen if you take a .deb for, say, Debian; will it still work or not)

Then, you simply double-click on the .deb file from Nautilus; the Package Manager (or some such) will pops-up; click on the install button, and you are done.

On even rarer occasions, you don't get a .deb file, then you take the source code and compile it yourselves.  Never have a need to do this myself, so can't comment about it.

Finally (I think), you can might also find/download scripts, which automate the installation for you (e.g. Envy Script to install nvidia or ati drivers).

---

### Post by Raptor45 on 2007-07-29
> **danl9x said:**
> Yes, when I extract the dl a bunch of files open and I can't do anything with them. If it's this difficult I'm giving up on ubuntu , sorry for the inconveinance. Just disregard this post I'm over it.

Can you please stop being so vague? A link or specific information would be very helpful.

From that it sounds like you're downloading the source code. It probably has a .tar.gz extension? If this is the case, you will have to build the software yourself. Doing so can be either very simple, or can get more complicated if things don't work right.

This may not be necessary however, if you would just let us know what you're trying to do. Most things can be found in the repositories, and so wouldn't require you to build it yourself.

---

### Post by danl9x on 2007-07-29
So it has to be a .deb file or it won't work? Thanks for the info.

---

### Post by Raptor45 on 2007-07-29
> **danl9x said:**
> So it has to be a .deb file or it won't work? Thanks for the info.

No, thats not true. Nobody said that.

Source can be built. RPM''s can be convert via alien. Etc.

Basically any linux software should work in Ubuntu, albeit with various level of complications.

---

### Post by livingtarget on 2007-07-29
> **danl9x said:**
> So it has to be a .deb file or it won't work? Thanks for the info.

The .deb file is native to ubuntu and debian. These work best with these distributions and are by far easiest to install. Basically it's just a point-click install progress. You download the .deb file and double click it to install.

The .rpm file is a file for Fedora/RedHat it can be installed but it's a bit advanced. Just stick to .deb files.

The .tar.gz file is basically a zip file and usually needs to be compiled by reading the "INSTALL" file, if compiling and source code mean nothing to you then it's probably best not to use this method.

I'd recommend to load up Add/Remove programs and you can find a lot of applications in there. It's not always necessary to browse the net to find the programs. These programs are usually included by ubuntu and can be freely downloaded.

If you are looking for a specific download please point us to what you are trying to download -or- what kind of program you want i.e.: a program to edit video for example.

Hope that helps.

---

