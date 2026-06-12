---
title: "Installing Xine"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-03
I am trying to install Xine, and I enter the command
> ./configure
Then I get the following error:
> configure:  error:  C compiler cannot create executables
See 'config.log' for more details.
Any good suggestions are appreciated.

---

### Post by Steveway on 2008-01-03
Why do you want to compile it?
Open Synaptic and search for it and then install it or enter this in a terminal:
sudo apt-get install libxine1
or click this link:
[apt:libxine1]("apt:libxine1")

---

### Post by philinux on 2008-01-03
Or from synaptic

gxine or

xine-ui

---

### Post by AndyCooll on 2008-01-03
Continuing on from above libxine is the engine, GXine and Xineui are frontends for the libxine engine.

What aspect of Xine are you seeking to use?

:cool:

---

### Post by jhvillegas2 on 2008-01-03
I am trying to install the 'lib'.  How do I do that?  Trying to install the lib is what is throwing errors.

---

### Post by AndyCooll on 2008-01-03
> **jhvillegas2 said:**
> I am trying to install the 'lib'.  How do I do that?  Trying to install the lib is what is throwing errors.

Easiest way is to open up Synaptic (System > Administration > Synaptic Package Manager) and do a search for libxine1. You'll find a few listed, click on which ones you wish to install (probably all of them) and install.

And I ask again, is there any particular reason why you are trying to install "xine"? It would give us more information on how we can help you.

:cool:

---

