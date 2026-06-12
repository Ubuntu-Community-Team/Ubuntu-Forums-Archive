---
title: "Gnome? KDE? QT?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Thistlewait on 2007-06-08
Okay, I'm completely new to Linux (Ubuntu). I worked with Unix briefly in the 80's, but that was a long time ago. I'm coming from a Windows background these days. But I saw Ubuntu and as curious, so I'm giving it a try. So far I like what I've got, but I have questions:

What, exactly, are Gnome, KDE, QT? Do they all run on X-Windows? What is the relationship between X-Windows and the Linux kernel?

I hope those questions make sense, and I can start to get a handle on this OS.

TIA,
thistlewait

---

### Post by Nekiruhs on 2007-06-08
GNOME and KDE are desktop environments, the control the windows, manage running applications etc. GTK and QT are toolkits. GTK and QT allow devs to acess GNOME and KDE functions, sort of like an API. X Windowing system is closer to the kernal and it is what "speaks" to the driver for your video card, it also handles keyboard and mouse input. 

If a more experienced person comes along and tells you differently, believe them. I'm still trying to figure this out myself, this is what I have gathered so far.

---

### Post by Inxsible on 2007-06-08
Gnome and KDE are desktop environments. They have different default applications for different tasks. For eg. Gnome has OpenOffice as its office software, KDE has KOffice etc.
 
Having said that, Gnome applications will work in KDE environment too and vice-a-versa.
I don't know much about QT.
 
X-Windows is another term for the GUI or rather handling of a few of your hardware thru the GUI. It has nothing to do with Microsoft Windows, as you might already know.

---

### Post by ggaaron on 2007-06-08
Gnome and KDE are desktop environment providing you window managers along with many other programs.

Qt is a c++ library, that is used by KDE to display everything (Gnome uses gtk)

Both Gnome and KDE need xorg, or some other x-server, so I think that they run on xwindows.

I don't know of any relations between kernel and xwindows.

---

### Post by ggaaron on 2007-06-08
And if you like reading this are quite good articles:

[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)
[http://en.wikipedia.org/wiki/KDE](http://en.wikipedia.org/wiki/KDE)
[http://en.wikipedia.org/wiki/Qt_%28toolkit%29](http://en.wikipedia.org/wiki/Qt_%28toolkit%29)
[http://en.wikipedia.org/wiki/Gtk](http://en.wikipedia.org/wiki/Gtk)
[http://en.wikipedia.org/wiki/Xorg](http://en.wikipedia.org/wiki/Xorg)

And for Gnome and KDE - all my gnu/linux installations had both gtk and qt and merged packages from Gnome and KDE, so I don't think that you have to choose one of this desktops and stick to it (of course this are not only desktop environments but probably most popular).

I hope you'll have much fun with linux=)

---

### Post by Thistlewait on 2007-06-08
Thanks for the info, everyone. I'll get there...eventually.

I'm still in the evaluation stages. I've installed Ubuntu 5 times in the past 2 days. I keep trying to install different packages from the repositories, and have wound up with some strange results that seem to be related to differences between Gnome and KDE. In one case, after loading some KDE applications, I got a dialog asking me to select a default environment. I selected KDE...for no particular reason...and the next time I booted Ubuntu I had a different login screen that had my login account listed, but wouldn't accept my password. So...I wound up reinstalling.

I don't get upset by such things...it's all a learning experience. But I am a bit flustered trying to find documentation that can help someone like me get up to speed. I guess that's what these forums are for. But, often it turns out that the question that one asks is not the "right" question, or pertinent to what it is that one actually wants to know. That can be frustrating.

Thanks for the links to other info. That seems to be reasonable starting point.

Thanks,
thistlewait

---

### Post by xael on 2007-06-08
> **Thistlewait said:**
> Thanks for the info, everyone. I'll get there...eventually.

I'm still in the evaluation stages. I've installed Ubuntu 5 times in the past 2 days. I keep trying to install different packages from the repositories, and have wound up with some strange results that seem to be related to differences between Gnome and KDE.

 (...)

I don't get upset by such things...it's all a learning experience. But I am a bit flustered trying to find documentation that can help someone like me get up to speed. I guess that's what these forums are for. But, often it turns out that the question that one asks is not the "right" question, or pertinent to what it is that one actually wants to know. That can be frustrating.

(...)

Thanks for the links to other info. That seems to be reasonable starting point.

Thanks,
thistlewait

Please, keep on insisting with Ubuntu, read a lot, experiment on your  own, reinstall it as many times as you feel comfortable. We all have been there. Help spread the word.

---

### Post by jonom on 2007-06-08
Get a stable install going, install a virtual machine (vmware-server, virtualbox, etc.), play with different operating systems on your desktop! \\:D/

---

### Post by Najand on 2007-06-08
> **Inxsible said:**
> Gnome has OpenOffice as its office software, KDE has KOffice etc.
OpenOffice is not a gnome software.

---

### Post by Inxsible on 2007-06-08
> **Najand said:**
> OpenOffice is not a gnome software.
 
Its not, but it comes pre-installed with Gnome version of Ubuntu. Thats what I meant, that different Desktop Environments will provide different applications for the same thing.
 
If you notice, I also mentioned that irrespective of that, you can install kde apps in gnome or vice-a-versa.
 
Sorry, if i wasnt clear enough before :)

---

### Post by Najand on 2007-06-08
> **Inxsible said:**
> Its not, but it comes pre-installed with Gnome version of Ubuntu. Thats what I meant, that different Desktop Environments will provide different applications for the same thing.
 
If you notice, I also mentioned that irrespective of that, you can install kde apps in gnome or vice-a-versa.
 
Sorry, if i wasnt clear enough before :)

It is ok.... I didn't want to say you were wrong... Just wanted to clear things here... Anyway, gnome has its office package, err... Called gnome-office... Have a look at:
[http://www.gnome.org/gnome-office/](http://www.gnome.org/gnome-office/)

---

### Post by ggaaron on 2007-06-08
Wow, it seems that you had installed kdm - kdm and gdm (for KDE and Gnome respectively) are managers that can choose which desktop environment to start. You can't use two at a time so it asked, but there shouldn't be problems with other packages=)

---

