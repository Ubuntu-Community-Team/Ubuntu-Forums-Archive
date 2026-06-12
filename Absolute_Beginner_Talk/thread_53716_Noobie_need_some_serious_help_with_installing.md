---
title: "Noobie need some serious help with installing"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by Epyon on 2005-08-01
Hi all, i just installed the newest version onto my laptop, i have a M6805.

well install went great everything works, i have a few linux type questions thou.

i want to get Azerus up and running, so i downloaded it, but i need java first. so i downloaded Java, but i do not know how to install it. so i got up to this part:
[IMG]http://i3.photobucket.com/albums/y72/EpyonMelee/Screenshot-1.png[/IMG]

i dont know what to do now, anyone care to help please? :)

---

### Post by super on 2005-08-01
both azeurus and the java runtime environment are available via synaptic

here is the instructions:
[http://ubuntuguide.org/#azureus](http://ubuntuguide.org/#azureus)

---

### Post by egon spengler on 2005-08-01
I have never done this myself so I dunno if it works but the [unofficial ubuntu guide](http://ubuntuguide.org/) offers [this solution](http://ubuntuguide.org/#azureus)

edit:
Looks like super beat me to it

---

### Post by Epyon on 2005-08-01
ok, i wrote that thingy in and it gave me this response

edgar@laptop:~$ sudo apt-get install azureus
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package azureus
edgar@laptop:~$

what does the couldnt find package mean?

---

### Post by super on 2005-08-01
you need to enable the universe software repositories
read this first then do the apt-get install:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

you should probably read the entire user guide when you get some time  :)

---

### Post by matthew on 2005-08-01
Do this first and try again:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Edit: oops! super beat me to this one

---

### Post by poofyhairguy on 2005-08-02
As a rule, that guide has our best stuff. If you can learn to use it, you will be happy. Read the notes at the top.

---

### Post by jccalhoun on 2005-08-03
Has someone tried that recently?  I updated the repositories and still got that it was not found.  Am I missing something wrong?

---

### Post by amrust on 2005-08-03
Your screenshot seems to indicate network connection problems, based on the GAIM and Network icons at the top of the screen, in your utility bar. Maybe that's just something else? You said you downloaded packages, so that can't be it, I guess.  :?

I think I've had a package or two that were not able to be found by Synaptic, even after adding the extra repositories. But then when I tried again later in the evening, they worked just fine.

FWIW

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=jccalhoun]Has someone tried that recently?  I updated the repositories and still got that it was not found.  Am I missing something wrong?[/QUOTE]

You need this command:

> sudo apt-get update

now try again

---

