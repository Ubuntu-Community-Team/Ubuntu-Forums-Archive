---
title: "Which is best?"
date: 2008-04-01
forum: Apple PPC Users
---

### Post by faelin on 2008-04-01
Ok, I have an old iMac G3 400MHz with 1GB RAM.
Currently it is running OS X 10.4.11 ok. But I a, really starting to feel the burden. Mostly my wife and daughter use it the most.
At my office, I have been playing with/learning the beta 2 of the gOS and Ubuntu 7.10 and really like both.
What I would like to do, in an ideal world, is install the gOS for my wife since it's ready-to-go for her to check email and browse... that's about all she does. And I would sync her ipod to it... no biggie.
But I want to also install Ubuntu, or maybe Xubuntu for my daughter (9) to play with. The thought for her is that I will teach her HOW to find the answers online, but let her learn for herself how to use a computer the "hard way". I am sick of all the spoiled kids who only want to "play" and not try to understand how to properly use a computer. I don't think I'll have much issue with the dual-boot, since I have it on the Dell at my office, but the 400MHz speed concerns me.
Can that old G3 handle the gOS? It's got great RAM speed and I read that Ubuntu taxes RAM more than processor. 
I also read that Xubuntu is perhaps the best for the older iMacs, but I really like the KDE environment and Gnome, too. I am yet unfamiliar with the Xfce one. Can the iMac handle Ubuntu or Kubuntu well?

I am really new to Linux, but I would say that the last couple of weeks has certainly made me a "fan-boy" for sure! Apple has done some very microsoft-like things lately and they have left a bitter taste, company wise. I still love Leopard, but I see a time when I may move solely to Linux coming.

I appreciate any help and feedback. Thanks

Any help

---

### Post by rev7 on 2008-04-01
Either one, since gOS is Ubuntu, with the addition of Avant Window Manager (to mimic the OSX dock) and some links to Google apps.  I started with gOS on my Everex and am now running Hardy on it.  The update was done using the Synaptic Package manager, not a fresh install.  So you could start with gOS and switch... Mac users will probably want to start with gOS, as it sets the close, minimize, and maximize buttons on left-- Mac style.  (Updating to Hardy did not change this.)

As to speed with various window managers-- install and try them all out.  You can easily add and remove KDE, Gnome, Xfce, etc...  So long as you have some time on your hands.

Whichever Ubuntu route you choose, you'll be able to get answers to most of your questions here. 

Another distro you might want to look into is 'Yellow Dog Linux.'  Ubuntu is no longer officially supported on PPC, but YDL is-- and is exclusively PPC.  It's a REDHAT distro, not Debian, so you won't get much support for it here-- but it will install properly out of the box.  (I ran YDL on my B&W G3 for a couple of years before reinstalling OS X and donating it to a student.)

Cheers!

---

### Post by stream303 on 2008-04-01
> **faelin said:**
> Ok, I have an old iMac G3 400MHz with 1GB RAM.

Nice!  That is roughly equivalent to an 800mhz x-86 box, and a very nice amount of ram.  No problems there.

> What I would like to do, in an ideal world, is install the gOS for my wife since it's ready-to-go for her to check email and browse... that's about all she does. And I would sync her ipod to it... no biggie.

Ubuntu (or any of the variants) should handle that nicely, although I have no experience with iPod syncing.

> Can that old G3 handle the gOS? It's got great RAM speed and I read that Ubuntu taxes RAM more than processor.

Should be fine, and it taxes ram no more than any other architecture.  I think the reason you may have heard that is from those who try to use low-spec Mac with only 64-128mb ram and find it rough going with a heavyweight like Ubuntu.

> I also read that Xubuntu is perhaps the best for the older iMacs, but I really like the KDE environment and Gnome, too. I am yet unfamiliar with the Xfce one. Can the iMac handle Ubuntu or Kubuntu well?

Easy - especially with your large amount of ram.  You can install Ubuntu, and afterwards add both Kubuntu (kde) and Xubuntu (xfce) desktops, and choose which "session" to use at login.  You can do it in Synaptic, or manually from the commandline:
```

sudo aptitude install kubuntu-desktop
and / or
sudo aptitude install xubuntu-desktop
```

Of course this will pull in all the related desktop programs and utilities for those environments as well.  So you can pick and choose and later delete those desktops you don't care for.

> I still love Leopard, but I see a time when I may move solely to Linux coming.

Great - no need to give it up, although some have no need for OSX.  Although PPC is no longer officially supported, you can see that unofficial support is alive and well here amongst the many enthusiastic members.  As long as they provide download repo's, I think we've got a bright future.  I don't care for the fact that they don't mention unofficial support on the download page, and it can lead some to think that only the older Dapper 6.06 is the last version of Ubuntu available.  For unofficial versions beyond that, downloading repositories are available and can be found in the faqs and threads.  It will be interesting to see if they mention the upcoming Hardy on the download page for ppc'ers.  In any case, anyone doing an internet search will be able to see that unofficial versions coming from Ubuntu's own repositories are actually available.

Sometimes a PPC install needs a little TLC to get going, and the members and faqs here should be able to guide you without too many problems.  Sometimes it involves editing a file or two, and if you pull up a terminal in OSX, you can get a little practice with the bash shell, and the nano editor in particular.  You can even get your feet wet with the vi editor in OSX.  Although many of us have no fear of the commandline, usually it can be avoided after just an edit or two if it comes to that.

You've come along at a good time since I really like how Hardy is shaping up, and will be released in April.  The older Feisty and Gutsy are doing ok, although in some cases, and edit or two of a config file is necessary.  No problems.

Welcome aboard!

---

### Post by faelin on 2008-04-01
Many thanks to both of you, Stream and Rev.
I am about to start with the gOS. I backed everything up last night. So if worse comes to it, I can just reinstall Tiger.
I did look at Yellow Dog, too. But:
1) I am most familiar with the Ubuntu/Debian style
2) YDL looked more like OS 9. My wife is very limited so I think the gOS will suit her well and my daughter has only use OS X* (no Win-blows for her)
But I want something with an easy-to-navigate GUI like ubuntu, but I want to force her to learn. I told her I will teach her HOW to look for answers, but the rest is up to her.
I do not want her to be complacent in taking technology  for granted like most kids today, and Linux is the perfect community and architecture for her to learn from. But I want the experience to be graphical enough to keep her entertained (she's not quite 9 yet). So I think Ubuntu will be a "best of both worlds scenario.
Again, thanks to you both. I think I am gonna like it here :guitar:

---

### Post by 3rdalbum on 2008-04-02
Is gOS actually available for PowerPC?

That Mac can handle Ubuntu or Kubuntu since you have a good amount of RAM. But I believe the hard disks in those machines are a bit slow, and of course the processors are ancient.

I'd still point you toward Xubuntu. It's not really that much different to Gnome.

---

### Post by faelin on 2008-04-02
Well, I have been having a hard time all around.
First of all, the gOS will not install... pity. I really think it would be perfect for my wife. 

The ubuntu Live cd I burned is the one designed for PPC machines and when I try to run it, i get the normal: ( I assume it's normal)
Welcom to Ubuntu 7.10 (Gutsy Gibbon)! 

....

If the system fails to boot at all (the typical symptom is a white screen which doesn't go away), use 'live video=ofonly'


---
First i tried pressing enter, which it says by default will boot: live

it says it is loading kernel, then I get " Read Failed"

I try boot:live.... same thing

then I tried the boot: live video=ofonly like it said.... same thing

any thoughts?
do I need to partition my HD a certain way? It is currently standard running OS X Tiger. All of my data is backed up, so I don't mind re-formatting. But after much ado yesterday, I just freshly installed Tiget last night because the Ubuntu disk said I had a file system error, now it just won't read it at all...
I want the whole HD to be Linux... HELP, please.

---

### Post by oswaldkelso on 2008-04-02
A bit old but useful 

[http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)

---

### Post by stream303 on 2008-04-02
Even though you have a large amount of ram, many consider using the "alternate" non-live cd installer the best just to cut down on the amount of weird variables.

Have you tried burning the alternate install iso image at a very low speed, like something ridiculous at 4x ?

Perhaps the issue is speed related with that older drive, possibly dirty lens, etc.

---

### Post by faelin on 2008-04-02
oswaldkelso and stream303,
both good ideas and resources. thanks. i am trying everything.
I am also downloading Yellow Dog Linux. I may have to go that route. I really want to stick with some form of Ubuntu, but I'll do what I have to do. Simply, this machine can't keep running OS X much longer, so I need to do something with it, or risk losing it.
Thanks to all.
I am always open to more ideas!

---

