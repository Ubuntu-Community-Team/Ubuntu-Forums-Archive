---
title: "Fluxbuntu vs. Xubuntu"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-01-20
I am hoping to start a discussion as to the differences between Fluxbuntu and Xubuntu. Please try to keep them technical I don't want any, "Xubuntu is the shiznat!!!!!".

Bottom line is I'm installing one of the two on an older computer I have, details aren't really important if its that important to you, you can search my posts, and see what I'm talking about, I really would like to know which of the two would optimize hardware the best.

If it helps the computer is a pentium III with 128mb RAM, but that's as technical as I'm getting. I realize there are other similar threads, but I want one that is basically two groups comparing and contrasting so that I an others can finally understand which of the two is better.

PS: I don't care about what software comes with them as anything can be installed. I'm basically just talking about the kernel and how much it uses system resources.

---

### Post by p_quarles on 2008-01-20
The kernel is the same for both, so no need to discuss that.

The main difference between the two is the graphical environment. Xubuntu uses Xfce4, which is slightly lighter than Gnome (the default for Ubuntu and several other Linux distros). People *say* it's designed for older computers, but a PIII with 128 MB of RAM is pushing it. It will be slow. Fluxbuntu uses the Swift login manager plus the Fluxbox window manager. You shouldn't expect miracles, but it will certainly perform much more efficiently than Xubuntu on your machine.

Fluxbuntu is configured very nicely to begin with, but changing the configuration will require you to edit text files. Xubuntu has a greater number of intuitive GUI configuration applications. Essentially, yes, you can install anything available in the Ubuntu repositories in either one. The difference is that Xubuntu's menu will update automatically, whereas you'll have to update Fluxbuntu's menu by either A) running the command line menu update program, or B) manually editing the menu file. 

Summary: Fluxbuntu will be considerably faster. Xubuntu will be easier for those who don't have much command line experience in Linux.

As for me: I run Fluxbox installed on top of a minimal Ubuntu. My computer could easily run Vista, but I find that the lightweight window manager is a great way to squeeze performance out of *any* computer. So, it's not *just* for older computers. ;)

---

### Post by Dr Small on 2008-01-20
I would definately go with Fluxbuntu with 128MBs of RAM.
Xubuntu is considered lightweight, but it is only slightly ligher than Gnome and most likely wouldn't run to well on 128MBs of RAM.

Personally, I would install a minimal ubuntu and go for IceWM :)

Dr Small

---

### Post by Kilz on 2008-01-20
128 megs or ram is real low memory. [This page of the Ubuntu wiki may be of some help to you.]("https://help.ubuntu.com/community/Installation/LowMemorySystems")  You might also consider [icewm]("https://help.ubuntu.com/community/IceWM") with rox filer.

---

### Post by louieb on 2008-01-20
As the others have stated FluxUbuntu is much lighter that Xubuntu. Have an old P2-400mHz 384mb ram. Did have xUbuntu and FluxUbuntu dual booting. On that PC FluxUbuntu ran faster. 
The downside of FluxUbuntu is its not as feature filled as xUbuntu.

If you want to see a really nice lightweight Fluxbox setup try [PCFluxboxOS:]("http://pcfluxboxos.wikidot.com/")  On the ole P2 its what I'm now running. 

BTW just noticed the latest versions of DSL now use JWM think I'm going to give it another spin.

---

### Post by rosegarden78 on 2008-01-20
I installed XFCE after installing Ubuntu.  I could have obtained a Xubuntu disc from Canonical.  I'm not sure you can obtain a Fluxbuntu disc.  It seems you should start with a clean install of Xubuntu Gutsy Gibbon.  Then install your secondary Fluxbox environment.  I'm not sure the difference is speed would be marginal at best but I would like to try the experiment myself.

Fluxbox is available from Synaptic Package Manager.  I'm installing it right now here are my basic figures:
Kubuntu >= 450 MB
Ubuntu >=450 MB 
XFCE >= 55 MB 
Flux >= 6.7 MB

---

### Post by rosegarden78 on 2008-01-20
OK I logged in with Fluxbox it seems totally useless for me at first glance.  The winner seems to be Xubuntu because you save more time with the productivity tools and GUI.  Try it and see!  Fluxbox is a completely empty blue screen with a little scrollbar on the bottom and nothing else at first glance.  But once you figure out how to run the terminal it becomes a different matter.  You can run nautilus for your desktop and now we're back in black.

---

### Post by JoshuaRL on 2008-01-21
I don't know whether this will make any difference to you, but Flux feels like a lightweight desktop.  Things just look and work differently.  XFCE feels more like a slightly smaller and slightly different version of Gnome.  But it runs much faster and on a smaller footprint, both on disk space and system resources.

I haven't spent much time on Flux, only a live CD from Linux Mint that I used for a little bit.  But I didn't like it much.  It felt bare and unfinished to me.  And that's on Mint!  So, I don't personally like it much.  But if that doesn't make a difference to you, go ahead.  You'll definitely get better performance out of it.

---

### Post by JoshuaRL on 2008-01-21
> **rosegarden78 said:**
> OK I logged in with Fluxbox it's totally useless for me.  The winner is Xubuntu because you save more time with the productivity tools and GUI.  Try it yourself!  Fluxbox is a completely empty blue screen with a little scrollbar on the bottom and nothing else.

Well, you have to know how to use it.  It took a while of me randomly trying things to figure this out:

Flux doesn't have an Application bar.
Flux has a menu bar, but it's incredibly tiny.
To configure the menu bar, right click it.
To open the Application menu, right click the desktop.

It was just too different and too flimsy for my tastes.  But when I get my server running and if I need a DM for anything, I might just go with it.  It's almost as fast as a headless system.

---

### Post by rosegarden78 on 2008-01-21
> **rosegarden78 said:**
> OK I logged in with Fluxbox it's totally useless for me.  The winner is Xubuntu because you save more time with the productivity tools and GUI.  Try it yourself!  Fluxbox is a completely empty blue screen with a little scrollbar on the bottom and nothing else.  Now if you want a real argument try Zenbox vs. Xubuntu.  You may consider trying Zenbox next!

Sorry ... Zenwalk.

Hey guys guess what?  I'm using BlackBox and I'm loving it!  I'll tell you what I did:

1) Install Ubuntu then add kde, xfce, fluxbox and blackbox window managers
2) Select BlackBox session as default
3) Write go script

go script type "nano go" to create
------------------------------------------------------
xgamma -gamma 0.75
nautilus

4) IMPORTANT: sudo chmod 755 go
5) Type bash go or simply ./go

Now you're running Nautilus.  You need to a create launcher for "terminal" run terminal and type: 
nm-applet
this will run the network manager panel but without the GUI.

Try it and see!

---

### Post by wolfen69 on 2008-01-21
Tinyflux [http://pcfluxboxos.wikidot.com/tinyflux](http://pcfluxboxos.wikidot.com/tinyflux) is a great do all flux desktop. comes with some great apps and has all codecs, flash, java etc. it's awesome.

---

### Post by p_quarles on 2008-01-21
> **rosegarden78 said:**
> OK I logged in with Fluxbox it's totally useless for me.  The winner is Xubuntu because you save more time with the productivity tools and GUI.  Try it yourself!  Fluxbox is a completely empty blue screen with a little scrollbar on the bottom and nothing else.  Now if you want a real argument try Zenbox vs. Xubuntu.  You may consider trying Zenbox next!
Installing Fluxbox on top of Ubuntu isn't even vaguely similar to installing Fluxbuntu. Try it yourself. ;)

---

### Post by Majorix on 2008-01-21
Xubuntu because it is officially supported by Canonical. Fluxbuntu is NOT official.

---

### Post by rosegarden78 on 2008-01-21
> **Majorix said:**
> Xubuntu because it is officially supported by Canonical. Fluxbuntu is NOT official.

Yes but Blackbox is the smallest and fastest desktop that I have tested.  I updated my last post with instructions for Blackbox setup with Nautilus and network manager.

---

### Post by rosegarden78 on 2008-01-21
8)

---

### Post by rosegarden78 on 2008-01-21
Would anyone consider suggesting a reliable source to download Fluxbuntu?  I'm told Fluxbox is a completely different entity than Fluxbuntu.  It would be interesting for me to conduct an experiment to compare it to Fluxbox and Blackbox.

---

### Post by hyper_ch on 2008-01-21
install tehm both, check them out, chose the one you like more.

---

### Post by Majorix on 2008-01-21
> **rosegarden78 said:**
> Would anyone consider suggesting a reliable source to download Fluxbuntu?  I'm told Fluxbox is a completely different entity than Fluxbuntu.  It would be interesting for me to conduct an experiment to compare it to Fluxbox and Blackbox.

[Here you go]("http://wiki.fluxbuntu.org/index.php?title=Get"), however I wouldn't rely on it too much, as it is not even a stable Gutsy yet, it says 7.10rc. Very odd. Gutsy is out for like what? 3 months? And still no stable release of it? :)

---

### Post by Dr Small on 2008-01-21
> **Majorix said:**
> Xubuntu because it is officially supported by Canonical. Fluxbuntu is NOT official.
Would it being official really make the decision for me??
That's like saying, "I'll use Windows because Microsoft supports it, and not Linux."

Similar, but hey, just because it is unofficial doesn't mean it won't work ;)

---

### Post by Majorix on 2008-01-21
Officially supported by Canonical means in my eyes more professional developers and more time spent developing, and better community support. So yes, I will choose Xubuntu over Fluxbuntu or similar.

---

### Post by whoscheesemine on 2008-03-01
Hey guys!

I know I haven't posted the entire thread as I've been wicked busy, but there's a lot of god information here and I think I'm going to try all of the mentioned! After using Ubuntu, Xubuntu, and Fluxbuntu it did seem as though Fluxbuntu was the hardest one to get used to/learn.

So long all!

---

