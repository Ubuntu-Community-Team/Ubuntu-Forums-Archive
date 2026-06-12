---
title: "[SOLVED] KDE and Gnome - Question"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by GayRockies on 2008-02-02
Hello, all.

I've looked around, and I can't seem to find the answer to this.  I'm absolutely sure it's here somewhere, but I just haven't been able to find it.

Ideally, I would like to be able to run both KDE and Gnome on this system.  However, all of the suggestions I've been able to find on how to do this have you install Ubuntu (Gnome) first.  Problem is that I've already installed Kubuntu (KDE).  Is it possible to add Gnome to Kubuntu rather than adding KDE to Ubuntu?

I hope I'm not confusing anyone.

Thanks in advance.  This wonderful community support is why I love Ubuntu.

Kind regards,

M.J. Christensen

---

### Post by jaytek13 on 2008-02-02
You can do 

```

sudo apt-get install ubuntu-desktop

```

---

### Post by emarkd on 2008-02-02
I think you just need to install the ubuntu-desktop package.

---

### Post by voteforpedro36 on 2008-02-02
They're right, that should put an option for Gnome in the "Sessions" part of KDM when you log in (supposing it's like Ubuntu in that respect)

---

### Post by GayRockies on 2008-02-02
Darn, 

That answer took 5 1/2 minutes to get!

I guess I get really confused when people say that they don't like Linux because it doesn't have the "customer support" that Windows does.  

Thanks again, as always.  I'll not post the thread as solved just yet, as I want to see what the results are to post on here, but I appreciate all the help.

Kind regards,

M.J. Christensen

---

### Post by RomeReactor on 2008-02-02
Hi. Just as a note: it would be better if you used aptitude instead of apt-get:
```
sudo aptitude install ubuntu-desktop
```
Using aptitude, if you want remove the Ubuntu desktop later, you can run:
```
sudo aptitude remove ubuntu-desktop
```
using apt-get, you would need to do as [instructed here]("http://www.psychocats.net/ubuntu/purekde").

---

### Post by ryanVickers on 2008-02-02
yea, just pick a *buntu live CD, install it, then go "sudo apt-get install %buntu-desktop", but change "%" to be u, or ku, or xu, etc etc

---

### Post by GayRockies on 2008-02-03
Heya,

Thanks for all the help.  Worked like a charm.  Only problem is, I did use apt-get instead of aptitude, as I hadn't read that post before I started.

Turns out, KDE absolutely hates my KVM (Keyboard, Video, Mouse) switch setup.  I've got a laptop running Ubuntu which doesn't have any problems, another laptop running XP with no problems, and I've run XP on this desktop with no problems (related to the KVM, at least.)  However, KDE's login screen takes about 4-5 minutes to recognize the Keyboard and Mouse with this setup.  This happens even if I have the KVM switched to this machine.  The only thing I can think that would cause this is, by having my keyboard and mouse on a USB KVM, it's like having them on a hub.  Perhaps KDE just isn't prepared for this.

I'm already resigned to many hours of work on this machine (once I have Linux up, I've got to rescue a Windows system that's, well, crashed as only Windows can.)  Therefore, I thought it was best, to save the gigabyte of space taken up by Kubuntu, to just reformat and install Ubuntu back on with no KDE.  One of these days I may play with it, but frankly, I'm happy with Gnome and Ubuntu, and there comes a point where you have to realize that you have computers to USE them, not to work on them constantly!

Thanks as always for the help.

Kind regards,

M.J.

:)

---

### Post by GayRockies on 2008-02-03
I know I marked this thread as solved, and the original issue was.  However, just an update on my progress:

I did what I was planning, installed Ubuntu and reformatted my Linux partition so that Kubuntu is completely gone.  While there is still some delay when you switch to this machine before it recognizes the keyboard, it's gone from 4-5 minutes to 3-4 seconds.

I don't know why that is, but I guess I'm stiking with Gnome, at least as long as I'm using multiple machines.

Kind regards,

M.J.

---

