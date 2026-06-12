---
title: "Can't install Firestarter 1.0"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by disk11 on 2006-04-29
Ubuntu 5.10, GNOME, everything up to date.

I tried using Firestarter 1.3 from Automatix, but it would not load on startup even with me putting my password into the prompt.  I spend about an hour looking at and trying different solutions and none worked.

In one thread I saw, a person said these issues don't occur with v1.0.  So I got the tar.gz off of sourceforge, but I cannot run "make" or "make install" to save my life.  I do have gcc and "build essential" packages installed.  How do I fix this?

---

### Post by Sef on 2006-04-29
Quickest way to install firestarter is this.

Open the terminal (Applications > Accessories > Terminal)

then type these commands

sudo apt-get update

sudo apt-get install firestarter

or you can go into Synaptic (System > Administration > Synaptic Package Manager) and click on search, then type in firestarter.

---

### Post by Sef on 2006-04-29
> In one thread I saw, a person said these issues don't occur with v1.0. So I got the tar.gz off of sourceforge, but I cannot run "make" or "make install" to save my life. I do have gcc and "build essential" packages installed. How do I fix this?

To compile, build-essential needs to be installed.

sudo apt-get update

sudo apt-get install build-essential

Here is a tutorial on installing software onto Ubuntu:

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

---

### Post by Stew2 on 2006-04-29
[QUOTE=disk11]Ubuntu 5.10, GNOME, everything up to date.

I tried using Firestarter 1.3 from Automatix, but it would not load on startup even with me putting my password into the prompt.  I spend about an hour looking at and trying different solutions and none worked.

In one thread I saw, a person said these issues don't occur with v1.0.  So I got the tar.gz off of sourceforge, but I cannot run "make" or "make install" to save my life.  I do have gcc and "build essential" packages installed.  How do I fix this?[/QUOTE]

Hi, my Automatix install of Firestarter does the same thing, asks for a password at boot up and then gives some kind of a termination error and closes. I found though that it did install. You have to click "applications", then "system tools", and it will be in the menu. I can start it from the menu and it works fine. Not too sure why it doesnt work from boot up though. I have to do some configuring on mine though because it wont let me access my other networked computers (samba). Hope this helps.
Regards,
Stew

---

### Post by disk11 on 2006-04-30
I just went ahead and installed firestarter from apt-get.

As for my compiling issues, it seems to start when I try ./configure as I get this
```
configure:error:XML::Parser perl module is required for intltool
```

I tried installing php-xml-parser but that didn't do it, and I already have build-essental.  How do I fix this?

---

