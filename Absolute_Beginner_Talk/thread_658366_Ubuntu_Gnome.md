---
title: "Ubuntu Gnome"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Jelmoh on 2008-01-04
Ok, I'm working with Ubuntu for some time now, I'm not a know it all... on the contrary... :P
But I'm wondering...
just the other day I wanted to figure out what KDE looked like (saw it before, but just a quick peek actually).. so I searched for the package.. found it...
later, I searched for Gnome... and I saw that the Gnome package wasn't even installed... I didn't install KDE, so that could not be it.. I'm definitely using Gnome...
I mean the package named Gnome, couldn't find another package that could refer to the actual Gnome desktop... Anyone knows more about this?

---

### Post by perlluver on 2008-01-04
It is called Ubuntu-desktop.

---

### Post by steeleyuk on 2008-01-04
If ubuntu-desktop is installed, you have the Ubuntu-variant of GNOME which includes all the GNOME customisations by the developers.

Though, you don't need to have ubuntu-desktop to be installed to still be running GNOME. Its what called a metapackage, it isn't necessary but it makes for easier upgrades and installs.

---

### Post by perlluver on 2008-01-04
> **steeleyuk said:**
> If ubuntu-desktop is installed, you have the Ubuntu-variant of GNOME which includes all the GNOME customisations by the developers.

Though, you don't need to have ubuntu-desktop to be installed to still be running GNOME. Its what called a metapackage, it isn't necessary but makes for easier upgrades and installs.

Well that is interesting, thank you.  I did not know that either.

---

### Post by seventhc on 2008-01-04
Before you log in you should see a place that says 'session' that will show you and let you choose the different desktops that you have installed. So you can install kde then just choose which you want to use. you can have many different desktop environments. I'm a big fan of gnome and stick with it, but every so often I'll try another.

---

### Post by kellemes on 2008-01-04
In order to get the default Ubuntu desktop back you need to install ubuntu-desktop.
You can simply install KDE by installing "kde", this will give you KDE as a option in your loginmanager-session-menu.

---

### Post by insertAlias on 2008-01-04
Also, if you install the package kubuntu-desktop, you will get KDE with all the Kubuntu default customizations.  Same for xubuntu-desktop and Xfce.

---

### Post by Jelmoh on 2008-01-04
So I don't exactly have Gnome installed?
But the Ubuntu version of Gnome?
what's the difference? I mean, is it a big difference?
or just some oversimplification of the original gnome?
I'm sorry for the questions.. But I want to know a lot about Ubuntu, and Linux in general.. :P
Thanks for your time for what its worth.. ;)

Edit:  @Steeleyuk: But if I don't have Ubuntu-Desktop installed, I have to have Gnome installed to run Gnome, am I right or absolutely wrong?

---

### Post by zipperback on 2008-01-04
A default installation of Ubuntu Linux will give you a Gnome based desktop.

A default installation of Kubuntu Linux will give you a KDE based desktop.

A default installation of Xubuntu Linux will give you a Xfce based desktop.

A default installation of Fluxbuntu will give you a FluxBox based desktop.

A default installation of Edubuntu will give you a KDE based desktop.


There are a few other Ubuntu variant distributions as well as those listed above, but once you see the various user interfaces of them, you should be able to recognize which desktop interface is being used.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-01-04
> **Jelmoh said:**
> So I don't exactly have Gnome installed?
But the Ubuntu version of Gnome?
what's the difference? I mean, is it a big difference?
or just some oversimplification of the original gnome?
I'm sorry for the questions.. But I want to know a lot about Ubuntu, and Linux in general.. :P
Thanks for your time for what its worth.. ;)

Edit:  @Steeleyuk: But if I don't have Ubuntu-Desktop installed, I have to have Gnome installed to run Gnome, am I right or absolutely wrong?

You're just misunderstanding what it is that you have.

If you have Ubuntu Linux installed on your computer, then you have Gnome installed by default.


- zipperback
:popcorn:

---

### Post by Jelmoh on 2008-01-04
I know, that's whats explained to me earlier.. 
but Steeleyuk said:
> Though, you don't need to have ubuntu-desktop to be installed to still be running GNOME. Its what called a metapackage, it isn't necessary but it makes for easier upgrades and installs.
But, I assume that I have to have the Gnome package installed to run Gnome desktop, IF I uninstall the Ubuntu-Desktop package, am I right?

---

### Post by steeleyuk on 2008-01-04
You don't need that 'gnome' package either. Even if you remove ubuntu-desktop, GNOME will still be there.

There isn't really one package which tells you whether you have GNOME or not, its more of a collection of packages which all go together to form the GNOME desktop.

---

### Post by insertAlias on 2008-01-04
> **Jelmoh said:**
> So I don't exactly have Gnome installed?
But the Ubuntu version of Gnome?
what's the difference? I mean, is it a big difference?
or just some oversimplification of the original gnome?
I'm sorry for the questions.. But I want to know a lot about Ubuntu, and Linux in general.. :P
Thanks for your time for what its worth.. ;)

Edit:  @Steeleyuk: But if I don't have Ubuntu-Desktop installed, I have to have Gnome installed to run Gnome, am I right or absolutely wrong?

With ubuntu-desktop installed, you do have Gnome installed, just with the Ubuntu customizations and default applications pre-set and pre-installed.  You could do the exact same thing package by package, it is just grouped together for you in ubuntu-desktop.

---

### Post by Jelmoh on 2008-01-04
ah, that starts to form a picture... :)
I think I get it now, except..
you say even if I uninstall the Ubuntu-desktop I still have gnome...
But the package named "Gnome" isn't installed.. I get the fact that Gnome exists of multiple packages, not just the package named Gnome, but isn't that package the main package with which the rest of the packages cooperate?  Lousy explanation... I hope you understand...

---

### Post by kellemes on 2008-01-05
> **Jelmoh said:**
> ah, that starts to form a picture... :)
I think I get it now, except..
you say even if I uninstall the Ubuntu-desktop I still have gnome...
But the package named "Gnome" isn't installed.. I get the fact that Gnome exists of multiple packages, not just the package named Gnome, but isn't that package the main package with which the rest of the packages cooperate?  Lousy explanation... I hope you understand...


It's getting confusing.. :)
1- If you ditch ubuntu-desktop you'll lose Gnome.
2- If you wanne have Gnome you can install "gnome" **or** install "ubuntu-desktop" (this gives you Gnome + mostly unimportant crap to give you the I'm-part-of-the-Ubuntufamily feeling)

Listen, you don't need Gnome, you can safely ditch it, kill it and install a window/desktop-manager for grownups. ;)

---

### Post by steeleyuk on 2008-01-05
> 1- If you ditch ubuntu-desktop you'll lose Gnome.

Wrong. ubuntu-desktop is a metapackage and removing it will not remove GNOME or any other programs. A metapackage can only install other packages, it cannot remove them...

Number 2 is correct though. Well except the unimportant crap bit...

And your last comment is just childish.

---

### Post by kellemes on 2008-01-05
> **steeleyuk said:**
> Wrong. ubuntu-desktop is a metapackage and removing it will not remove GNOME or any other programs. A metapackage can only install other packages, it cannot remove them...

Number 2 is correct though. Well except the unimportant crap bit...

And your last comment is just childish.


Thanks for correcting me. :)

---

### Post by Jelmoh on 2008-01-05
I wasn't planning on beginning an all-out desktop environment war here.. :P
Well, thanks for your answers and advice.. :P
I'm just going to look around and see which I like best... :)
I like Gnome very much, but what I've seen of KDE really interests me..
It looks more mature... sorted out... more "bling bling":P

---

### Post by Martje_001 on 2008-01-05
Yes it does. You should really try KDE 4 when it's out (11 jan)!

---

### Post by Jelmoh on 2008-01-05
I am looking forward to it! :D  and I really AM! going to try that one out to...
just to stay on top of things... to know a little bit about it...
I'm the so called.. Linux guru in my class... school... don't know exactly how you English  /American people call it... :P    (The group of people that share the same level of education as me) I'm studying ICT (IT, in your country I guess.., computers and networking.. hard- and software)

---

