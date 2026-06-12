---
title: "Creating a Blank Ubuntu/Linux"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by penpenguin on 2006-01-28
Hi everyone, I am new here and had a question.  I downloaded the LiveCd for Ubuntu \\:D/ (gosh I had to use that) and I found that there is alot of unnecesary stuff on it (such as games that would stop me from working).

Anyway, I like the interface, but would make some changes if I could (I figure like adding an object dock and more stuff to desktop [if I was not dumb I could probably do that anyway])

Is there a way or a package of linux where I can download just the linux and the desktop environment, then all of the specific stuff I want (like GEdit, Open Office, etc) afterwards?

I like the interface of Ubuntu, but I want less of the stuff on it.

Let me know when you can, thanks in advance.

---

### Post by public_void on 2006-01-28
Why don't you just remore it. It can be easily gotten back via Add Application. All the applications are listed, you just uncheck the item you want rid off and it will be uninstalled. If you want it back just check the item and it will be installed and setup.

---

### Post by christhemonkey on 2006-01-28
or do a server install (you wont have a desktop environment though) and then apt-get all the stuff you want.

---

### Post by penpenguin on 2006-01-29
I am not that handy with the server loading and commanding, but I would follow step by step isntructions after installing linux if there are any available ones online.  I would like a GUI desktop enviornment though with it, so how would I go about doing that?

---

### Post by christhemonkey on 2006-01-29
sudo apt-get install ubuntu-desktop

---

### Post by johnraff on 2006-01-30
[QUOTE=christhemonkey]sudo apt-get install ubuntu-desktop[/QUOTE]
Is that the same as installing default Ubuntu from the disk, or are a lot of apps left out?

---

### Post by Sokraates on 2006-01-30
[quote=johnraff]Is that the same as installing default Ubuntu from the disk, or are a lot of apps left out?[/quote]

AFAIK ubuntu-desktop will give you the full ubuntu GNOME experience. So all non-gnome apps should be left out. Like maybe Firefox (don't know exactly, since I've never tried).

On the other hand ubuntu-desktop will install games, too. So if you want to have a relly clean ubuntu-system from the very start, it would be better to write donw everything contained in "ubuntu-desktop" and then leave out the packages you don't want (as long as no others depend on them).

This "solution" will take a lot of time, though.

---

### Post by az on 2006-01-30
Ubuntu-desktop will give you everything.  Nothing will be left out.

From a server install do

sudo apt-get install x-window-system-core xterm gdm icewm menu mozilla-firefox synaptic.



for a lean basic system.  You can use synaptic to add stuff on top of that later.


Actually, for really barebones, just install 

x-window-system-core icewm menu synaptic xterm
and type
startx
at the prompt to get into graphical mode.  Run synaptic (as root) to install more stuff.

---

### Post by johnraff on 2006-01-30
btw, if you install something that needs other "libraries" etc, Synaptic puts them in too, but when you uninstall that app it seems the other stuff gets left on your system. 
Is there a utility that will check for unused libraries so you can uninstall them?

---

### Post by Oz_hack on 2006-01-31
What if you want Gnome but you don't want rhythm box, and firefox ( and some other apps) 

If you try gettting rid of them it wants to uninstall ubuntu-desktop 

Is there a easy way to just get the basics and add what you want ?


andrew

---

### Post by r4ik on 2006-01-31
[QUOTE=azz]Ubuntu-desktop will give you everything.  Nothing will be left out.

From a server install do

sudo apt-get install x-window-system-core xterm gdm icewm menu mozilla-firefox synaptic.



for a lean basic system.  You can use synaptic to add stuff on top of that later.


Actually, for really barebones, just install 

x-window-system-core icewm menu synaptic xterm
and type
startx
at the prompt to get into graphical mode.  Run synaptic (as root) to install more stuff.[/QUOTE]

Thanks Azz just what i was lookin for.

---

### Post by mcduck on 2006-01-31
[QUOTE=johnraff]btw, if you install something that needs other "libraries" etc, Synaptic puts them in too, but when you uninstall that app it seems the other stuff gets left on your system. 
Is there a utility that will check for unused libraries so you can uninstall them?[/QUOTE]
Install deborphan. Then you can make a new filter in Synaptic to show only orphaned packets. This will help removing some of the junk.

Also, if you install something that takes a lot of dependencies with it, install it with apt-get, and when it tells you what it's going to install copy that into a text file. This way you can easily copy that after 'sudo apt-get remove' to get rid of everything ;)

---

### Post by johnraff on 2006-01-31
[QUOTE=mcduck]Install deborphan. Then you can make a new filter in Synaptic to show only orphaned packets. This will help removing some of the junk.

Also, if you install something that takes a lot of dependencies with it, install it with apt-get, and when it tells you what it's going to install copy that into a text file. This way you can easily copy that after 'sudo apt-get remove' to get rid of everything ;)[/QUOTE]
 Thanks mcduck.
Two good ideas there. I'll try out deborphan right away!

---

### Post by johnraff on 2006-01-31
[QUOTE=Oz_hack]What if you want Gnome but you don't want rhythm box, and firefox ( and some other apps) 
If you try gettting rid of them it wants to uninstall ubuntu-desktop 
Is there a easy way to just get the basics and add what you want ?
andrew[/QUOTE]
I think ubuntu-desktop is just the name of a package, so if you want to take out something that was in the package, the system is warning you that it won't be the proper full package any more. AFAIK all the rest of the stuff will still be there.

---

### Post by Sokraates on 2006-02-01
ubuntu-desktop (like "kubuntu-desktop", "kde" or "kde-multimedia") is a metapackage. It does not contain any package itself but a **list **of packages to be installed.

Removing an **one** package listed, will also remove ubuntu-desktop but not the rest of the list. Should any packages depend on the removed one, they will be mentioned separately.

---

### Post by mcduck on 2006-02-01
[QUOTE=Sokraates]ubuntu-desktop (like "kubuntu-desktop", "kde" or "kde-multimedia") is a metapackage. It does not contain any package itself but a **list **of packages to be installed.

Removing an **one** package listed, will also remove ubuntu-desktop but not the rest of the list. Should any packages depend on the removed one, they will be mentioned separately.[/QUOTE]yes, removing the desktop packages is safe, but if you later want to upgrade to new Ubuntu version, you should first install the ubuntu-desktop (or kubuntu-desktop) package again. If you don't, some new features and programs might not get installed. (after upgrade, you can remove the desktop package and programs you don't want again)

---

### Post by Sokraates on 2006-02-01
[quote=mcduck]yes, removing the desktop packages is safe, but if you later want to upgrade to new Ubuntu version, you should first install the ubuntu-desktop (or kubuntu-desktop) package again. If you don't, some new features and programs might not get installed. (after upgrade, you can remove the desktop package and programs you don't want again)[/quote]

Right. The annoying thing is, that you go through the pain of installing all the apps only to once again remove bunch.

I think it's more sensible to do an upgrade **without** the removed meta-packages. Then try installing them and copy the list of the packages to be installed. Now you can study the list and see, if you find anything interesting. You can then install those packages separately and don't need to uninstall anything again.

On a sidenote: AFAIK debs from already installed packages are kept on the system, even after removing/purging the app. Where are the debs stored and is there a tool to remove them as well?

---

### Post by mcduck on 2006-02-01
[QUOTE=Sokraates]
On a sidenote: AFAIK debs from already installed packages are kept on the system, even after removing/purging the app. Where are the debs stored and is there a tool to remove them as well?[/QUOTE]You can remove them with 'sudo apt-get clean'. Or with Synaptic, go to Settings/Preferences/Files and click 'Delete Cached Package Files'.

---

### Post by Sokraates on 2006-02-01
[quote=mcduck]You can remove them with 'sudo apt-get clean'. Or with Synaptic, go to Settings/Preferences/Files and click 'Delete Cached Package Files'.[/quote]

Thank you! Now I can finally free up some space on my poor laptop. Considering how many apps I've already removed ...

---

