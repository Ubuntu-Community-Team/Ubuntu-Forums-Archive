---
title: "2 question! Help needed!"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-05-25
Hey all.
Here are another 2 question ?

1. How to make transparency effect like this :--

][IMG]http://img213.imageshack.us/img213/1112/screenshotcs4.png[/IMG]

2. How can I install a dock in Festive? Plz tell the whole process thanks a lots :)

Regards

---

### Post by aeiah on 2007-05-25
1: that uses beryl. it can also be done with compiz

what video card do you have? the installation process is really simple now but some cards have issues, or need drivers installed etc [wikipedia page for beryl to explain what it is](http://en.wikipedia.org/wiki/Beryl_(window_manager))

2: there are several docks, which one caught your eye?

---

### Post by Dark Star on 2007-05-25
> **aeiah said:**
> 1: that uses beryl. it can also be done with compiz

what video card do you have? the installation process is really simple now but some cards have issues, or need drivers installed etc [wikipedia page for beryl to explain what it is](http://en.wikipedia.org/wiki/Beryl_(window_manager))

2: there are several docks, which one caught your eye?

Can u tell me how to install a dock :(

---

### Post by starcraft.man on 2007-05-25
Uh, I would strongly recommend against all the docks today... they just don't seem to function well, and I've certainly gone out of my way to try a good lot of them (kool dock, kiba, awn dock, gdesklets dock, a few more). They just either seem unstable, or difficult to get working well enough that its usable daily. I personally don't see whats wrong with the bottom bar in gnome. Plus, docks usually eat up quite a few cpu cycles for no real reason...

As for 1, I recommend Beryl. I like it more than compiz, thats just me though.

Here is [link]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy") for installing Beryl/compiz on ATI or Nvidia cards. To install your drivers, use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") rather than the manager. It is just easier and better methinks. Download latest stable version (.9.3 I think) and install it, then go to Applications > System Tools > envy and automatically install your card. Then follow the guide for your choice of manager. You can not only change transparency, but also saturation and brightness and much more with Beryl :).

---

### Post by Dark Star on 2007-05-25
I am not having a good system requirement though a dock would work gr8 suggest a good 1 with installation meathods :)

---

### Post by aeiah on 2007-05-25
[here is a howto for avant window manager](http://ubuntuforums.org/showthread.php?p=2307772), which seems like a popular dock. i too dont like using docks though, as they seem to be unstable.

edit: uh. nevermind, you need beryl/compiz

check out the other ones that are mentioned by starcraft.man i guess

---

### Post by Dark Star on 2007-05-25
Thanks fo r th e guidfe link but where to write these commands 

Installing:

Repository:

NOTE: Repository is for Feisty 32-bit ONLY.

If you are using Feisty 32-bit, this is the recommended method of installation.

Just add this to your /etc/apt/sources.list:
Code:
```

deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator

```

---

### Post by shen-an-doah on 2007-05-25
Actually, to make your terminal transparent, you just have to open a terminal and go Edit > curent profile, then click on the Effects tab.

However, without something like Compiz or Beryl running, it just shows your desktop background, rather than whatever else might be behind it...

---

### Post by Happy_Man on 2007-05-25
First, learn to shrink images. :D

1. You need beryl for that. 
```
sudo apt-get install beryl beryl-manager emerald-themes
```

2. You could try AWN, or Kiba-dock. Tutorials for both floating around these forums, too tired to look. Sorry.

---

### Post by Dark Star on 2007-05-25
You mean I cant install a dock without Berly :(

---

### Post by starcraft.man on 2007-05-25
> **Dark Star said:**
> Thanks fo r th e guidfe link but where to write these commands 

Installing:

Repository:

NOTE: Repository is for Feisty 32-bit ONLY.

If you are using Feisty 32-bit, this is the recommended method of installation.

Just add this to your /etc/apt/sources.list:
Code:
```

deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator

```

1) To answer your question.

To add those to your sources flie you need to open it manually... open a terminal (applications > Accessories > Terminal, type in: (Just a note but every time you see a guide with code indented from the main text, it means put it in terminal 99% of time).

gksudo gedit /etc/apt/sources.list

then copy and paste the two lines on the end of the file save and close. Then run this command in terminal:

```
sudo apt-get update
```

then do whatever is next.

2) To add and further explain.

Let me just make this clear though, I'm not sure if you have been confused by everyone's suggestions. Both (I'm pretty sure) AWN and Kiba need beryl/compiz to work effectively since they depend on their compositing. Without having those installed, you will probably have a more glitchy dock than average, maybe not even open. Those managers in turn require that you have your proprietary drivers installed (be they nvidia or ati). Thus, to get the dock working, the steps you need are as follows, if not already done.

A) Install drivers for card. Use envy, like I linked above.
B) Install Beryl/Compiz (I recommend Beryl, don't hurt me compiz users out there >.<), follow guide I linked to.
C) Continue installing AWN or whatever other dock you want.

Hope that makes it clear, I'd go with just beryl to start. You'd be surprised it runs well on old systems, better than Vista. My old P4 handles it with my somewhat old 6800 GT with no problems at all >.>.

---

### Post by Dark Star on 2007-05-25
> **Dark Star said:**
> Thanks fo r th e guidfe link but where to write these commands 

Installing:

Repository:

NOTE: Repository is for Feisty 32-bit ONLY.

If you are using Feisty 32-bit, this is the recommended method of installation.

Just add this to your /etc/apt/sources.list:
Code:
```

deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator

```

Repeating my question :) Plz tell me where to write these codes:KS Thanks a lot Sir lemme give it a try :)

---

### Post by starcraft.man on 2007-05-25
> **Dark Star said:**
> Repeating my question :) Plz tell me where to write these codes:KS

I just answered :p No double posting, thats illegal :p.

As for your question, no, I don't think any of the main docks work well without Beryl/Compiz. Install one and see if it runs smoothly, you can uninstall them after if you find them unstable/slow. Follow my three steps, should work. As long as you have any ati/nvidia 64 mb card minimum it should work just fine.

Edit: Darn it, editting after I post :p LOL

---

### Post by Dark Star on 2007-05-25
> **shen-an-doah said:**
> Actually, to make your terminal transparent, you just have to open a terminal and go Edit > curent profile, then click on the Effects tab.

However, without something like Compiz or Beryl running, it just shows your desktop background, rather than whatever else might be behind it...

Thanks a lot it worked :)

---

### Post by Kent84 on 2007-05-26
I'm driving to get Beryl working with my ATI card too in Feisty. Envy you mention installs the propriety drivers for my card but the guide assumes that I am using open source drivers. Is that going to be a problem? I find that the propriety drivers work much faster for my Radeon 9600pro.

> **starcraft.man said:**
> 
Here is [link]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy") for installing Beryl/compiz on ATI or Nvidia cards. To install your drivers, use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") rather than the manager. It is just easier and better methinks. Download latest stable version (.9.3 I think) and install it, then go to Applications > System Tools > envy and automatically install your card. Then follow the guide for your choice of manager. You can not only change transparency, but also saturation and brightness and much more with Beryl :).

---

### Post by airtonix on 2007-05-31
Darkstar: avoidz za kiba lollerz qq. lfm dock?? qq roflmao.

god i hate lollerTalk.

---

