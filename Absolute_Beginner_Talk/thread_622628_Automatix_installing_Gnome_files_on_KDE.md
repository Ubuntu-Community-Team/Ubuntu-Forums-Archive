---
title: "Automatix installing Gnome files on KDE?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Gripp on 2007-11-25
i'm just making sure here.... i just started installing Automatix and it calced a bunch of gnome dependancies and started running them - but i'm running KDE..

is this okay?
if not, how do i undo/reverse everything?

---

### Post by overdrank on 2007-11-25
> **Gripp said:**
> i'm just making sure here.... i just started installing Automatix and it calced a bunch of gnome dependancies and started running them - but i'm running KDE..

is this okay?
if not, how do i undo/reverse everything?

Please do not use automatix! What are you trying to install codecs?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

---

### Post by Gripp on 2007-11-25
honestly i wasn't even completely sure what the program was - just saw a lot people talking about it/reccomending it and read on some website of someone listing their top 10 favorite ubuntu apps - this was #1...

curiosity got the better of me i suppose :)
i've never really used linux as a desktop so i dont really know about all of the goodies - exploring :)

so, you;re saying it isn't a good program? it is working for me.. i'm not really "media person" and the VLC player already plays my music - so, no, i'm not after codecs

it was able to get ndiswrapper installed (after two days of me fighting with it...) so i'm atleast happy with that
but, i mean, is it dangerous? should i uninstall it?

---

### Post by overdrank on 2007-11-25
> **Gripp said:**
> honestly i wasn't even completely sure what the program was - just saw a lot people talking about it/reccomending it and read on some website of someone listing their top 10 favorite ubuntu apps - this was #1...

curiosity got the better of me i suppose :)
i've never really used linux as a desktop so i dont really know about all of the goodies - exploring :)

so, you;re saying it isn't a good program? it is working for me.. i'm not really "media person" and the VLC player already plays my music - so, no, i'm not after codecs

it was able to get ndiswrapper installed (after two days of me fighting with it...) so i'm atleast happy with that
but, i mean, is it dangerous? should i uninstall it?

Ok I am not saying it is good or bad but it is not supported by ubuntu. I have used automatix in the past but it does cause some issues.

---

### Post by Sir_Sid on 2007-11-25
It has been known to break systems. It is getting better and I hear that the developers ares starting to work with the ubuntu deveolopers on it. If you want a way to install programs and what not, just use the synaptic package manager. (System >> Synaptic Package Manager).
Just search for the packages you want click the small box and mark it for installation and then press apply at the top. This is a much safer way to install packages or programs. You can run gnome programs on kde, you will just need the dependancies. When you use apt-get or aptitude to install these gnome programs, it will also get the needed dependencies. (btw, apt-get and aptitude are two "programs" that allow you to install programs via the command line).

---

### Post by Gripp on 2007-11-25
Thanks :)
i'll leave it on my system, but just not use it - just to spare myself from any uninstall issues....
and just stick with Adept 
is synaptic better/different than adept? i dont seem to have it installed on my machine...
and, yeah i've had some experience with apt-get but for some reason i seem to be getting better luck getting some things to install using adept (like automatix .. it just so happens...) - any ideas why?

---

### Post by FuturePilot on 2007-11-25
> **Gripp said:**
> Thanks :)
i'll leave it on my system, but just not use it - just to spare myself from any uninstall issues....
and just stick with Adept 
is synaptic better/different than adept? i dont seem to have it installed on my machine...
and, yeah i've had some experience with apt-get but for some reason i seem to be getting better luck getting some things to install using adept (like automatix .. it just so happens...) - any ideas why?

Adept is the QT front end to Apt, while Synaptic is the GTK front end to Apt. In the end they both accomplish the same task.
I'm not sure what you mean by better luck with Adept than apt-get. Adept is just a GUI for Apt

---

### Post by Gripp on 2007-11-25
yeah i know its just a front end for adept
its why i'm a bit confused as to why one would work better than the other...

---

### Post by bodhi.zazen on 2007-12-19
Automatix is a third party project and, at this time, is not supported on the ubuntu forums. For additional information see the following links :

	[Technical review of Ax](http://mjg59.livejournal.com/77440.html)

	To my knowledge the maintainers of Ax are working to address these issues, but they remain unresolved at this time. You might check the Ax forums for an update. When and if this occurs the situation will be re-evaluated and subject to change.

	[Official Forums Policy](http://ubuntuforums.org/announcement.php?f=13/)

	[Supported Installation Alternatives to Automatix](http://ubuntuforums.org/showthread.php?t=519872)

	[Automatix forums](http://www.getautomatix.com/forum/index.php?act=idx)

	If you want to discuss Ax, feel free to post here : 

	[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

