---
title: "newbie question - easy update for multiple installations"
date: 2005-06-26
forum: Absolute Beginner Talk
---

### Post by robertzhong on 2005-06-26
hi all,
 I installed Ubuntu one day ago, I liked it very much indeed, for me it is a perfect linux distro (coming from winxp).

I am thinking putting same Ubuntu on my wife's computer (she is sick of the the emails with so many virus etc).

now what is the easier way of updating both computers, I have already spend a lot time down loading on my computer, don't want to repeat the same process with my wife's Ubuntu update.

thks in advance
robert zhong

---

### Post by Xian on 2005-06-26
You could make a local repo using [Debarchiver](http://www.opal.dhs.org/programs/debarchiver/) and set up your own [config](http://koenraad.heijlen.be/dev/debarchiver/). You could also provide an [Automatic Package Repo](http://familiasanchez.net/~sanchezr/?page=debrepository) which will perform a similar function. Most of these are based on the [Debian Repository How-To](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html). Then you would just need to sync with other systems that you have need to update.

---

