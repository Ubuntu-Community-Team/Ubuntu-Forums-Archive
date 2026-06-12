---
title: "Using Qt applications in Gnome or Xfce"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-11-27
Hi,

I'm all new to Linux, tried Ubuntu over the weekend and definitely want to throw away XP (will probably dualboot in the beginning though). 

I prefer Gnome and XFCE to KDE but I'd like to use KDE applications too. Most people say that it's OK to run KDE applications in Gnome (or reverse) but I keep on reading some have problems or even that it's not a good idea to run Qt applications in GTK environment... The truth is certainly that it depends on the application. 

I came across several things to run Qt applications in Gnome or Xfce:

1) do nothing, just run KDE applications in Gnome. Some will work but slower than in a KDE desktop and some simply won't run at all.

2) I should load KDE libraries in Gnome/Xfce! This will slow down the startup but then ALL Qt applications should work in Gnome or Xfce at the same speed they would run in KDE!

3) install both KDE and Gnome/Xfce desktops and run Qt applications from KDE and GTK applications from Gnome/Xfce. I don't really like this one.

OK so basically I can choose between 1 and 2. But then I saw that XFCE has a setting to launch KDE or Gnome services on startup (or even both). Isn't it the "best" solution for me? Does this work the same as loading KDE libraries? Does Gnome also have this option???

Sorry if this question is a bit confusing, I'm a still confused :confused: 

Thanks

---

### Post by Jimmey on 2006-11-27
When you install a program with apt, then apt will independantly sort out all of that program's dependancies (including libraries). It will only install the packages and libraries that this program _needs_ to run. 

If you're installing a KDE app, apt won't install every library designed for use with KDE in existence. Just the ones that your applications needs. And I doubt that it will slow boot time by much, if at all.

As far as I know, there's no problems with running applications intented for other desktop environments on XFCE.

---

### Post by muep on 2006-11-27
I recommend the first option. There's nothing wrong with running Qt apps in a Gtk desktop envirinment, except for looks and a small performance hit, that you probably won't even notice.

---

### Post by bailout on 2006-11-27
As has been said, if you install a kde app on gnome though apt/synaptic then the necessary libraries will be installed. I think the performance hit of running kde apps on gnome, or the other way round, comes from the kde libs not being started until you start a kde app that needs them whereas under the native environment the libs etc are loaded when the DE boots. I am no expert though so that is just what I have gathered reading the forums.

I used to run both gnome and kde before switching to just kde. Most kde apps worked well under gnome. The only one I can remember having problems with was Konqueror which used to take a long time to shut down rather than start. That was a couple of releases ago though.

I think you are best off choosing the desktop environment which is native to most of your preferred apps. Having tried both I found I mostly preferred kde applications so went with kde as my desktop. The few remaining apps from the other 'side' you can't find equivelents for will usually run well enough, whether kde apps in gnome or gnome apps in kde.

---

### Post by kilou on 2006-11-27
Thanks for these informative replies :) For sure I'll first go with the first option since it's the easiest one. However I wonder what's the purpose of this "launch KDE services on startup" feature of XFCE. If I check this option, does it mean that XFCE will basically work EXACTLY as efficiently with Qt apps than KDE native (same speed)? Basically the questions are:

- does this option makes XFCE a "KDE-light" desktop (less features but the same support for Qt applications)?

- does this option exist in Gnome as well?

- who would advise using checking both marks (launch KDE services AND Gnome services on startup)? Would this make XFCE "the most" compatible Desktop environment for Qt and GTK applications? Would this increase the boot time significantly??

Thanks

---

### Post by rev_b on 2006-11-27
I have both KDE an gnome installed, and I run Qt and GTK apps from gnome. If there's some performance hit, I really can't notice it. Yes, maybe the first time you run a KDE app, it'll take 4-5 more seconds to load while loading Qt libraries. Big deal.
Boot time isn't any longer at all. With Ubuntu, I have the faster booting system to desktop ever. I didn't find any stability problems also.

So go for it. If you haven't heard about all those "problems", I doubt you ever noticed any difference running Qt apps in Gnome. That's the beauty about Linux modular system.

---

### Post by kilou on 2006-11-27
OK I'll do that then. Thanks a lot for your lightning fast and efficient help! I was first impressed by Ubuntu and now I'm impressed by this forum :)

---

