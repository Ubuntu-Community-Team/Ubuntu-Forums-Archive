---
title: "[SOLVED] I need help uninstalling Amarok"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by ladybumavere on 2008-01-21
I installed Amarok and I didn't really enjoy it, I was just getting it for the scrobbling feature but the I didn't like the usability of it.  I installed it through add/remove programs and when I attempt to uninstall it from add/remove programs it tells me this:

> Cannot remove 'amarok'

One or more applications depend on amarok.  To remove amarok and the dependent applications, use the Synaptic package manager.

So I open the Synaptic package manager and I become totally lost, I have no idea what I can and cannot remove and I don't know what half of the things in there do and what amarok even installed.



HELP!

---

### Post by PeterJS on 2008-01-21
The search function is the best way to get anything done in Synaptic. 

Don't worry about knowing what everything in there does. I've been using linux for years and still can't tell you what every core library does or why it's needed. When you try and uninstall something in synaptic it will give you a list of dependent packages that need to be removed, just take a look at it, if the list is very large, contains something you want, contains something that looks important, ask first somebody'd be glad to answer (I know at least I will). If you don't want to ask, try google.

---

### Post by ladybumavere on 2008-01-21
> **PeterJS said:**
> The search function is the best way to get anything done in Synaptic. 

Don't worry about knowing what everything in there does. I've been using linux for years and still can't tell you what every core library does or why it's needed. When you try and uninstall something in synaptic it will give you a list of dependent packages that need to be removed, just take a look at it, if the list is very large, contains something you want, contains something that looks important, ask first somebody'd be glad to answer (I know at least I will). If you don't want to ask, try google.



So... should I just try searching for Amarok and start removing?

---

### Post by emarkd on 2008-01-21
Search for Amarok.  Find the "Amarok" package, right-click and select "Mark for Removal"  Let us know what it says.

---

### Post by ladybumavere on 2008-01-21
> **PeterJS said:**
> The search function is the best way to get anything done in Synaptic. 

Don't worry about knowing what everything in there does. I've been using linux for years and still can't tell you what every core library does or why it's needed. When you try and uninstall something in synaptic it will give you a list of dependent packages that need to be removed, just take a look at it, if the list is very large, contains something you want, contains something that looks important, ask first somebody'd be glad to answer (I know at least I will). If you don't want to ask, try google.


Never mind, I got gun shy.  I searched and the only thing that looks like it's used for another program is this "xmms-kde" which says:

> MP3 player integrated into the KDE panel
xmms-kde is an MP3 player integrated into the KDE panel.  It can also
be used to control Amarok, MPlayer, Noatun, or XMMS from the panel.
Features are:

 * Starting, pausing, and stopping the player
 * Jumping backward and forward in the playlist
 * Dragging and dropping files from the file manager
 * On-screen display to show the title of the song that starts playing
 * Database support for Ogg and MP3 files

You can do most of these things by using the mouse or customizable
keyboard shortcuts.

Web site: [http://xmms-kde.sourceforge.net/](http://xmms-kde.sourceforge.net/)

Now, I use xmms all the time, if I remove this will this cause a problem with xmms?  Should I maybe remove xmms then remove amarok then re-install xmms?

What's your suggestion?

---

### Post by PeterJS on 2008-01-21
I wouldn't go on an indiscriminate deleting spree, but the package that contains Amarok should be pretty easy to find when you search (search results are in alphabetical order, which puts Amarok right at the top), mark it for removal, and it will tell you what else needs to be removed, if you're fine with that click Ok, then apply.

---

### Post by PeterJS on 2008-01-21
xmms-kde is just the kicker plugin for xmms, so if you're not running a full kde desktop you won't be missing anything. If you're ever curious what something is, look it up in Synaptic, the descriptions are generally quite good at explaining what things are.

---

### Post by emarkd on 2008-01-21
I don't use KDE, so my advice here carries little weight.  It sounds like that xmms-kde package is some sort of task bar launcher or something and not related to the xmms core application.  I don't think removing amarok will have any effect on xmms.  If I were you, I'd go ahead and remove Amarok and then see if xmms still works like you want it to.  Again, that's just what I'd do...

---

### Post by ladybumavere on 2008-01-21
> **PeterJS said:**
> I wouldn't go on an indiscriminate deleting spree, but the package that contains Amarok should be pretty easy to find when you search (search results are in alphabetical order, which puts Amarok right at the top), mark it for removal, and it will tell you what else needs to be removed, if you're fine with that click Ok, then apply.



Great that appears to have worked great!

It doesn't show in my Applications menu as well as in add/remove programs!

Thank you very very much.

I really appreciate it.

---

### Post by emarkd on 2008-01-22
You're welcome!

---

### Post by firefeather on 2008-01-22
If you've removed the package "amarok" you're probably fine. if you're running Ubuntu (not Kubuntu) then you'll likely have installed some KDE libraries too. You won't need those but they won't be hurting anything (except taking up hard drive space) by being there. Synaptic probably got rid of many of those when you uninstalled Amarok but if you're just barely starting on Ubuntu and haven't installed many programs then you probably can get rid of anything like "kdelibs" just fine. **However**, I don't recommend removing packages willy-nilly, either.

Here's a trick I learned: you can see what packages a program installed when it got installed by going into Synaptic Package Manager and single-clicking a package (like "amarok") and clicking "Properties" on the toolbar. There should be a tab there that says "Dependencies" and it will tell you all the packages that it needs. **But that's not all**...linux shares these "dependencies" among its programs. You can tell if you're going to break another program by removing a lib-something package because if you go to remove it, it will tell you that certain other packages would need to be uninstalled. If other programs are listed, you shouldn't remove it unless you want to remove those other programs too.

---

### Post by ladybumavere on 2008-01-22
> **firefeather said:**
> If you've removed the package "amarok" you're probably fine. if you're running Ubuntu (not Kubuntu) then you'll likely have installed some KDE libraries too. You won't need those but they won't be hurting anything (except taking up hard drive space) by being there. Synaptic probably got rid of many of those when you uninstalled Amarok but if you're just barely starting on Ubuntu and haven't installed many programs then you probably can get rid of anything like "kdelibs" just fine. **However**, I don't recommend removing packages willy-nilly, either.

Here's a trick I learned: you can see what packages a program installed when it got installed by going into Synaptic Package Manager and single-clicking a package (like "amarok") and clicking "Properties" on the toolbar. There should be a tab there that says "Dependencies" and it will tell you all the packages that it needs. **But that's not all**...linux shares these "dependencies" among its programs. You can tell if you're going to break another program by removing a lib-something package because if you go to remove it, it will tell you that certain other packages would need to be uninstalled. If other programs are listed, you shouldn't remove it unless you want to remove those other programs too.


Awesome!

Thanks a lot.

---

