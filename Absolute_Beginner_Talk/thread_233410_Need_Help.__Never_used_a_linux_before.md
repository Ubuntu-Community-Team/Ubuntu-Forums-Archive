---
title: "Need Help.  Never used a linux before"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Rxq on 2006-08-10
Windows keeps crashing, so i switched to UBUNTU LINUX.

1. How do i install things? Particually the driver of my wireless adapter so i can on ONLINE? And after that what do i do? Where do i navigate to to find the networking options and select my signal?
2. Everytime i log in it ask for my password. How do i eliminate that and go straight to the desktop?
3. I notice a few obvious differences from windows. What else is there? Such as key commands and etc? Wheres the program menus?
4. How do i install windows apps? Is there like a virtual windows for it?
5. What else do i need to know about linux/ubuntu?
6. How does this version differ from any other linux?

---

### Post by Kurt` on 2006-08-10
I don't have enough to time answer all of your questions, but here's one anyways.

2) Follow this guide: [http://ubuntuguide.org/wiki/Dapper#How_to_automatic_login_into_GNOME_.28not_secure.29](http://ubuntuguide.org/wiki/Dapper#How_to_automatic_login_into_GNOME_.28not_secure.29)

Good luck with your Linux experience!

---

### Post by SeaRox on 2006-08-10
I'm pretty new to linux and ubuntu myself so I don't know how much help I can be, but while you are waiting for more experienced people to answer your questions check out this thread.

How to help yourself.
[http://www.ubuntuforums.org/showthread.php?t=142716](http://www.ubuntuforums.org/showthread.php?t=142716)

Your questions sound pretty common so, I think if you look around a bit you will be able to find answers to most of your questions.

For installing things I would check out the wiki and help.ubuntu.com or do a search for your wireless card in these forums.  You could probably find the answer to your password question around in here somewhere too.

If I'm not mistake "wine" is a windows emulator or some such thing that will help you with windows apps.

As for what to know about linux.  The applications menu on ubuntu is in the upper-left by default.  There is tons of info on the different versions of linux (distrowatch.com is a good one), what else you need to know, and on linux commands.

Besides the Ubuntu site, you can look on linux.com, linux.org, and I've seen several people in these forums recommend [www.google.com/linux](www.google.com/linux).

I hope this helps you find some useful info.

---

### Post by Arkian on 2006-08-10
A lot of typical questions from a new Linux User. I asked them a few months ago :p 

About your #2 question try this:

Press System
Press Administration
Press Login Window
Press Security 'tab'
Check Enable Automatic Login

Haven't tried it myself and value the login part of any OS because of the involved security.

---

### Post by SeaRox on 2006-08-10
For your wireless card issue the desktop guide ([https://help.ubuntu.com/pdf/ubuntu/C/desktopguide.pdf](https://help.ubuntu.com/pdf/ubuntu/C/desktopguide.pdf)) has a section on wierless cards and suggests this website if your wireless card is not automatically detcted.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by SeaRox on 2006-08-10
This is another good site to help you as you get into Ubuntu.

[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

---

### Post by drtvasudevan on 2006-08-10
> **Rxq said:**
> Windows keeps crashing, so i switched to UBUNTU LINUX.

> 1. How do i install things? Particually the driver of my wireless adapter so i can on ONLINE? And after that what do i do? Where do i navigate to to find the networking options and select my signal?
search forum
[QUOTE]2. Everytime i log in it ask for my password. How do i eliminate that and go straight to the desktop?
answered already

> 3. I notice a few obvious differences from windows. What else is there? Such as key commands and etc? Wheres the program menus?
for programs pull down the menu from top left
lot of things are there. take your time and explore.
you wont really need commands as most of the routine is in gui
of course learning them and using is a cool thing.

> 4. How do i install windows apps? Is there like a virtual windows for it?
wine

> 5. What else do i need to know about linux/ubuntu?
mainly that it is not windows.
it is different in a lot of ways.
dont compare them.
if you like ubuntu and comfy with it stick with it.
it is a bit exasperating at the begining but soon you will get used to things.
look at the wiki and howtos and search the fora for answers first.
if there is anything not answered there people are here to help.
there is also help in the system menu.
save the guides that you see.
you may need them later.

6. How does this version differ from any other linux?[/QUOTE]
more user friendly is my verdict

---

### Post by nalmeth on 2006-08-10
Did you click the READ THIS FIRST BEFORE POSTING sticky note in the beginners section? If not, you should. 

If you're really fresh to linux, the WirelessTroubleshootingGuide will likely be too much.

First, let's see if you can just activate it and it works. 
Go to System -> Administration -> Networking

See if the wireless device is there, and try to activate it. 

If it isn't there, or won't activate, go into System -> Administration -> Device Manager, and see if you can find a wireless device there. Post what you see, even if it says unkown model or device.

To learn how to install anything in Ubuntu, see this link:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

When you get wireless up and running, you will want this to install some important stuff you're probably used to in windows:
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Wine is a *windows compatibility layer* but before you try that, see if there are linux alternatives for the apps you need, likely there are. Here is one list from the forums here to start:
[http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)

Wikipedia can explain whats up with ubuntu:
[http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29](http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29)

---

### Post by Rxq on 2006-08-10
> **Arkian said:**
> A lot of typical questions from a new Linux User. I asked them a few months ago :p 

About your #2 question try this:

Press System
Press Administration
Press Login Window
Press Security 'tab'
Check Enable Automatic Login

Haven't tried it myself and value the login part of any OS because of the involved security.

This did not work.

I also went to system>administration>networking, found my card
and enabled teh Wireless adapter and found my network.  A loading menu pops up and about 5 minutes later it closes.  Unfortunately i am still not online.

---

### Post by MetalMusicAddict on 2006-08-10
> **Rxq said:**
> This did not work.

After clicking the checkbox you noticed that field below turn white right? Did you enter you user or scroll through with the arrow?

---

### Post by nalmeth on 2006-08-10
[QUOTE=nalmeth]
If it isn't there, or won't activate, go into System -> Administration -> Device Manager, and see if you can find a wireless device there. Post what you see, even if it says unkown model or device.[/QUOTE] /

---

### Post by drtvasudevan on 2006-08-11
you must be having other prblems of net but do this first just to eliminate a  hitch.
in the firefox address bar type about:config and in the filter bar type ipv6 and change from false to true just double click it 
try this
in the firefox address bar type about:config 
and in the filter bar type ipv6 
and change from false to true= just double click it 
shutdown firefox
restart firefox.

---

