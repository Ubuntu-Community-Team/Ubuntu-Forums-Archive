---
title: "stopping synaptic package removal"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by TonyLB on 2008-03-08
Just started with ubuntu after years with suse, and I have a problem.

The initial install dumps a lot of packages onto my machine which I don't want /wont ever use.  So I tried to use synaptic to get rid of some of these.  But when I tried to, synaptic wanted to get rid of lots more.

For example, I tried to remove the english/japanese dictionary.  Synaptic wanted to get rid of kde-amusements, kde and various other kde components.

I'm sure that these don't depend on an english/japanese dictionary - not listed in the dependencies anyway.  Is there any way to just get rid of the bloat I don't want while keeping the stuff I do want? :confused:

Tony

---

### Post by Nameless_one on 2008-03-08
Synaptic tries to uninstall packages which were automatically installed, if no other packages depend upon them. If you want to keep some of these packages, mark them as not automatically installed. 

I am not sure how one can do this with Synaptic. I use [aptitude](https://help.ubuntu.com/community/AptitudeSurvivalGuide). 

However, if one of the packages Synaptic tries to uninstall is kubuntu-desktop, I wouldn't worry about it. This is just a virtual package, meaning that it isn't a real package, but basically a "pointer" to other packages. Installing it installs all the packages it points to, but I think that removing it leaves them installed and so you can do without it. For the other packages, I don't know.

---

