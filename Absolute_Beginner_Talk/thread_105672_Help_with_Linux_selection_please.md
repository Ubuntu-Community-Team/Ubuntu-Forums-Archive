---
title: "Help with Linux selection please?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by Lee C on 2005-12-18
I have an X86 based PC (with a ATI AIW 8500 card) on my LAN that I'm expunging XP from and am trying to decide which Linux to install.  I AM NOT :-) looking for a heated debate of which is best (whatever that means), but rather which might better facilitate a couple personal general criteria.

1) My wife will be using it for documents and communication.  I'm sure OpenOffice will satisfy the documents use, and she prefers Thunderbird and Firefox for communications.  Oh yes, she says she has to have her card games :<))

2) I mainly play at (I'm supposedly retired) software development on my PMac G5 using ObjC/Cocoa.  I would like to be able to expand into the Linux world using GNUstep.

So, a combination of a simple home system and one on which an old SE can keep his head busy :-)  I'm comfortable using Unix, but have had no experience using Linux.

Though it may be as unneeded as on a Mac, I'll want to include ClamAV or an equivalent.  Some sort of firewall would also be a consideration, as well as a volume cloning tool for backup and whatever system maintenance tools might be appropriate.  Maybe I'll even have more luck keeping it networked with my Mac than I had with XP.

Any comments are appreciated.

Thank you,
Lee C

---

### Post by ltmon on 2005-12-18
There are plenty of choices, almost all equally as valid.

A couple of points I would make:

- GNUStep may be harder to run in some of the more consumer oriented distributions, such as Lindows.  Ubuntu/Kubuntu are more open ended, in that they have direct access to the whole Debian universe.  Distributions such as Lindows have only a subsection of selected software provided by the vendor, which will most likely not include GNUStep.  You might have to jump through some hoops to get it running otherwise.

- SuSE, (K)Ubuntu, Fedora and Mandriva are all mainstream and quite nice.  I like Ubuntu more for these forums than any other reason.  SuSE has excellent graphical configuration tools, making it my second choice.

- Almost all distrobutions provide live cd's.  If you can spare the time to burn a few and check them out you might find your choice is crystalized a little.

L.

---

### Post by aysiu on 2005-12-18
Take this quiz:
[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

---

### Post by Lee C on 2005-12-19
L,
> A couple of points I would make:

- GNUStep may be harder to run in some of the more consumer oriented distributions, such as Lindows.  Ubuntu/Kubuntu are more open ended, in that they have direct access to the whole Debian universe.  


That's a good point - thank you.  Otherwise I guess I'm looking for an easy GUI for the wife, and a Terminal and GNUstep package to use myself.  If the installation process of the GNUstep package is something "like" Unix, then I think I can handle it.  A binary would be nice, but I've "built" a package or two before.

Lee C

---

### Post by Lee C on 2005-12-19
[QUOTE=aysiu]Take this quiz:
[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)[/QUOTE]


Did but it didn't tell me anything.

However, one of your links may have.  With k/ubuntu there is a Terminal "like" with Unix? Bash is what I use mostly.

Also, the k/ubuntu distinction? Just the GUI tool?

Thank you,
Lee C

---

### Post by aysiu on 2005-12-19
[QUOTE=Lee C]Did but it didn't tell me anything.[/quote] Well, it must have told you *something*. You take the quiz. It recommends two Linux distributions to you. What were the two it recommended?

> 
However, one of your links may have.  With k/ubuntu there is a Terminal "like" with Unix? Bash is what I use mostly. Um... there's a terminal in *every* Linux distribution.

> 
Also, the k/ubuntu distinction? Just the GUI tool? Ubuntu uses the Gnome desktop environment. Kubuntu uses the KDE desktop environment.

---

### Post by Lee C on 2005-12-19
[QUOTE=aysiu]Well, it must have told you *something*. You take the quiz. It recommends two Linux distributions to you. What were the two it recommended?

 Um... there's a terminal in *every* Linux distribution.

 Ubuntu uses the Gnome desktop environment. Kubuntu uses the KDE desktop environment.[/QUOTE]

Let me rephrase my answer :-) It didn't tell me anything new.  It's not geared to select both a simple GUI (for the wife) and a development platform for me.  One pass it selects K/Ubuntu and the other Debian.

Being a Unix "derivative" I assumed there was a Terminal but in all the screen shots and text I've seen so far I did not see it.  Since the GUIs I did see are more Windows like I don't want to end up with a Windows like CLI :-)  Guess I just have not looked far enough.

I've used Cocoa, Tcl/Tk and X windows, but not Gnome or KDE.  Any distinctive characteristics of the two worth mentioning?

Basically, I just want to provide the wife with a good GUI and the apps I mentioned, and an ObjC development platform for myself.  I already know I'll have to rebuild the nibs of anything I try to port to GNUstep.  

Thanks again,
Lee C

---

### Post by aysiu on 2005-12-19
I don't even know what Gnustep is, but we've got it (see attached screenshot).
The terminal is there, too.
You can have it within the GUI (Terminal for Gnome or Konsole for KDE), or you can also Control-Alt-F1 and just have the entire screen be the terminal (no X GUI at all).

---

### Post by senectus on 2005-12-19
[QUOTE=Lee C]
I've used Cocoa, Tcl/Tk and X windows, but not Gnome or KDE.  Any distinctive characteristics of the two worth mentioning?
[/QUOTE]

phew! now _there_ is some serious flame bait :-)

Having used Dec Alpha Unix in the past (long distant past) I can tell you you'll be pretty comfortable in Linux and more so in Ubuntu/Debian.

I'm the guy that started the [Project: Mother]("http://www.ubuntuforums.org/showthread.php?t=13414") thread, and a major part of that was "cards games" both locally and on the net and as long as your happy to install Java and MacroMedia flash you'll be covered with the cards games.

All in all you should find Ubuntu to be to your liking, go give it a go. :-)

---

### Post by Lee C on 2005-12-19
[QUOTE=aysiu]I don't even know what Gnustep is, but we've got it (see attached screenshot).
The terminal is there, too.
You can have it within the GUI (Terminal for Gnome or Konsole for KDE), or you can also Control-Alt-F1 and just have the entire screen be the terminal (no X GUI at all).[/QUOTE]

Thanks Aysiu,

I looks like I can have what I might use of Debian, but a little simpler :-)  

Best wishes for the holidays,

Lee C

---

### Post by Koybe on 2005-12-19
Gnome or KDE are "just" desktop environnement, the window manager is a derivative of the X window system named x.org. It's quite the same configuration.

Gnome is omre simple, quick menu, few apps at the beginning. KDE is more a windows-like feeling with many apps. Question of taste.

---

### Post by Lee C on 2005-12-19
[QUOTE=senectus]phew! now _there_ is some serious flame bait :-)

Having used Dec Alpha Unix in the past (long distant past) I can tell you you'll be pretty comfortable in Linux and more so in Ubuntu/Debian.

I'm the guy that started the [Project: Mother]("http://www.ubuntuforums.org/showthread.php?t=13414") thread, and a major part of that was "cards games" both locally and on the net and as long as your happy to install Java and MacroMedia flash you'll be covered with the cards games.

All in all you should find Ubuntu to be to your liking, go give it a go. :-)[/QUOTE]


Thanks senectus,

You've all been a great help.

Nice thread you referenced :-)

Best wishes for the holidays,

Lee C

---

### Post by Lee C on 2005-12-19
[QUOTE=Koybe]Gnome or KDE are "just" desktop environnement, the window manager is a derivative of the X window system named x.org. It's quite the same configuration.

Gnome is omre simple, quick menu, few apps at the beginning. KDE is more a windows-like feeling with many apps. Question of taste.[/QUOTE]


Thanks Koybe,

Thats a distinction I can take to the bank :-)  Having wasted more time than I care to remember on W<snip>  I hate reminders.  I'll start with Gnome and add what I want, rather than cleaning house.  Mac and W<snip> are the two different ends of the spectrum to me, and I'd prefer no reminders of the low end :-)  

Lee C

---

### Post by senectus on 2005-12-19
[QUOTE=Lee C]
You've all been a great help.
[/QUOTE]

You'll find a lot of that here :-) It's one of the defining qualities of Ubuntu :-D





[SIZE="1"]just you _try_ and get this sort of support from fedora or SuSE[/SIZE]

---

### Post by Lee C on 2005-12-19
[QUOTE=aysiu]I don't even know what Gnustep is, but we've got it (see attached screenshot).
The terminal is there, too.
You can have it within the GUI (Terminal for Gnome or Konsole for KDE), or you can also Control-Alt-F1 and just have the entire screen be the terminal (no X GUI at all).[/QUOTE]


Aysiu,

I forgot to mention (if you're interested) that GNUstep is to *nx what Cocoa is to Mac OS X basically.  Basically Cocoa is a set of development tools (if you lump in Xcode) and, more importantly, all the OO foundation (ObjC class headers and implementations) for Mac OS X that facilitate the development environment.  You use either in ObjC code depending on the base class you import and gcc (compile and link) pulls it all together.  The main difference is the Interface Builder nib (interface resource archives) files.  

Some may find fault with my wording, but I tried to stick to the basic idea.

And if you're not interested :-) you can ignore this and like me get some sleep.  

Thanks again for your help,

Lee C

---

