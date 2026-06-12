---
title: "Want to try out different WM's. Which Ubuntu flavor? And how?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by kentl on 2007-10-04
Hi,

[SIZE="4"]Background[/SIZE] (jump over this heading if you don't like rants ;))
I've used Linux on and off for a couple of years. While I absolutely love it on my little home server I've not yet found the window manager of my dreams. To be frank, I've found none that I like more than the UI of Windows XP.

This isn't so much because I love Windows XP's UI. But I think it does its thing pretty well. In my past I've tried XFCE, Gnome, KDE and Fluxbox. While they're all good window managers I guess I'm looking for something different, a new way of working.

I liked the minimalism of Fluxbox when I tried it. So I want to give it yet another try. And I want to try others too.

[SIZE="4"]My problem[/SIZE]
I want to try out lots of different windows managers. And see if I can find someone which I will stick with for the long run. My questions are:
[LIST=1]
[*]Which flavor of Ubuntu (ie Ubuntu, Kubuntu etc) should I start with installing?
[*]If I install one window manager using Apt, try it and uninstall it. Will it leave traces and clutter up my system? (I've heard that this is a problem of the past, and that Aptitude doesn't serve any purpose anymore.)
[*]If I install, for example, Ubuntu. Then uninstall Gnome using Apt. Will I have the same system base as if I would have installed Kubuntu and uninstalled KDE? That is, will I have a clean system ready for another WM without clutter?
[*]If I install KDE, Gnome and for example, Fluxbox. Then I install, for example, Firefox. Will it be available in the menus of all three window managers or just the one I'm using during the Firefox installation?
[*]Is there a general way to install window managers? Is it as easy as any other application, that is, just an apt install and it's available? How do I start it and set the default VM?
[*]If I install a driver for my GeForce card using Ubuntu. Will it then be available and used in Fluxbox as well?
[*] *A side note.* Is it possible to copy, or even better, syncronize the configuration of for example Fluxbox on my desktop machine and my laptop machine? I can't syncronize it all though, they use different resolutions.
[/LIST]
When looking at the questions above, keep in mind that:
[LIST]
[*]I plan to do a complete fresh install, as a start of my exploration.
[*]I prefer to have a system which is as clean as possible. As I would like to just uninstall the WM's I don't need/want and keep on using the one/ones I do want.
[*]I plan to try out Ratpoison, Fluxbox, Enlightment, Fvwm-crystal and maybe some more. Gnome, XFCE and KDE aren't that interesting to me.
[/LIST]

---

### Post by tdrusk on 2007-10-04
> **kentl said:**
> Hi,

[SIZE="4"]Background[/SIZE] (jump over this heading if you don't like rants ;))
I've used Linux on and off for a couple of years. While I absolutely love it on my little home server I've not yet found the window manager of my dreams. To be frank, I've found none that I like more than the UI of Windows XP.

This isn't so much because I love Windows XP's UI. But I think it does its thing pretty well. In my past I've tried XFCE, Gnome, KDE and Fluxbox. While they're all good window managers I guess I'm looking for something different, a new way of working.

I liked the minimalism of Fluxbox when I tried it. So I want to give it yet another try. And I want to try others too.

[SIZE="4"]My problem[/SIZE]
I want to try out lots of different windows managers. And see if I can find someone which I will stick with for the long run. My questions are:
[LIST=1]
[*]Which flavor of Ubuntu (ie Ubuntu, Kubuntu etc) should I start with installing?
[*]If I install one window manager using Apt, try it and uninstall it. Will it leave traces and clutter up my system? (I've heard that this is a problem of the past, and that Aptitude doesn't serve any purpose anymore.)
[*]If I install, for example, Ubuntu. Then uninstall Gnome using Apt. Will I have the same system base as if I would have installed Kubuntu and uninstalled KDE? That is, will I have a clean system ready for another WM without clutter?
[*]If I install KDE, Gnome and for example, Fluxbox. Then I install, for example, Firefox. Will it be available in the menus of all three window managers or just the one I'm using during the Firefox installation?
[*]Is there a general way to install window managers? Is it as easy as any other application, that is, just an apt install and it's available? How do I start it and set the default VM?
[*]If I install a driver for my GeForce card using Ubuntu. Will it then be available and used in Fluxbox as well?
[*] *A side note.* Is it possible to copy, or even better, syncronize the configuration of for example Fluxbox on my desktop machine and my laptop machine? I can't syncronize it all though, they use different resolutions.
[/LIST]
When looking at the questions above, keep in mind that:
[LIST]
[*]I plan to do a complete fresh install, as a start of my exploration.
[*]I prefer to have a system which is as clean as possible. As I would like to just uninstall the WM's I don't need/want and keep on using the one/ones I do want.
[*]I plan to try out Ratpoison, Fluxbox, Enlightment, Fvwm-crystal and maybe some more. Gnome, XFCE and KDE aren't that interesting to me.
[/LIST]

[LIST=1]
[*]Which flavor of Ubuntu (ie Ubuntu, Kubuntu etc) should I start with installing?
icewm has a windows like appearance.
[*]If I install one window manager using Apt, try it and uninstall it. Will it leave traces and clutter up my system? (I've heard that this is a problem of the past, and that Aptitude doesn't serve any purpose anymore.)
No, it shouldn't. 
[*]If I install, for example, Ubuntu. Then uninstall Gnome using Apt. Will I have the same system base as if I would have installed Kubuntu and uninstalled KDE? That is, will I have a clean system ready for another WM without clutter?
I THINK so. They all run off the Ubuntu kernal. 
[*]If I install KDE, Gnome and for example, Fluxbox. Then I install, for example, Firefox. Will it be available in the menus of all three window managers or just the one I'm using during the Firefox installation?
With fluxbox you will have to renew the menus (I think...), but the program is installed and kde should recognize it.
[*]Is there a general way to install window managers? Is it as easy as any other application, that is, just an apt install and it's available? How do I start it and set the default VM?
Just search for it in the repositories. If it's not there find a guide here.
[*]If I install a driver for my GeForce card using Ubuntu. Will it then be available and used in Fluxbox as well?
Yes
[*] *A side note.* Is it possible to copy, or even better, syncronize the configuration of for example Fluxbox on my desktop machine and my laptop machine? I can't syncronize it all though, they use different resolutions.
[/LIST]

If you want a clean simple system, you may want to start with
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

It gives you everything you need to just start installing packages you want.

---

### Post by kentl on 2007-10-04
I made your answers bold and reference them below using their numbers.
>    1. Which flavor of Ubuntu (ie Ubuntu, Kubuntu etc) should I start with installing?
**      icewm has a windows like appearance.**
   2. If I install one window manager using Apt, try it and uninstall it. Will it leave traces and clutter up my system? (I've heard that this is a problem of the past, and that Aptitude doesn't serve any purpose anymore.)
**      No, it shouldn't.**
   3. If I install, for example, Ubuntu. Then uninstall Gnome using Apt. Will I have the same system base as if I would have installed Kubuntu and uninstalled KDE? That is, will I have a clean system ready for another WM without clutter?
**      I THINK so. They all run off the Ubuntu kernal.**
   4. If I install KDE, Gnome and for example, Fluxbox. Then I install, for example, Firefox. Will it be available in the menus of all three window managers or just the one I'm using during the Firefox installation?
**      With fluxbox you will have to renew the menus (I think...), but the program is installed and kde should recognize it.**
   5. Is there a general way to install window managers? Is it as easy as any other application, that is, just an apt install and it's available? How do I start it and set the default VM?
**      Just search for it in the repositories. If it's not there find a guide here.**
   6. If I install a driver for my GeForce card using Ubuntu. Will it then be available and used in Fluxbox as well?
**      Yes**
   7. A side note. Is it possible to copy, or even better, syncronize the configuration of for example Fluxbox on my desktop machine and my laptop machine? I can't syncronize it all though, they use different resolutions.
[B]If you want a clean simple system, you may want to start with
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[/B]
It gives you everything you need to just start installing packages you want.
1. Actually I'm not looking for Windows like appearence. That's why I'm going to try out, for example, Ratpoison. Sorry if I didn't make it clear. And also, there is no Iceuntu as far as I know. I'm wondering which Ubuntu flavor it would be best to start from.
2. Sounds nice! :-)
3. The same kernel, but what about all the other packages? (the GNU-part)
4. Good, it sounds pretty convenient.
5. All right. After install. What do I do to try the installed window manager? And how do I set it to be my default wm?
6. Also good. I haven't found a guide explaining the different parts of a linux system in an easy manner. For example, that a graphics driver is available to all wm:s. I would guess it's the xwindows part that is common for all wm's. Hm.. I'll keep looking.
7. This was an extension to your answer to [1] I would guess. Thanks for the tip.

---

### Post by Terl on 2007-10-04
I played with lots of WM's.  I just installed Ubuntu and then through synaptic I downloaded others.  To use them, at your sign-on screen hit the sessions button and you should see your wm's listed.  Pick the one you want to use.  It will ask if you want it to be your default or a one-time session.  I usually do one-time and off you go.  If you like it you can always make it your default later.

BTW, I have tried ratpoison.  It is stark and barren but quite fast with little to no overhead.  

Also I would recommend checking out the sites for the WM's to see how they configure them and all.

---

### Post by Hospadar on 2007-10-04
Just a general note on window managers, the difference between gnome, kde, icewm, xfce, etc is almost entirely cosmetic, all the different WM's can run any other applications.

You should try burning a couple livecd's and see which one you like best.  If it's not that super important to you, I would just go with gnome, the most people use it so it will be easiest to get help.

---

### Post by RedSquirrel on 2007-10-04
All of the configuration files for Fluxbox itself are in the directory ~/.fluxbox. You can just make an archive of that directory and extract it on your other system(s).

With regard to resolutions, that information is in the file /etc/X11/xorg.conf. The contents of that file may vary from system to system, depending on what hardware you are using. 

You might want to install the full Ubuntu,  Kubuntu, OR Xubuntu and then just try out different window managers. You can simply choose them from the login screen as mentioned above. The advantage of doing this is that you'll have a nice set of applications installed and you can work with them using the new window manager and see what you think.

The alternative is to install a minimal system and build up from there. Here's another link:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Celegorm on 2007-10-04
Ooh ratpoison. I've been thinking I ought to try that one out. Right now I'm totally addicted to ion, another keyboard based wm. Fluxbox is my favorite after that; I love its easy to modify text configuration files and tabbed windows are the greatest thing ever. Bit of advice for when you try ratpoison though- make sure you give it a while (or take a break and then come back) before you decide whether or not you like it. From my experience with ion, it takes a significant amount of getting used to that sort of wm, as it is so very different.

---

### Post by mivo on 2007-10-04
As for wanting a "different way of working", I really recommend that you look at the Gutsy Beta with the Compiz integration and turn on some of the features. The 3D Cube, Ring Switcher and Windows Grouping/Tabbing are about to revolutionize the way I work. This would be the third significant change. I started with a C/PM-based (command line interface) Amstrad in the first half of the 80s, then switched to Atari with a graphical interface, GEM, which in essence was not really different from the later Windows. Then came over fifteen years of Windows. All in all, the GUIs were all very similar, no truly innovative improvements. The 3D Cube is different, a more "natural" way of working, and that is really a change that goes deeper than small additions or eye candy.

Gutsy i well done, really, I am still majorly impressed, even though it is still a beta version.

---

### Post by kentl on 2007-10-05
What are the differences (in terms of pros and cons) betweeen the [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) and the [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) methods?

---

### Post by deserthowler on 2007-10-05
When you talk about window managers, you're talking something highly configurable.  My suggestion is look at the websites for the various WMs.  Many have sample screens donated by users and sample configuration files to download, try, and modify to suit your interests and needs and artistic leanings.  It depends how much you want to customize and how much work you want to do.

By customize, I don't mean changing icons or backgrounds or screen savers, although you can do that too.  I mean setting mouse bindings, key bindings, how and where windows open.  You can design menus and how they act.  You can create your own look and feel.  Most of this is done by editing text files, unfortunately with different syntax for different managers.

You can mix KDE and GNOME apps and just about any apps you want to mix.  You can make the WM quick and light or bloated as you wish.  The underlying networking, WiFi, video and sound will work under all of the WMs although it might be necessary to tweak to use them.

I personally chose FVWM because it is the ultimate to configure; you start with a blank screen with a cursor in the center.

Earl

---

### Post by kentl on 2007-10-06
bump! See my questions above in my most recent post (before this one) and the one before that. :)

---

### Post by RedSquirrel on 2007-10-06
> **kentl said:**
> What are the differences (in terms of pros and cons) betweeen the [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) and the [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) methods?

The end result is the same: a base (minimal) system.

[B] net installer (on the psychocats page, "A Barebones Installation"):
[/B] 
_Pros_

- you will download the latest packages from the repositories
- small initial download (the mini.iso is less than 10 MB)


_Cons_

- you will have to be able to setup your internet connection from within the installer. If you can't, then you can't use this method.
- you definitely need a broadband connection


[B] Installing from the Alternate CD ("Install a command-line system"):
[/B] 
_Pros_

- if you have an unstable internet connection, you can use the CD since everything for the base system is on there; you can download the other packages later


_Cons_

- large initial download (the alternate CD is around 700 MB) and it contains things you won't be using (i.e., the full desktop installation)
- the base system will contain packages that were released when the version of Ubuntu on the CD first came out; many of them will need to be updated


Generally speaking, I think the net installer is the ideal way if you can establish your internet connection from within the installer. You don't have the large initial download and you get all the latest packages.

---

### Post by kentl on 2007-10-06
Thanks all! Off I go to re-install! :-)

---

### Post by TeaSwigger on 2007-10-06
Hello kentl,

My favorite alternate wm is Fluxbox. It's efficient, snappy, different, flexible, easy to customize and configure (just a few text files!) and if you want to copy your configuration to another computer running fluxbox, hey just copy those text files. Seriously groovy. If you try it again, please see the thread in RedSquirrel's sig and join us in a few of the informative fluxbox oriented threads you can find at these forums. Two in point:

[http://ubuntuforums.org/showthread.php?t=483613](http://ubuntuforums.org/showthread.php?t=483613)
[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

Next fav is IceWM. By default it's horrid! Just a few easy tweaks later and it's sweet. It's windows-like while having many of the same advantages of Fluxbox, including being configurable with just a few text files and it's also easy to share your settings between computers. You'll undoubtedly want to find the tweaks to allow the menus to open without clicking, and to get a decent theme on it. Once that's done, give it time and enjoy. There's a great thread here abouts on it, I think both those points I mention are covered somewhere in it:

[http://ubuntuforums.org/showthread.php?t=263710](http://ubuntuforums.org/showthread.php?t=263710)

If you're looking for other different ways, I also can suggest that you check out WindowMaker and Enlightenment. Very interesting as well.

All these are easy as pie to install and cleanly uninstall from ultra-convenient repository packages, thanks to the fine work done for us by the Ubuntu folks. Enjoy! :D

---

### Post by kentl on 2007-10-06
Thanks TeaSwigger! I'll defenitely check out Fluxbox as I tried it some years ago and like the minimalism. It will be interesting to see if I can get along with Ratpoison as well. I do a lot of coding and such, that's what I mostely love about computers, and I think it can fit in quite well for such circumstances. I did read about some problems with Ratpoison, it will defenitely be an interesting experience.

IceWM sounds interesting as well. I'll check it out as well. Everything that's not KDE, Gnome or XFCE is worth checking out for me. As I've already check out the three mentioned and am looking for something different. (Even though they are very good at what they do.)

---

### Post by Ptero-4 on 2007-12-04
> **kentl said:**
> Hi,

[SIZE="4"]Background[/SIZE] (jump over this heading if you don't like rants ;))
I've used Linux on and off for a couple of years. While I absolutely love it on my little home server I've not yet found the window manager of my dreams. To be frank, I've found none that I like more than the UI of Windows XP.

This isn't so much because I love Windows XP's UI. But I think it does its thing pretty well. In my past I've tried XFCE, Gnome, KDE and Fluxbox. While they're all good window managers I guess I'm looking for something different, a new way of working.

I liked the minimalism of Fluxbox when I tried it. So I want to give it yet another try. And I want to try others too.

[SIZE="4"]My problem[/SIZE]
I want to try out lots of different windows managers. And see if I can find someone which I will stick with for the long run. My questions are:
[LIST=1]
[*]Which flavor of Ubuntu (ie Ubuntu, Kubuntu etc) should I start with installing?
[*]If I install one window manager using Apt, try it and uninstall it. Will it leave traces and clutter up my system? (I've heard that this is a problem of the past, and that Aptitude doesn't serve any purpose anymore.)
[*]If I install, for example, Ubuntu. Then uninstall Gnome using Apt. Will I have the same system base as if I would have installed Kubuntu and uninstalled KDE? That is, will I have a clean system ready for another WM without clutter?
[*]If I install KDE, Gnome and for example, Fluxbox. Then I install, for example, Firefox. Will it be available in the menus of all three window managers or just the one I'm using during the Firefox installation?
[*]Is there a general way to install window managers? Is it as easy as any other application, that is, just an apt install and it's available? How do I start it and set the default VM?
[*]If I install a driver for my GeForce card using Ubuntu. Will it then be available and used in Fluxbox as well?
[*] *A side note.* Is it possible to copy, or even better, syncronize the configuration of for example Fluxbox on my desktop machine and my laptop machine? I can't syncronize it all though, they use different resolutions.
[/LIST]
When looking at the questions above, keep in mind that:
[LIST]
[*]I plan to do a complete fresh install, as a start of my exploration.
[*]I prefer to have a system which is as clean as possible. As I would like to just uninstall the WM's I don't need/want and keep on using the one/ones I do want.
[*]I plan to try out Ratpoison, Fluxbox, Enlightment, Fvwm-crystal and maybe some more. Gnome, XFCE and KDE aren't that interesting to me.
[/LIST]

1. Use ubuntu server edition. It includes only the stuff in the command-line part of the alternate CD (saves you from downloading a full DE which you obviously won't be using).

2.  No. It won't (but if you really want to be sure you can use the purge option instead of remove to remove the config files along with the wm.

3. If you install ubuntu the normal way (by using the regular optons in the installer), No, you won't be able to leave your system clean. If you install either the server edition or using the command-line option in the alternate CD you will have a clean system and it will stay that way after each wm uninstall.

4. Yes. Every app you install through apt will appear in the menus in every wm, as long as you have the menu and menu-xdg packages installed.

5. Yes. just install them through apt and select them through the sessions menu in the login box.

6. The drivers are run by xorg and the kernel, the wm runs under xorg without even knowing anything about the drivers themselves.

7. You can do that by copying the text based config files from one PC to the other. As for the resolutions, it doesn't matter since that is handled by xorg.

---

### Post by Dr Small on 2007-12-04
Greetings,
Please take a look at the list (which needs to be updated) of Window Managers that I have tried:
[http://php.8ez.com/drsmall/blog/?p=154](http://php.8ez.com/drsmall/blog/?p=154)

Dr Small

---

