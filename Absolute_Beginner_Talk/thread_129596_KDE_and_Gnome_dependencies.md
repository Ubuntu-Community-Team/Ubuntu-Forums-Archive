---
title: "KDE and Gnome dependencies"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by Edward The Bonobo on 2006-02-14
I'm trying to increase my understanding of how Linux software is put together - for no other reason than curiosity.  Can someone explain a bit about KDE and Gnome dependencies?  Or point me somewhere that can?

What I've discovered in my 2 month and counting voyage into the Wonderful and Frightening World of Ubuntu is that KDE and Gnome do 'something' that integrates applications together so they all work on a desktop.  But they take a lot of memory to do this...so I've had to abandon them in favour of Xubuntu.  Xfce - for reasons I'm not entirely clear on - doesn't quite give me a desktop as I understand it (documents and apps littered around the screen) but does handle window for me.

However...as I understand it, running Gnome/KDE applications in xfce doesn't seem to be entirely ruled out.  For example...I want to try out amaroK and Banshee (because I want to manage my iPod and don't like gtkpod) - and Synaptic or apt-get will load all the Gnome/KDE bits I need.  But I don't understand what these bits are, what they're doing for me and how they'll effect my computer (will Banshee be as hopelessly slow as Gnome in general was?)

Can anyone make sense of all this for me?

(and, while I'm here...has anyone used amaroK/Banshee with an iPod?)

---

### Post by Robgould on 2006-02-14
The answers to most of your questions are sketchy to me as well, but there a couple of things I do know. You can run KDE and Gnome packages in Xfce. That is because apt or synaptic will handle all of the dependeny issues for you. If you install Amarok in gnome, necessary kde dependencies will be installed automatically. Both KDE and Gnome are simpy GUI shells that sit on top of the ubuntu kernel - if my understanding is right. Unlike windows, the desktop environment is not part of the kernel, it runs on top of it. You can run ubuntu, with all of its functionality, without KDE, Gnome or any desktop at all.

---

### Post by Jucato on 2006-02-14
AFAIK, dependencies are just the Linux versions of DLL's in Windows. Basically, they are libraries that contain code needed by certain programs to run. Apt-get takes care of resolving dependencies during installation. This means it downloads and installs the needed files for the program to work.

I don't think installing KDE or GNOME apps in XFCE will bog your system down. I'm not really sure myself why XFCE is faster than KDE/GNOME, but I think it has to do with some functionality that's present in the bigger Desktop Environments but not present in XFCE.  But I'm not entirely sure.

---

### Post by meborc on 2006-02-14
xface is faster because it uses less memory (logical)... it uses less memory because it uses a window manager that uses less memory... the whole eyecandy thing is what keeps KDE and GNOME slow... at least that is what i think before going to bed every night :-k

---

### Post by Edward The Bonobo on 2006-02-15
Ok...that's all kinda what I assumed.

Only - my intuition was that KDE/Gnome packages would be constructed using their respective UI objects - the 'eye candy' bits - so that a package running in xfce would still have the same Look and Feel as it's original desktop???

And why would the Xubuntu project people want to be so careful to ensure that their distro had no Gnome/KDE dependencies?

And...if their are bits in the desktop which aren't strictly part of desktop functionality, but are still needed to make some of their packages run - then this seems inefficient.  Why not re-use equivalent building blocks which are desktop independent?  Surely that's what Open Source is about?

And...the difference between xfce and Gnome/KDE seems to be more than eye candy - eg drag and drop to the desktop background itself.

Questions, questions, questions.:-k

---

### Post by Robgould on 2006-02-15
Gnome and kde can both work in ubuntu at the same time, but they are not interchangeable.  They are programmed in differen languages and have different structures.  Amarok for example ins a KDE package.  It can not run natively in Gnome.  It needs to load some dependencies to allow it to run in Ubuntu.  You see it on your gnome dektop, but it is not PART of your gnome desktop.  Amarok will look the same in gnome or sfce as it does in KDE.

---

### Post by Edward The Bonobo on 2006-02-15
Yeah...that kinda makes sense...but...

I guess this is an Xubuntu question.  Why the need for dependency-free packages?  If the problem with Gnome/ KDE is simply the slowness of the desktop, what's wrong with including Gnome/KDE packages, PLUS their non-desktop-related dependencies?

(I don't need to know any of this.  I'm just being inquisitive).

---

### Post by Estariel on 2006-02-15
[QUOTE=Edward The Bonobo]Yeah...that kinda makes sense...but...

I guess this is an Xubuntu question.  Why the need for dependency-free packages?  If the problem with Gnome/ KDE is simply the slowness of the desktop, what's wrong with including Gnome/KDE packages, PLUS their non-desktop-related dependencies?

(I don't need to know any of this.  I'm just being inquisitive).[/QUOTE]

If you start amarok, a lot of KDE related subprocesses will be started, because amarok needs these processes to handle certain stuff for it.
The same thing happens when you start a GNOME application.

These processes need a certain amount of computational power, and if you have a (very) slow PC, you don't want that.

---

### Post by Gustav on 2006-02-15
And the Gnome and KDE libs take a lot of space.

---

### Post by carlosqueso on 2006-02-15
Actually AFAIK, XFCE uses GTK+ (which GNOME also uses) to run its stuff as well.  Thus, GNOME apps should work fine (it's the window manager that slows GNOME down), but KDE ones will cause the KDE libs to load and will probably look kinda weird.  As for your other thing, yes XFCE doesn't allow putting icons on the desktop, but there is a way to set up ROX-filer to get that to work (don't ask me how, I like my desktop clean).

---

### Post by LordBug on 2006-02-15
Some of the basics, as I understand them:

Gnome and KDE are Desktop Environments.  They run on top of Window Managers and use various libraries for graphics and sound.  Gnome uses Metacity by default, but can be re-configured to run on top of XFCE.  KDE, I dunno.  I don't use it :)  Library wise, Gnome uses GTK+ for graphics and ESD for sound.  KDE uses QT and ARTS.

Window Managers do a lot of the work.  As I mentioned, XFCE is one.  Fluxbox, Blackbox, Waimea (R.I.P.), and many more are also window managers.

Now, graphical/X11 applications also run on top of the window managers.  They are mostly not Desktop Environment specific (there's probably a few exceptions).  They will usually call for files from either the GTK+ or QT libraries, though, so you'll need those.  You can have both GTK+ and QT libraries installed at the same time.  They will co-exist.  Thus, you could easily have XFCE installed for the Windows Manager and use applications from both Gnome and KDE (and anything else you want).

The main advantage to Gnome and KDE is the fact that they setup things so that new users have an easy to use, and very pretty, environment right away.  Beyond that, you can do anything they can do in any other Window Manager.

---

### Post by Edward The Bonobo on 2006-02-17
Cool!  VMT.

I'll await Xubuntu developments to see if they're going to give me a desktop as I understand it (ie messy.  Via Rox?) without my having to think about it.

The problem this Ubuntu thingy is that it's too damned flexible.  Too many choices.  Too much information to decide.  To latte or not to latte?  And *do* I want fries with that???

---

### Post by meborc on 2006-02-21
ubuntu, kubuntu, xubuntu, edubuntu, serverinstall, ubuntu-lite ... you can go on for hours (ok, you can't, but its just to make a point) :mrgreen: 

it is true that the field of ubuntu and its 'modifications' is big, but new user chosing UBUNTU choses by default GNOME and has nothing more to worry about... more advanced users are the ones, who will go around searching for the _BEST_ possible setup, and that is where the different versions get their start from...

as long as the official/normal/default ubuntu stays **UBUNTU**, i'm not worried :-D , but when all these different choises become to bother newcomers, i guess it will be time to make things more simple...

and simplesness/humanity is the moto behind ubuntu...

---

### Post by Edward The Bonobo on 2006-02-21
Up to a point...

I would love a simple life.  I'd love to install vanilla Ubuntu with its lovely Gnome desktop.  I'd love to have it run at a tolerable speed.  I'd love to have some money to replace my ancient, third-world spec PC.

'Ubuntu is Linux for Humans'.  I've recently watched the movie 'Kinsey'.  One of the lessons one can draw from his work is that there are many, many different types of human.  I'm the impoverished kind...hence Xubuntu on a crappy machine.

---

