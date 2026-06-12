---
title: "What ubuntu program to use to burn iso?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-05-25
I guess I couldn't figure out how to properly search to get this answer.

I am running feisty and I want to burn an iso file.  I burned one when I was on microsoft.  I don't know which program to use.

Thanks

dace

---

### Post by Outrunner on 2007-05-25
You can use either Gnomebaker or K3b. I belive you can also just right click om the .iso and use "Write to disk", but I've never used that so I'm not sure if it works well

```
sudo aptitude install gnomebaker
```

or

```
sudo aptitude install k3b
```

---

### Post by seetho on 2007-05-25
> **dace@bigfoot.com said:**
> I am running feisty and I want to burn an iso file.

I use xfburn.  It's light weight and it works.  Install using Synaptics.

---

### Post by ICUR2Ys on 2007-05-25
Thank you

I copied and pasted the commands and I got this, only coping last part of output.

Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
ardour [1:2.0-0ubuntu2 (feisty)]

Score is -19

Accept this solution? [Y/n/q/?] 

I don't know what the proper response should be.  Also don't know what a q response would mean.

dace

---

### Post by Hobo Joe on 2007-05-25
Go ahead an do it. It will figure it all out for you.

Q would be Quit.

---

### Post by BHelts on 2007-05-25
i just use the built in "write to disk"  hasn't been a problem yet for me.

---

### Post by ICUR2Ys on 2007-05-25
Thanks for everyones help.

I managed to get both programs and I will see which I like best also I will try the write to disk this was great.

I was going to ask about fixing a brocken package but when synaptic downloaded xfburn it removed that package so now it is moot.

I really appreciate your help.  thanks alot.

dace

---

### Post by dbbolton on 2007-05-25
i use the nautilus-cd-burner for ISO files. you just right-click on the file, then click burn to disk.

---

### Post by ICUR2Ys on 2007-05-25
Thank you,

I will play with that one too.

All this help is really appreciated.

dace

---

### Post by seetho on 2007-05-26
I use Xfburn because I need to erase CD-RWs sometimes.  I could not find this in Nautilus.  Can someone confirm this to be so or did I miss it somewhere?  Thanks.

---

### Post by dbbolton on 2007-05-26
> **seetho said:**
> I use Xfburn because I need to erase CD-RWs sometimes.  I could not find this in Nautilus.  Can someone confirm this to be so or did I miss it somewhere?  Thanks.
i think whenever you burn an ISO onto a cd-rw on nautilus, it automatically erases it. maybe i'm thinking of serpentine (which would be with audio cd's and not iso's).

---

### Post by seetho on 2007-05-26
I just tested it... and you are correct.  If the CD-RW has something on it, Nautilus gives you the option to erase.  Thanks for the info.  Maybe I don't need Xfburn anymore.

---

