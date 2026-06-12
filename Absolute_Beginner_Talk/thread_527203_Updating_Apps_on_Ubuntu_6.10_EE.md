---
title: "Updating Apps on Ubuntu 6.10 EE"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-08-16
hey,

I was wondering how to update all the apps in Ubuntu EE 6.10 (open office in particular). Do these updates take up lots of space?


thanks in advance!

(lol im running 6.10 not 7.04 FF because I heard there is a bug with 7.04 that does not allow you to save changes on USB key)

---

### Post by Hobo Joe on 2007-08-16
> I heard there is a bug with 7.04 that does not allow you to save changes on USB key

I've never heard of that, where did you hear it?

Anyways, it should update automatically, but if it doesn't, you can first open all your repositories by going to system>administration>synaptic package manager, then going to settings>repositories, and opening all of them except the cd-rom ones.

Then you can type these commands into the terminal:
```

sudo aptitude update

sudo aptitude upgrade

```

---

### Post by loserboy on 2007-08-16
you should get update notifications in the tray (orange square with white star).

if you mean you want to do version updates, i think you will have to change your sources list to the feisty sources to get more recent versions, you should be able to search to find out how

edit: oh sry late to post

---

