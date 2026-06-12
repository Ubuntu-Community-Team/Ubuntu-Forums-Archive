---
title: "Kubuntu crashes more times than Windows would ever crash!"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by ObsessedMikey on 2008-01-13
Okay, yeah I'm a complete rookie to the whole Ubuntu thing, and Linux in general.  So recently I started off with Ubuntu.  It worked pretty much okay I guess, although it did have plenty of problems to chew over (the sound doesn't work and this is apparently due to Ubuntu ruining this in the Gutsy "update").

So, not content with what I personally believe is quite an ugly looking operating system, I decide to try out Kubuntu.  So I made myself a nice little Live CD of Kubuntu and off I went.

Then, my life became worse, stressing became a constant thing, cursing at my laptop was a common accurance...why?  Kubuntu just doesn't work.

I try to update it, BANG "Sorry, Kubuntu can't update, what do you think this is?  A decent operating system!?"  Constantly giving trouble in the middle of attempting to install the updates.  Then I think, oh well, I'll install the Start-up manager so I can give the worthy Windows the priority over this problematic operating system.  "Oh oh, you can't do that, Adept is pathetic and wants to recover, do you want to?" So I go for it, BANG "Yup, it's crashed again".

You guys complain about Windows?  Vista has miles less bugs than this!  I've seen that crash screen so many times I feel like I'm good friends with it.

---

### Post by JoshuaRL on 2008-01-13
What is your hardware?  And how did you install KDE, a fresh install or just the desktop?  What is the exact error messages encountered when updating and trying to recover Adept?  Not sure I can help, but I'll try.  And if you give us those things we might be able to find the problem.

---

### Post by meanburrito920 on 2008-01-13
I understand your pain, having been in a similar situation myself. However, you have to realize that Linux isnt a system for everyone. If you want to go back to windows, feel free. No one is stopping you.  But please consider the following first. All of the *buntu distros are aimed towards making the system as friendly as possible. We know we can't be perfect at this, which is why we need people like you, people who have these problems, to come to the community and the developers and allow them to know that there is a problem. This will allow people that genuinely want to help you to be able to do so (and there are plenty of them). Heck, if you are feeling motivated you could even try and fix it yourself! You just have to realize that the *buntu community is not a big company that you can simply get mad at and hope they fix your product. We are not trying to sell anything, or make any product. We are simply trying our best to give back to the software we use. 
     *buntu runs differently on every system it is installed on. Some hardware it likes. Some hardware it doesn't. You, or any one of us, could be the person that makes it usable where it never could be used before. If you want to be part of that, a part of that community, of that generosity, then please, welcome to the *buntu community. If you do not want to be a part of that, and simply want to be able to complain over the flaws you find in *buntu, please feel free to go back to windows. I dont want to be harsh, but if you have that opinion, the community could do better without you.

---

### Post by ObsessedMikey on 2008-01-13
> **JoshuaRL said:**
> What is your hardware?  And how did you install KDE, a fresh install or just the desktop?  What is the exact error messages encountered when updating and trying to recover Adept?  Not sure I can help, but I'll try.  And if you give us those things we might be able to find the problem.

Okay, I'm on a HP Compaq Presario V6000 laptop, I won't bother going through all the specs cause obviously they're not gonna effect it but I'm using a Mobile Intel 965 Express Chipset graphics chip, and my sound is a Intel HD Audio Controller.

I decided to install a fresh install of KDE actually (which I'm now regretting).

As for good old Adept, firstly the updater (which I can't actually find right now but it happened when Kubuntu decided it was time for a good old update) came up to say it couldn't install all the updates.  And secondly, when I open Add/Remove programs now, or the package manager which is also unfortunatly Adept on Kubuntu, returns an error message every time I open it stating that "Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude)"  It asks if I would like to resolve the problem if I state yes it crashes guranteed every time.  When I say crash, I mean I see that "The KDE Crash Handler" screen that I seem to see plenty of in Kubuntu.

Another problem I'm having is that of the KDE Wallet Service, why do I have to keep inputting a password every single time I turn on my computer so it can get online?  Ubuntu worked fine without stuff like that.

Oh and also Kopete will not connect to MSN, cause guess what, it crashes! lol.

Please help, I've decided to go back to good old Windows permantly and exclusivly if I can't fix the problems soon, all this Ubuntu and Kubuntu stuff really isn't worth all the bother when I can quite happily play around on Windows problem-free :)

---

### Post by JoshuaRL on 2008-01-13
So when you installed KDE did you do it this way:

```

sudo apt-get install kubuntu-desktop

```

or did you go and download KDE from the makers and install it?

---

### Post by ObsessedMikey on 2008-01-13
> **JoshuaRL said:**
> So when you installed KDE did you do it this way:

```

sudo apt-get install kubuntu-desktop

```

or did you go and download KDE from the makers and install it?

Nu huh, I wanted a fresh install so I downloaded the Live CD, and installed it, formatting the old partition that had Ubuntu on it and installing Kubuntu on it instead.

Is Kubuntu less supported/popular or something?  It just seems hardly anyone is using it, and also the problems I'm having just wouldn't happen with Ubuntu.

---

### Post by Linuxratty on 2008-01-13
If you want to use a KDE Linux,you can run live mepis7,or Klikit, as examples and see how they do.

---

### Post by icechen1 on 2008-01-13
> **ObsessedMikey said:**
> Nu huh, I wanted a fresh install so I downloaded the Live CD, and installed it, formatting the old partition that had Ubuntu on it and installing Kubuntu on it instead.

Is Kubuntu less supported/popular or something?  It just seems hardly anyone is using it, and also the problems I'm having just wouldn't happen with Ubuntu.

If Kubuntu don't work for you,try other distros(like PCLinuxOS,MEPIS and many more) (maybe back to ubuntu?).What's good with Linux is that you will **always** have choice.

---

### Post by JoshuaRL on 2008-01-13
So when you did your fresh install were you connected to the internet?  What I'm wondering about is if you have all the repositories, including the update one?  Because if you're not connected at the time of install then it will by default turn off all the repositories.  So that might be your update problem.

From what I've seen Gnome is more popular than KDE, but not by a huge amount.  In fact, a lot of the old guard run or have run KDE because they prefer the interface and tweakability.  So I don't think that's the issue.  Plus, that shouldn't mess with the updates.  It's just the desktop manager.

And as far as Adept, I have no idea.  I haven't messed with it at all.  Hopefully you can find something about that or if we solve the update issue you can post a dedicated thread about Adept.

---

### Post by mivo on 2008-01-13
Kubuntu isn't the best choice for a KDE-based distro, in my opinion. I love Gnome-Ubuntu and have no troubles with it (it also doesn't have to look boring -- hop over to gnome-looks.org and have a look around), but when I tried Kubuntu, I had some apps crash on me various times. I have a KDE installation running on an Arch Linux system, and it is rock-stable.

So, I agree that Kubuntu isn't the most stable KDE distro out there, but I also think the troubles you described are not typical or common. Sounds more like a faulty installation, actually, or sub-optimal configuration.

---

### Post by chewearn on 2008-01-13
> **ObsessedMikey said:**
> 
Please help, I've decided to go back to good old Windows permantly and exclusivly if I can't fix the problems soon, all this Ubuntu and Kubuntu stuff really isn't worth all the bother when I can quite happily play around on Windows problem-free :)

I'm sure if you really think about it and be honest with yourself, you will admit that Windows is not problem free.

I normally direct new users, facing "growing" pains to this post:
[http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)

We are here to help you solve the problems; in return, we hope you will focus on solving the problem, and refrain from trashing our favorite OS, thank you. ):P

---

