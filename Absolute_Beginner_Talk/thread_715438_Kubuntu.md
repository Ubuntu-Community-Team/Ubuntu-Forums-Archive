---
title: "Kubuntu"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-04
I just installed it and i don't think i like it...
haha
i like the menus and such but i really feel like it runs slower on my laptop.
not slow
just slower
so yeah not really any problems with it
just taught i'd say i think i'm going to switch back
i'm used to regular ubuntu now
and i really don't think i'm ready for another change.
:lolflag:

---

### Post by JoshuaRL on 2008-03-04
Thats cool man, thats what Linux is all about.  Choice.

You remember how to uninstall if you want to right?

---

### Post by RadiationHazard on 2008-03-04
haha. no? i didn't know that you could?
i always just install over?

---

### Post by kool_kat_os on 2008-03-04
> **JoshuaRL said:**
> Thats cool man, thats what Linux is all about.  Choice.

You remember how to uninstall if you want to right?

I hope he knows how to uninstall it :-)...thats a trick business...if not careful

---

### Post by kool_kat_os on 2008-03-04
> **RadiationHazard said:**
> haha. no? i didn't know that you could?
i always just install over?

uh...

---

### Post by RadiationHazard on 2008-03-04
either that of i use one of my disks to whip my drive...
haha
are those both bad?
:(

---

### Post by neurostu on 2008-03-04
did you install Kubuntu over Ubuntu, or did you install KDE?

If you want to go back to Ubuntu without re-installing you can install gnome by:
```

sudo apt-get install gnome

```
Then when you login click on the options button in the bottom left, then click session (or something like that) and select gnome! 

Then you'll be back to regular ubuntu w/o a reinstall

---

### Post by JoshuaRL on 2008-03-04
Well RadiationHazard, it all depends on how you installed it.

If you followed the steps from the other thread, you can do:
```

sudo aptitude remove kubuntu-desktop

```

Aptitude can remove not only the metafile, but all the dependencies that were installed at the same time.  That is, if you used it to install.

---

### Post by JoshuaRL on 2008-03-04
> **neurostu said:**
> did you install Kubuntu over Ubuntu, or did you install KDE?

If you want to go back to Ubuntu without re-installing you can install gnome by:
```

sudo apt-get install gnome

```
Then when you login click on the options button in the bottom left, then click session (or something like that) and select gnome! 

Then you'll be back to regular ubuntu w/o a reinstall

Well, that may be gnome.  But it wont be "Ubuntu" as we're used to.  All the art and specific stuff to Ubuntu is under **ubuntu-desktop**.

Same for Kubuntu, Xubuntu, and Mythbuntu.

---

### Post by kool_kat_os on 2008-03-04
> **JoshuaRL said:**
> Well RadiationHazard, it all depends on how you installed it.

If you followed the steps from the other thread, you can do:
```

sudo aptitude remove kubuntu-desktop

```

Aptitude can remove not only the metafile, but all the dependencies that were installed at the same time.  That is, if you used it to install.

if he removed the desktop...whats left?

---

### Post by JoshuaRL on 2008-03-04
> **kool_kat_os said:**
> if he removed the desktop...whats left?

Well, he had another thread about how to try out other DEs.  So I suggested there to use aptitude so he could keep his optimized OS.  So he should have ubuntu-desktop still.  That is, if he didn't do a fresh install.

---

### Post by RadiationHazard on 2008-03-04
i installed it from the actual disk
haha
i'm just going to install over what i already have
i don't think that's bad?
it's always worked fine so far...

---

### Post by JoshuaRL on 2008-03-04
> **RadiationHazard said:**
> i installed it from the actual disk
haha
i'm just going to install over what i already have
i don't think that's bad?
it's always worked fine so far...

Okay, thats fine.  I thought you had installed with Aptitude, so thats why I suggested that.

But again, its your choice!  :guitar:

---

### Post by neurostu on 2008-03-04
That will probably be the fastest and most painless way to do it. (I say fastest b/c IF something goes wrong, you'll spend more time fixing it)

Just to clearify (you probably know this)
Ubuntu = Ubuntu with Gnome
Kubuntu = Ubuntu with KDE
Xubuntu = Ubuntu with XFCE

In the future if you want to try a different "flavor" of ubuntu you don't have to do a clean install, just figure out what is special with that flavor and use "apt-get install" to get the specializations.

---

### Post by RadiationHazard on 2008-03-04
that's what i love about linux
even though i mess up alot it's usually an easy fix
=]

---

### Post by RadiationHazard on 2008-03-04
yeah i know i didn't have to do a clean install.
i just wanted to
hah

---

### Post by JoshuaRL on 2008-03-04
> **neurostu said:**
> That will probably be the fastest and most painless way to do it. (I say fastest b/c IF something goes wrong, you'll spend more time fixing it)

Just to clearify (you probably know this)
Ubuntu = Ubuntu with Gnome
Kubuntu = Ubuntu with KDE
Xubuntu = Ubuntu with XFCE

In the future if you want to try a different "flavor" of ubuntu you don't have to do a clean install, just figure out what is special with that flavor and use "apt-get install" to get the specializations.

True, but I would always suggest you use Aptitude for that operation.  As an example, if you only install Gnome, you can have problems with not having everything Ubuntu normally has.  But if you install ubuntu-desktop you will have everything that makes up the Ubuntu default install.

Also, Aptitude is the way to go instead of apt-get.  If you install ubuntu-desktop with apt and you want to uninstall, it gets hairy.  You would have to go into Synaptic, use packages.ubuntu.com as a reference, and remove everything that was installed.  Aptitude does that automatically.

Doing it that way makes sure everything is easy.  And Aptitude in this example is pretty much bomb-proof.  Unless it gets interrupted during download.  But that's true of APT too.

---

### Post by RadiationHazard on 2008-03-04
alright well i'm installing ubuntu back on as we speek
:)

---

### Post by neurostu on 2008-03-04
So what are the differences between using:
Synaptic
Apt-get
aptitude, 

What do they do differently?
What are their strengths, weeknesses?

---

### Post by JoshuaRL on 2008-03-06
> **neurostu said:**
> So what are the differences between using:
Synaptic
Apt-get
aptitude, 

What do they do differently?
What are their strengths, weeknesses?

Well, a little bit of this is always personal preference.  I've done a little bit of research, but you should feel free to experiment and figure out what you like personally best.

APT is simple, easy, effective.  It fixed the dependency problems Debian and other Linux distros were having at the time.  It is intuitive to helping you fix problems.  But it's CLI, and does JUST what you tell it too.  And searching for packages you want (via "apt-cache search") can be a little daunting and difficult.

[Aptitude](http://img137.imageshack.us/my.php?image=aptitudeqq0.png) is a graphical front-end for APT, and took over that role from dselect.  It has more in-depth descriptions of packages and keeps them in a [tree-organization](http://img137.imageshack.us/my.php?image=aptitude1ke0.png) for ease of use.  It is a text-based GUI, but has some [basic mouse abilities](http://img137.imageshack.us/my.php?image=aptitude2ay9.png) in an Xwindow environment.  For this discussion here, aptitude works well since it keeps track of all the pieces in a metapackage, not just the "wrapper" they came in, unlike APT.  Aptutude can also be used from the CLI without using the graphical part.  That's what the earlier command was, trying to uninstall a metapackage without opening the GUI.   What I like best about it is that [it has a game in it!](http://img137.imageshack.us/my.php?image=aptitude3im5.png)

Synaptic is a fully GUI GTK+ based front-end for APT.  It is very useful and one of my and many others favorite tools.  It has saved me from some stupid stuff I did, by fixing broken packages and returning APT and dpkg to a workable condition.  It is much less scary than anything from the terminal, and is just all-around great.  It has much better search capabilities than either aptitude or APT, and is able to manipulate multiple packages from multiple sources at the same time.

So basically, just use the tool you best like for that job.  They're all great and have their own strengths and weaknesses.

---

