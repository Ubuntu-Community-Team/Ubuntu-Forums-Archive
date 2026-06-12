---
title: "Problem with Source Install (WordNet 2.1)"
date: 2005-09-06
forum: Absolute Beginner Talk
---

### Post by mousepad on 2005-09-06
Converted to Linux today and it's my first time using it so please bear with me.  I am using ubuntu 5.04 on an ibm t42.

I think I am actually over the hardest part of installing from a source file.  I extracted the tar file, but in order to configure WordNet2.1 I was required to get the gcc compiler, tcl, and tk. I tried using apt-get build-neccesary which didn't help much because configure didn't recognize anything.  Manually apt-get gcc worked fine, but I still needed tcl and tk.  Synaptic shows that I have v8.4 of both tcl and tk, but unfortunately configure for Wordnet2.1 still had fits about those compilers.  So, I had to compile tcl and tk source v8.4.11 and configure/make/make installer finally worked for WordNet2.1.  

Now, the problem.  Under /usr/local/WordNet-2.1 there are many other folders, but I can't figure out how to execute the problem.  Ideally, I would like to have a WordNet Icon show up under applications/accessories. Folders under WordNet-2.1 include bin, dict, doc, include, lib, man.  The only thing that seems remotely executable is "wn" (MIME type: application/x-executable) in bin, but when I double click it nothing happens.  If necessary I can post all other sub files/folders.

Please help me get this program to run.

---

### Post by rpgcyco on 2005-09-06
It's actually build-essential. May be worth installing it now, anyway.

When a configure script is looking for a library (tcl for instance), it usually wants the development packages. For tcl, this is tcl8.4-dev.

```
sudo apt-get install tcl8.4-dev
```

Same with tk.

```
sudo apt-get install tk8.4-dev
```

I'm wondering if you know about the existence of Synaptic? It's a point and click front-end to apt-get. Should be under System -> Administration -> Synaptic Package Manager.

I've also noticed that wordnet is available in the repos. If your prepared to settle for a slightly older version, then you can just install it using the above mentioned Synaptic, or by typing in a terminal:

```
sudo apt-get install wordnet
```

Never-the-less, it seems you've now got it compiled. You should be able to run it by opening a terminal and typing **wordnet**. As for creating a link to it, you can add a custom launcher to the panel relatively easily. Right click on a panel, select add to panel, then custom application launcher and fill out the fields.

However, adding a launcher to the menu is a whole different story. GNOME 2.10 does not come with a menu editor, so you either have to follow [this HOWTO](http://www.ubuntuforums.org/showthread.php?t=61713) or enable the backport repos ([see here](http://www.ubuntuguide.org/#extrarepositories)) and then install [Smeg](http://www.ubuntuguide.org/#menu-editor).

Sorry to chuck so much info at you!

- Rpg Cyco

---

### Post by mousepad on 2005-09-06
Thanks for the quick response. Okay, where to begin (ah, the joys of learning a new system).  I actually meant to type build-essential and I did obtain it through synaptic. 

I am kicking myself because I spent hours installing something that could've taken minutes.  Figuring out how to compile tcl and tk when I could've just used their dev packages? DAMN IT!  

Worst of all WordNet already appears on synpatic through a quick search MOTHERFSKER ](*,)  Lesson learned, search synaptic before compiling source just in case.  Just wondering, I added the repositories mentioned at ubuntuguide.org, are there any other major/minor ones that I should add?

---

### Post by mousepad on 2005-09-06
I tried typing wordnet in the terminal and receive the error:

> bash: wordnet: command not found 

I'm going to try running my compiled version of wordnet a little longer before giving up and using synaptic.

---

### Post by rpgcyco on 2005-09-06
> I am kicking myself because I spent hours installing something that could've taken minutes. Figuring out how to compile tcl and tk when I could've just used their dev packages? DAMN IT!

As you said, it's the joys of learning a new system. :D I did a similar thing when I first started last year. I compiled Beep Media Player from source, when there was a package right in front of me. :D

> Worst of all WordNet already appears on synpatic through a quick search MOTHERFSKER

Yeah. :) As I said though, it may be a bit older then the latest publicly available version, due to Ubuntu's no updates after release policy, except for security fixes. The upside of this is, that no instability should creep in. (Keyword: should).

> Just wondering, I added the repositories mentioned at ubuntuguide.org, are there any other major/minor ones that I should add?

The repositories there are fairly complete, though they are still using the older unofficial backports repository, because the [new official repositories](http://www.ubuntuforums.org/showthread.php?t=52168), do not contain all the backports the old ones do. It is safe to have both in there though, which means the best of both. :)

> I tried typing wordnet in the terminal and receive the error:

Yeah, sorry. :) That was a logical guess at the executable name. Check the README file in the source archive, it may have instructions on how to run it. You've probably already looked though. :)

If not, every program installed from the repositories create their own menu entries (I say every, meaning every program I have installed).

- Rpg Cyco

---

