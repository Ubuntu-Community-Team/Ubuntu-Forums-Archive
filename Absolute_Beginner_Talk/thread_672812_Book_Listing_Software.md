---
title: "Book Listing Software"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by corowakid on 2008-01-20
Hope this is the right forum.

I'm looking for a book listing program for Linux that will allow me to catalog my library. I use one on MS, but as I'm going to move to Linux only I need to find a suitable app.

Any comments/help would be much appreciated. thanks

---

### Post by bwtranch on 2008-01-20
What is a book listing program? There are database programs MySQL and such.

---

### Post by Thund3rstruck on 2008-01-20
Open-Office.org Database
Open-Office.org Spreadsheet

Otherwise, you could write a front-end for a MySql as suggested above

---

### Post by TheWizzard on 2008-01-20
tellico

```
aptitude show tellico
```
[http://periapsis.org/tellico/](http://periapsis.org/tellico/)

---

### Post by Malta paul on 2008-01-20
Hi, you might find a program that you need ai:
[http://www.gnomefiles.org/](http://www.gnomefiles.org/)
[http://www.cnr.com/supportPages/about.seam](http://www.cnr.com/supportPages/about.seam)
Good luck:)

---

### Post by forestpixie on 2008-01-20
> **TheWizzard said:**
> tellico

```
aptitude show tellico
```
[http://periapsis.org/tellico/](http://periapsis.org/tellico/)

I use this for my music etc, seems to fit the bill

---

### Post by geeree on 2008-01-20
> **corowakid said:**
> I'm looking for a book listing program for Linux that will allow me to catalog my library. I use one on MS, but as I'm going to move to Linux only I need to find a suitable app.

Alexandria is a wonderful little program written in Ruby. It is exactly what you need:

[http://alexandria.rubyforge.org/](http://alexandria.rubyforge.org/)

I have used Tellico and personally find Alexandria to be far superior to it because of its simple design and useful capabilities. You can enter books in Alexandria just by putting in their ISBNs and Alexandria will then look up various Z39.50 servers for downloading the book details and cover picture. In Ubuntu, you can install Alexandria through Synaptic.

Girish.

---

### Post by pumahalen on 2008-01-23
> **geeree said:**
> Alexandria is a wonderful little program written in Ruby. It is exactly what you need:

[http://alexandria.rubyforge.org/](http://alexandria.rubyforge.org/)

I have used Tellico and personally find Alexandria to be far superior to it because of its simple design and useful capabilities. You can enter books in Alexandria just by putting in their ISBNs and Alexandria will then look up various Z39.50 servers for downloading the book details and cover picture. In Ubuntu, you can install Alexandria through Synaptic.

Girish.


I agree with you on Alexandria, that is why I'm using time to try to find out why it installs on 7.10 without the "Advanced"-button under Edit-Preferences-Providers. Without the possibility to add proivders, (and with amazon left out in the install) it is not what I was hoping for. I have tried the "all-deb" packages on rubyforge and softpedia as well with no different result. So, perhaps you have an idea?

---

### Post by geeree on 2008-01-23
> **pumahalen said:**
> I agree with you on Alexandria, that is why I'm using time to try to find out why it installs on 7.10 without the "Advanced"-button under Edit-Preferences-Providers. Without the possibility to add proivders, (and with amazon left out in the install) it is not what I was hoping for. I have tried the "all-deb" packages on rubyforge and softpedia as well with no different result. So, perhaps you have an idea?

Oh, sure. I've spent some time on that issue myself. Basically you are not finding the "Advanced" button because of two bugs in the v0.6.1 that you are using. These bugs were not corrected even as late as the second beta release of the newer version, which is v0.6.2, so you'll not find the advanced button even you are using either v0.6.2b1 or v0.6.2b2.

To solve this problem, install the latest stable version 0.6.2. In case that is not available through Synaptic, get it from their web site. I'm sure this will help.

Girish.

---

### Post by pumahalen on 2008-01-23
Thanks for the quick reply. 

Problem is, though, that I really have used their alexandria_0.6.2_all.deb (my first choice, actually :) ), then I started to think about dependencies, so I used apt-get, still no difference. 
The 7.10  I am using is freshly installed, no previous versions of Alexandria on that. Perhaps that is the problem?  Or perhaps some Ryby-files are needed?

J

---

### Post by geeree on 2008-01-23
> **pumahalen said:**
> 
Problem is, though, that I really have used their alexandria_0.6.2_all.deb (my first choice, actually :) ), then I started to think about dependencies, so I used apt-get, still no difference. 

Hmm ... yes I think Alexandria has a somewhat sensitive dependence on Ruby/Amazon and also perhaps on Ruby/ZOOM and YAZ. So I guess you *might* be having a version problem there. (Why not try getting the latest versions of these packages from Synaptic?) But I am not aware of exactly what.  So I'd suggest you post this problem on the Alexandria mailing list [email]alexandria-list@rubyforge.org[/email]. Alexandria developers are currently pretty active so help might be surprisingly quick in coming!

Girish.

---

### Post by pumahalen on 2008-01-23
Thanks,

I'll try that.

J

---

