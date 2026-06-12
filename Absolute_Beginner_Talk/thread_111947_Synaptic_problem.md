---
title: "Synaptic problem"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by Edward The Bonobo on 2006-01-03
I'm having an ongoing frustration trying to install something that wil make my iPod work.

I'm trying to get YamiPod, which has been suggested as an alternative to gtkpod (which doesn't work for me.  don't know why).

So...I'm using Synaptic.  I go Preferences...Repositories...Add and tick the Community box.  But - when I OK it, it doesn't seem to stay selected.  Therefore a search on YamiPod doesn't find anything.

When I OK from the Repositories dialogue, it updates the repositories every time - which I don't think it's meant to do.

Any ideas?

Alternately - I can download YamiPod from the site.  How would I install it from my desktop?

---

### Post by aysiu on 2006-01-03
[Yamipod isn't in any Ubuntu repositories.](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=yami&searchon=names&subword=1&version=all&release=all)

---

### Post by Edward The Bonobo on 2006-01-03
Ah, Thanks.

In that case...would installing it be 'a bad thing/?

And...How?  The instructions for enabling extra repositories seem complex.  I can download it to my HD.  Is there an easy way of installing from there?

---

### Post by Jimmey on 2006-01-03
Yeah, I looked at the download for Yamipod, and it's in a tar.gz - I think that's the source code. That'd mean that you'd have to compile this program yourself. You'd have to look for a tutorial on compiling software - I've never done it, lol.

---

### Post by Edward The Bonobo on 2006-01-03
EeK!

Scary for an absolute beginner!

---

### Post by Jimmey on 2006-01-03
Yeah - Definately. Although, if all goes well, it should prove easy.....I hope it does!

---

### Post by Mustard on 2006-01-03
It may or may not be easy, depending on what you have installed already.  The one package you really need to start compiling your own stuff is build-essential.  You can either search for it in synaptic, or enter this command in terminal (with syanptic closed)...

```
sudo apt-get install build-essential
```

This installs some of the basic tools necessary for compiling programs.  A lot of tar.gz files come with a README file inside which explains how you go about installing them.  If you use the search function in this forum you will find quite a  few threads on this subject, as its a very common question.  Try searching with the keywords 'tarball' and 'installation'.  The word 'tarball' is a linux term for describing files that end in tar.gz.

I would strongly suggest your find some information on using 'checkinstall' too.  This is handy feature in which you replace the last command 'make install' in the compiling process, and use the command 'checkinstall' instead.  This creates an entry in synaptic which has a record of where the application was installed and this can make it extremely easy to uninstall the application.  Uninstalling applications installed using the tarball method can be very troublesome otherwise.  Read first and do later would be my advice.

---

