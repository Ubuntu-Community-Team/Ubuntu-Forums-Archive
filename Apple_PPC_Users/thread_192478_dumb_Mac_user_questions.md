---
title: "dumb Mac user questions"
date: 2006-06-08
forum: Apple PPC Users
---

### Post by swartzfeger on 2006-06-08
All,

Still sifting though various docs, wikis and faqs to learn Linux, KDE etc. There are still some little things that I've yet to figure out. Such as...

Contextual menus -- I've tried control-clicking on various files to invoke contextual menus but nothing seems to work. Does KDE support something like contextual menus, or am I simply using the wrong key?

I did just figure out how to get the numeric keypad on my keyboard to work, so I'm feeling pretty proud of myself. :)

---

### Post by swartzfeger on 2006-06-08
Another example -- Konqueror always defaults to icon view, and I prefer detailed list. In OS X, you can invoke cmd-1, -2, -3 etc to switch through different icon views. Is there a way to do this? I didn't see anything mentioned in the KDE users guide...

---

### Post by dashnak on 2006-06-08
Well, my girlfriend has an iBook G4 and to get the contextual menus we use the Eject, that is F12, key. No click, just put the mouse over whatever you want to "right-click" and tap the key. I suppose this could be mapped to any key, but that's the default.

---

### Post by Patrick-Ruff on 2006-06-08
isant Mac OS X alot like Linux? since its base system is Unix, couldn't you simply install a bunch of linux apps on mac? it is a much smoother and stable system then Ubuntu.

---

### Post by n00bWillingToLearn on 2006-06-08
Right click, for me at least, is F12. Also, of course you can connect a usb mouse and or set right click to be ctrl click like in OS x.

[edit] I have no idea how I missed dashnak's post.

---

### Post by n00bWillingToLearn on 2006-06-08
[quote=Patrick-Ruff]isant Mac OS X alot like Linux? since its base system is Unix, couldn't you simply install a bunch of linux apps on mac? it is a much smoother and stable system then Ubuntu.[/quote]

Sadly, no. Yes osX has X11 support but it is not at all like Ubuntu.  There is only one application I know of that has been ported from linux to OS x and it is Open Office and it looks horrible in OS x. There is no Synaptic, no Freedom, yes technically OS x is based on UNIX but I think it is more practical to think of it as being just as different as windows except for the terminal.

---

### Post by xurios on 2006-06-09
For open source, *NIX software ported to OS X, check out [Fink](http://fink.sourceforge.net/). This is a project that has ported a couple of thousand porjects. They use a debian-based (apt-get install, etcetera, just like Ubuntu) package manager to do the dirty work. It also has a [GUI front end](http://finkcommander.sourceforge.net/), if want to go that way. 

Also, [Darwin Ports](http://darwinports.opendarwin.org/) (they currently list 3252 ports) is full of resources. 

You can even run KDE, via X11 under OS X (i.e. full screen KDE desktop, complete with all the standard KDE apps). True, things can be a little akward at times, but essentailly you can get almost anything you want as far as apps and libraries that typically exist under LINUX are concerned, and you will learn a lot once you start using more and more ports.

---

### Post by macheadPDX on 2006-06-10
For me right-click is F11.

---

### Post by swartzfeger on 2006-06-10
[QUOTE=macheadPDX]For me right-click is F11.[/QUOTE]

I can't for the LIFE OF ME get this to work. I've tried both F11 and F12 with no luck.

I've tried 'sudo showkey' and editing sysctrl.conf with no luck.

This is basically screwing me, because I need to grab unrar via adept, so I need to right-click to enable the universe repository, but of course I have no right click, so I can't enable it, so that means I can't open my new firefox download. :(

Why must some things on Linux be some frustratingly HARD? I mean c'mon, unrar isn't installed by default? I only found this out because Ark gave me errors on launch because unrar isn't installed.

Ok, rant over. :)  I *do* like Kubuntu, but I'm finding myself wanting more and more just to reboot into OS X to get stuff done instead of tweaking stuff in Linux that should've been there by default.

---

### Post by kellogs on 2006-06-10
[QUOTE=swartzfeger]I can't for the LIFE OF ME get this to work. I've tried both F11 and F12 with no luck.[/QUOTE]

Hehehe, Try F10+shift over the file you want to right click, I think for G5's they forget to put the correct function key as in G4.

also, for cdrom mounting and unmounting, the eject key works, but to mount press eject put the cdrom/dvd on the tray, and double click the cd icon in places--computer, or wherever you have a cdrom icon.

edit: the good solution is to buy a normal mouse, that is probably what Im gonna do. I'm slowly starting to forget Macosx.... and loving ubuntu everyday more and more.

---

### Post by kellogs on 2006-06-10
Another interesting bit, if you note that, is all that you learn with linux. Observe that, in Macosx when you do a normal boot, you just boot and that is. But in linux you will have to learn a little about openfirmware (macosx here tells you nothing about that, learning experience=0) or partitions... and that having in consideration that no system installation has been yet made... and you are still learning. 

Macosx limits itself to work, and does not show you anything, does not let you control nothing. All propietary system creates a dependency on them, and that can't be good. (look at DRM technology with m$ for example).

---

### Post by 3rdalbum on 2006-06-10
Buying a 2 or 3 button PC mouse will solve the right-clicking problems.

As for enabling the Universe repository, you don't have to do it via the GUI. If you open the file "/etc/apt/sources.list":

```
sudo nano /etc/apt/sources.list
```

Then "uncomment" the lines that it says to, to get access to the Universe repository.

The Ubuntu install and Live CDs use a compressed filesystem, and are designed to use less than 700 megabytes each. This means that some things are left out by default - it's unavoidable, unless you want to become like Debian. Fortunately, it's a piece of piss to add those things afterwards. Any new operating system feels alien compared to what you're used to - I found it difficult to learn Windows XP after using OS 9 and Ubuntu - so stay with it and soon you'll be a pro!

---

### Post by swartzfeger on 2006-06-10
Thanks all... I had already uncommented the repositories in the list file, so that's one problem addressed. I'll try the shift-F10, but I think I need to reedit my sysctl.conf since I've already changed it.

---

### Post by etherealshadows on 2006-06-11
[QUOTE=kellogs]Macosx limits itself to work, and does not show you anything, does not let you control nothing. All propietary system creates a dependency on them, and that can't be good. (look at DRM technology with m$ for example).[/QUOTE]

You can't be serious.

I won't post my reply here, because this simply isn't the place.  For those who want a bit of truth regarding the "limitations" of Mac OS X, though, visit the site listed in my profile, or follow [this link]("http://etherealshadows.blogspot.com/").

---

