---
title: "Dvd Drive Problems"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by metalfanatic07 on 2007-04-29
I recently bought a new DVD burner and I basically can't do anything with it. the only thing it is useful for is playing and ripping CDs, it will not open or acknowledge the existance of DVDs. What do I do to fix this problem

---

### Post by Metacarpal on 2007-04-29
First question: did you previously have a DVD burner in that computer (with Ubuntu installed) that did work?  If so, I'm afraid that the rest of my post is going to be completely useless to you.

Also, please forgive if I'm telling you anything you already know.  I find it's better to assume you have no idea what I'm talking about, so I don't leave you with more questions than answers.  :)

If this is the only DVD player you have installed, there are a couple of packages you'll need to get DVD playback going.  First, you'll need to add some extra software repositories.  (These are download locations your computer will use to install software packages.)  Go to your System menu > Administration > Software Sources.  It'll ask you for a password - use the same one you use to logon to the computer.  Then make sure the "Universe" and "Multiverse" check boxes are checked, and close.

Next, you'll need to install some software.  I know, this is kind of a pain, but due to some legal issues (I'll provide a link explaining that), Ubuntu can't have this stuff installed by default.

There are two basic ways of installing software - using a graphical interface called Synaptic (located in System > Administration > Synaptic Package Manager), or through a text-based command line called the terminal (Applications menu > Accessories > Terminal).  In general, I use Synaptic if I don't know the name of the package I want to install, and I use the command line if I do know.  Give both a try, see which you like better.

Installing from Synaptic is as easy as using Search to find what you want, clicking it, choosing Install, and clicking Apply.  From the terminal, you just type:

```
sudo aptitude install *package-name-here*
```

Both ways ask for your password.  This is to make sure nobody installs anything you don't want installed (no spyware! Yay!).

[Why those packages aren't already installed]("https://help.ubuntu.com/community/RestrictedFormats")

[What you'll need to do to get DVD playback up and running]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

If that's all too confusing for you, let me know what version of Ubuntu you're running (such as 6.06/Dapper Drake, or 7.04/Feisty Fawn), and I'll walk you through it.  :)

---

