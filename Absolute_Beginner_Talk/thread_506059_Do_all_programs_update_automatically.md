---
title: "Do all programs update automatically?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by keyboardashtray on 2007-07-21
One of my favorite things about Ubuntu is how smooth updates have been for it. I've read somewhere that one of its strengths is that, while in Windows, each program has to watch for its own updates, in Ubuntu, all are checked together. I know there are more technical ways, but right now I'm very happy to let Ubuntu automate the whole process.

If I understand correctly, Ubuntu doesn't necessarily try to get you the cutting edge, newest version of a program, even if it came with Ubuntu, instead since new OS releases are so common, it puts that newer version in the next release. Am I right on that? Like for example, Rhythmbox: when I go to Synaptic, it says there is an update for that (along with a whole bunch of other stuff). But it doesn't show up in the Update Manager, like Firefox did today.

But what I'm unsure of, is which qualify for that update check? Right now, in software sources, I have the first two options checked, the first two, important security updates and recommended updates. I think I have a grasp on the third option: it is slightly experimental, right? Proposed changes for the next release. The fourth option is what confuses me, though.

What options need to be checked for programs like Rhythmbox to get checked for an update, through update manager? Or how about something like Lincity NG, say they were to make a new release of that, would that be checked for me too? 

If someone can explain to me, or point to good tutorial that really delves into these four options specifically that would be great - I do like to be running the cutting-edge releases of stuff, but I want stability too.

---

### Post by bapoumba on 2007-07-21
> **keyboardashtray said:**
>  Proposed changes for the next release. The fourth option is what confuses me, though.
I would not go with the -proposed repositories. These are for packages that nned to be checked on a larger scale and that can turn out to be buggy. Security and updates are fine. What do you have in your sources.list ?
```
cat /etc/apt/sources.list
```

---

### Post by keyboardashtray on 2007-07-21
I have main, restricted, universe and multiverse enabled. So do you think I should enable unsupported (feisty backports) in the updates list?

---

### Post by bapoumba on 2007-07-21
[http://packages.ubuntu.com/feisty-backports/]("http://packages.ubuntu.com/feisty-backports/")
For the backports, it's up to you. You can browse through and see is they are any packages you might want to upgrade.

I usually keep the backports commented, and install things one by one, rather have them on all the time and upgrade with the backports activated. I recall a tricky problem with a package a year ago or so, so I've been doing this way from that time on.

---

