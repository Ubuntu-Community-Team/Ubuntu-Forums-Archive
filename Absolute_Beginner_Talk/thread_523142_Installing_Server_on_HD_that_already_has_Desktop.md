---
title: "Installing Server on HD that already has Desktop"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by peterpancreas on 2007-08-11
I'm very new to Linux and Ubuntu but I would eventually like to set up a server from home.  I downloaded the Desktop module of Ubuntu the other night, installed it and everything seems hunky dory.  What I'm wondering is: should I remove the Desktop module before installing the Server?  Or can they both run on the same HD?

And on a similar note, any tips on how to setup the server once it's downloaded and installed?

Thanks for your future tips!

---

### Post by irish_flu on 2007-08-11
Nope, you'll do just fine adding whatever you want to the desktop edition.  Use Synaptic Package Manager, or apt-get from the command line, to add any packages you wish (such as Apache2, PHP, a mail server, etc).

In fact, had you installed the Ubuntu Server Edition instead, you could just as easily add the ubuntu-desktop package from the command line and go the other direction.

---

### Post by kronk on 2007-08-11
Strictly speaking the Desktop "version" is simply optimised for desktop use. With Ubuntu package management aka .deb you can pretty much combine both rolls if you wanted to although it's probably not best practice.

Point being that you should be able to load any Server based service you might want to try out on the install you already have with little difficulty particuarly if you have a decent net connection.

:)

---

