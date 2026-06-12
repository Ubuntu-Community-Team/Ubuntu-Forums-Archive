---
title: "Installing Downloaded Apps"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by diddler on 2007-05-15
I do not speak Geek, and I am too old to learn ANOTHER language, so most of my posting will be in English.

I really just wanted to make my first post here.  I just loaded and started using Ubuntu.  I tried Debian, but it refused to find all my various and sundry devices.  Ubuntu had no such trouble, so here I am.  While new to Ubuntu, I have dabbled in Linux before, primarily with Red Hat, but gave it up due to the CONSTANT 'security updates" which proved unsupportable over a dial-up connection.  I am STILL on a dial-up, which almost proved my undoing since apparently no one in Linux world uses dial-up any more, so no one could tell me how to configure my modem.  I am past that now, having diddled around until the modem decided to work.  So here I am, I have removed Microcrap from my computer completely (no dual boot for THIS boy), and I am committing heart and soul to Linux.

Here is the current problem (and I know it has been answered before, and I WILL research it myself, but like I said I needed a first post).  It is really two related problems:

1)  When I download from the add/remove list the apps do not always work.  I check to see if they are distro specific, and don't download any that are, but I still have problems, particularly with (I hate to admit it) games.  One game I downloaded, X Slash'EM, installed OK but will not run when I click on it (no error message or anything).  There is, perhaps, another program I need to download to make it run.  Another game I downloaded went through the download and install process, then disappeared!  It never showed up on the drop-down menu.

2)  I downloaded the flash plug-in for Firefox as a tar.gz file, got it unpacked on the desktop, and cannot get it to install.   I AM in the desktop directory, but keep getting a message that it can't find the file and/or directory.  I know this question has been answered before so don't bother to respond until I come back and complain that none of the previous suggestions work. 

Thanks

---

### Post by Boelcke on 2007-05-15
I'm sure others will answer this better, but I thought I'd give you a quick answer before dropping off to bed, seeing how this is your first post and all!

In downloading tgz files, you might be making things harder for yourself than you really need to.  Go to System, Administration, Synaptic Package Manager.  In there, you can simply add and remove tons of applications easily.  For example, you can get version 7 of Flash from there pretty easily.  (There's a beta for Flash 9, which this forum has a good how to on somewhere.)

Also, there are a few repositories of stuff that ubuntu won't show in there right out of the box.  There's some restrictions based on licensing and legal matters that prevents them from enabling these larger collections of easily installable software.  You can edit your source list something like that suggested [here]("http://www.psychocats.net/ubuntu/sources").  (First thing I came across.)

Welcome to ubuntu.  I've been at it for a year now.  This forum has been an essential tool for me in getting it to do all I want out of it.

---

### Post by diddler on 2007-05-16
Thanks for the tip  Boelcke.  I guess I didn't explore the menus enough.  It never occured to me that there would be THREE separate download apps.  Silly me.

---

### Post by Happy_Man on 2007-05-16
Uh... Add/Remove, Synaptic, ???? What's the third one? :confused:

---

### Post by aysiu on 2007-05-16
This tutorial has screenshots:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by diddler on 2007-05-17
> **Happy_Man said:**
> Uh... Add/Remove, Synaptic, ???? What's the third one? :confused:

The security update app that appears automatically on the task bar.  (At least on MY task bar):)

---

### Post by diddler on 2007-05-17
Still no luck on installing the flash player plug-in for Firefox.  It may be there but does not show up in the "add-on" window.  I have now tried the manual method and the synaptic package method.  Any other suggestions?

---

### Post by diddler on 2007-05-17
Thanks Ayisu, I'll give that site a try as soon as I have the time.

---

### Post by Delkster on 2007-05-17
> **diddler said:**
> While new to Ubuntu, I have dabbled in Linux before, primarily with Red Hat, but gave it up due to the CONSTANT 'security updates" which proved unsupportable over a dial-up connection.
You'll probably run into that on any modern and easy-to-use Linux distribution because of the sheer amount of software in such a distro and also because the open-source folks are quite pedantic about filling most holes.

> One game I downloaded, X Slash'EM, installed OK but will not run when I click on it (no error message or anything).  There is, perhaps, another program I need to download to make it run.  Another game I downloaded went through the download and install process, then disappeared!  It never showed up on the drop-down menu.
Not all of the unsupported applications in the universe channel/repository comply with modern things such as the menu layout. In most cases it's a pretty good guess that you can start the application from the terminal with the name of the program -- e.g. Chromium could be started by entering "chromium" in the terminal. Once you've found out the command you can add a menu entry for it yourself if you want. (Chromium does actually come with a menu entry but I used it as an example since I couldn't immediately find anything that doesn't)

More and more items in Add/Remove Applications have proper menu entries but not all do yet. There's a vast number of them after all, and not every one has been hand-crafted for Ubuntu.

> and I WILL research it myself
I just had to quote that as well -- with that spirit you'll be getting far. Usually there is an answer, and someone even knows it. You just need to find it out.

In any case, welcome!

---

### Post by Happy_Man on 2007-05-18
Oh...that's Update Manager, it's part of Synaptic.... incidentally, so is Add/Remove.

---

### Post by diddler on 2007-05-20
Well, there are things I have discovered :cool:: 

One of the games I downloaded had no sound, but I ran across the sound file while browsing Synaptic, so that solved THAT problem.  (Unfortunately, if Paused it won't Unpause, but not a deal breaker.)

The game that disappeared?  Figured out that I had only downloaded the GAME ENGINE.  Got to go somewhere else for the game files.

Worked a little in The Gimp, then discovered I have no Help files.  Back to Synaptic. 

(Next week I will have access to a high speed connection for about a week, then watch out!)

Could not understand why I could not write to my second physical drive (or my USB drive).  Finally realized they are both formatted with NTFS (curse you Microsoft).  I guess I should count myself lucky that I can READ them (Red Hat couldn't), but it really cuts down on my file storage capacity.  Looks like I will be burning a LOT of files to DVD-ROM, so I can clear and reformat the second hard drive.

Problems still plaguing me at this point in time :(:

Need to figure out bug reporting - every time I use the Preview on any screen saver it crashes the computer and I am kicked back to the log-in.  It also causes any open programs to close and any unsaved work is lost.  The most interesting result is if I am on-line through GnomePPP, it closes the little "Connected" icon, leaving me no way from the desktop to disconnect.

STILL can't get the flash plug-in to load in Firefox, but one day, as God is my witness, I will never be flashless again!

---

