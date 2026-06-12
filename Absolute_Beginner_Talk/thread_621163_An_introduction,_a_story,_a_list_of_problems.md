---
title: "An introduction, a story, a list of problems"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by DMBrazil on 2007-11-23
Hey everyone, My name is Leo and am on my first full day with Ubuntu (xubuntu actually). I'd like to think I knew alot about Windows (XP Pro) but I've never been so confused in my life now! Heres my story (feel free to skip haha) :

I came home from college for Thanksgiving fully expecting to purchase the desktop I've been configuring for the last 3 weeks (Dell 531, AMD 5600+, 3G RAM, GeForce 256MB, 320 GB HD, 22" Samsung Widescreen... etc). Due to some car troubles, a flight to Brazil coming up and some Black Friday Deals I couldnt pass up; My Dell 531 is going to have to wait till this summer. That being said I needed to do something about how slow my Dell Inspiron 1100 (laptop) was running. Having a couple first being DIE HARD Linux fans, I figured... why not? And after reading about Xubuntu, I knew it was the OS for me. (Not to mention some of the Youtube videos on old computers with Xubuntu and Compiz and how amazing they worked!) So I saved all my un-replaceables and wiped everything off and install Xubuntu as my only OS and partition. GOODBYE WINDOWS- COLD TURKEY!!! After a hand full of problems with the installation (which were all solved on this forum.. THANK YOU!!!) I finally got a up and running ubuntu on my Dell 1100 at 3:40 AM this morning. After a couple hours of sleep I'm back at it! First thing is first: Get my most used programs back (Firefox, iTunes, VLC Media Player, MSN Messenger, etc). Right away I notice that Firefox is already installed: "MAN THIS IS GONNA BE EASY IS PIE" I thought. 

I was wrong. I've never been more confused in my life.

Problems/Questions:
After reading countless pages on apt-get.. I still cannot seem to work it. One of the first programs I went to get was iTunes.. No such luck but through this forum I've found Amarok. Went to amarok's website and found the Debian Install is just type    # apt-get install amarok   . No luck. So I thought "Ok, maybe there is a Youtube video on how this works" Go to youtube. No flash plugin installed. Went to the website and didnt see a apt-get but instead a tar.gz file. Tried opening that.. nothing to open with. Ok so I head back on the forums and most of the advice I'm finding is in Terminal which doesn't seem to work or the links are bad. HELP?

How do solve the problems above?

Is there an "control panel" where I can start customizing things? 

Can I have different backgrounds on different work spaces?

What are the must-have programs? (Remember I have NOTHING right now)

What is Fiesty? 

Are there keyboard shortcuts? (Minimize all, View all, Move to another workspace).

Is there a list of alternative programs. such as Amarok for iTunes?

Why did I do this?  :lolflag:

Any help would be much thanked and who knows maybe this can turn into the Step by Step Noob guide to getting started on Ubuntu!

Thanks in advance. 

PeaceLoveUnity

---

### Post by asmiller-ke6seh on 2007-11-23
> **DMBrazil said:**
> --CLIP--------------------%<------------------CLIP-------------------
Problems/Questions:
--CLIP--------------------%<------------------CLIP-------------------
Went to amarok's website and found the Debian Install is just type    # apt-get install amarok   --CLIP--------------------%<------------------CLIP-------------------

**-> Did you include the "#" in your input? It is not supposed to be included in your input in Terminal.**

How do solve the problems above?

Is there an "control panel" where I can start customizing things? 

**-> There is not just one control panel. For example, instead of Windows Control Panel - Add/Remove Programs, there is Synaptic - this is a graphic alternative to APT-GET in Terminal.**

Can I have different backgrounds on different work spaces?

**-> There are ways , but why not be patient and leave this one aside for now ... it's just eye candy, and you have more basic things to tackle, first.**

What are the must-have programs? (Remember I have NOTHING right now)

**-> You already determined what your must-haves are.**

What is Fiesty? 

**-> Feisty (Feisty Fawn) is the release just prior to Ubunty 7.10 (Gutsy Gibbon) and Gutsy is the most current release. Feisty was released earlier this year. Ubuntu releases updated versions every 6 months.**

Are there keyboard shortcuts? (Minimize all, View all, Move to another workspace).

**-> There are keyboard shortcuts, but I advise you to take things one step at a time: Linux is not Windows, and you have will be dealing with some cultural adjustments for a little while.**

Is there a list of alternative programs. such as Amarok for iTunes?

**-> If you want to be buying music from the iTunes store, or using AAC format with DRM (Digital Rights Management - ugh!) protection, you may have a bit of a steep learing curve to go through. I would put this one on the back shelf, for now, until you have tackled a bit more in Ubuntu that's probably more basic and more important.**

Why did I do this?  :lolflag:

**-> Probably for the same reason most of us got involved -- the need for Freedom and personal choice and because of the promise of higher performance at a lower price.**

Any help would be much thanked and who knows maybe this can turn into the Step by Step Noob guide to getting started on Ubuntu!

**-> I suggest that you break up your needs into separate topics, post a new and separate thread in on each of the items you are working on. It will make your life easier, you will more likely get focued attention on each separate topic, you and the people working with you will be more organized (e.g., less confused). Also, by breaking each topic separately and focusing on each topic separately, you are more likely to find the answer you are looking for is already covered her. You first step is to search for a look at the many HOW TOs that are all over this forum.**

Thanks in advance. 

**-> Your welcome, in advance. My advise to you is first learn about how software is installed and uninstalled using REPOSITORIES. Next, I think you would benefit from learning how to install the required third-party CODECS. Next, you may want to learn about the various important third-party BROWSER PLUGINS. This will form a basic foundation for much of the rest of what you are looking to learn how to do.**

PeaceLoveUnity

**-> Stick with it. What you learn here will really pay off in the long run**

---

### Post by aysiu on 2007-11-23
Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by aktiwers on 2007-11-23
>  Went to amarok's website and found the Debian Install is just type # apt-get install amarok 
No you type:
```
sudo apt-get install amarok
```
 don't include that #.
>  Is there an "control panel" where I can start customizing things? In the System menu there are 2 other menu's. Preferences and Administration. There is all you expect form a control panel.
>  Can I have different backgrounds on different work spaces?In Gnome (the ubuntu default shell) I have heard this is not easy, or at least not worth the trouble. But maybe someone else can help you out here.
>  What are the must-have programs? (Remember I have NOTHING right now)What programs do you need? There are a lot of programs in the Applications menu, of as PeaceLove Unity talks about, you can install lots through System => Administration=> Synoptics
>  What is Fiesty? The Version of Ubuntu that was before Gutsy..  Like XP is before Vista.
>  Are there keyboard shortcuts? (Minimize all, View all, Move to another workspace).Yes you can find them and change them in System => Preferences => Keyboard Shortcuts
CTRL+ALT Right and left arrow  turns to next desktop.
>  Is there a list of alternative programs. such as Amarok for iTunes?[http://ioannusdeverani.wordpress.com/2006/09/30/awesome-itunes-alternative-works-on-linux/](http://ioannusdeverani.wordpress.com/2006/09/30/awesome-itunes-alternative-works-on-linux/)
>  Thanks in advance. No problem, good luck and welcome to Ubuntu

---

### Post by asmiller-ke6seh on 2007-11-23
> **aysiu said:**
> Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

:guitar: That is a great link!!!

---

