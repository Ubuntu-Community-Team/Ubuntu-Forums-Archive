---
title: "How do I solve dpkg interruption?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-03-08
Hi, i just installed Ubuntu ( a couple of days ago) but i have HUGE problems adapting to it. I have to sudo that and sudo this..... and when i try to sudo anything or install anything from add/remove programs i just get this message 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. :confused: :confused: 
Do anny one know how to fix this, and is it possible for me as a newby to use Ubuntu and install stuff without the terminal???, or do i just have to learn to use the terminal:confused:

---

### Post by jvc26 on 2007-03-08
Open the terminal and type:
```

sudo dpkg --configure -a

```
That will solve the issue you mentioned - you can install via add/remove programs and also via synaptic package manager (both have GUIs) Terminal is the simplest way as it is just a simple 1 line command - have a look at [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) for many install commands.
Il

---

### Post by PartisanEntity on 2007-03-08
This should be of help too: [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by ajmannen on 2007-03-08
Aaaaaaaaaaaaa so complicated, in windows it was just, dobbel click - next - next - next - wait - wait - wait - finish, and rebot :(

---

### Post by Perfect Storm on 2007-03-08
In ubuntu you just write one command then it's installed and ready to use, much easier (when you learned it) and you can install multiply programs in one command without going to hunt down on various sites.

---

### Post by milton1 on 2007-03-08
> **ajmannen said:**
> is it possible for me as a newby to use Ubuntu and install stuff without the terminal???, or do i just have to learn to use the terminal:confused:

Think of it like learning to drive a stick-shift. It's a bit scary at first, but you will have much better control in the end.

---

### Post by ajmannen on 2007-03-08
hmmm..... i'l try to learn, but can you install everything in synapic package maneger or do you need terminal?

---

### Post by Perfect Storm on 2007-03-08
You can use synaptic.

---

