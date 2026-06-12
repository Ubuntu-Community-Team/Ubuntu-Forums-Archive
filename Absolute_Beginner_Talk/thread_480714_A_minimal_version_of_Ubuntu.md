---
title: "A minimal version of Ubuntu?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-06-21
I've tried and tried, but I can't seem to find a way to get Ubuntu **without** also getting a bunch of stuff I have absolutely no need for.

I've tried the alternate CD, but must have messed up because I still ended up with all the big packages I don't want.  Trying to remove those packages is not only tedious, but I keep being warned that to remove certain things will also cause the removal of "ubuntu-desktop" -- which if I'm not mistaken means that I won't get notifications of updates to the packages I *do* have installed.

I have absolutely no use for Evolution, OpenOffice, Games, Accessibility packages, CUPS, HPLib, all of the support for laptops, and the list goes on and on.

How can I install just Ubuntu, and then pick and choose the few applications that I actually *do* want on my system?  And how can I do that and still be notified when something I have installed has an update available?

Thanks much,
Bob

---

### Post by wpshooter on 2007-06-21
Go into Synaptic, find the applications that you want to get rid of/uninstall and **mark for removal **but DON'T "**mark for complete removal**", so the dependencies do not get uninstalled.

Good luck.

---

### Post by GrueTamer on 2007-06-21
The best way to install ubuntu and work your way up in terms of installing packages is most likely the minimal cd.  This will download the packages that you want to install from the internet, and will only get what you want it to get, instead of you downloading the ubuntu iso file and getting all the software on it.  You can learn more about it [here]("http://psychocats.net/ubuntu/minimal#barebones").

---

### Post by RTrev on 2007-06-21
> **wpshooter said:**
> Go into Synaptic, find the applications that you want to get rid of/uninstall and **mark for removal **but DON'T "**mark for complete removal**", so the dependencies do not get uninstalled.

Good luck.

I've found that in many cases "Mark for Removal" also causes the warning that ubuntu-desktop will be removed.  For example, try removing evolution-webcal.

---

### Post by RTrev on 2007-06-21
> **GrueTamer said:**
> The best way to install ubuntu and work your way up in terms of installing packages is most likely the minimal cd.  This will download the packages that you want to install from the internet, and will only get what you want it to get, instead of you downloading the ubuntu iso file and getting all the software on it.  You can learn more about it [here]("http://psychocats.net/ubuntu/minimal#barebones").

Thank you!  That sounds like just the ticket.  I'll report back after I try it out.

Appreciate the replies!

Bob

---

### Post by diatribe on 2007-06-21
you can always remove ubuntu-desktop and whatever other packages you want, then reinstall ubuntu-desktop

---

### Post by John.Michael.Kane on 2007-06-21
This should help you install a light system.
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by RTrev on 2007-06-21
> **diatribe said:**
> you can always remove ubuntu-desktop and whatever other packages you want, then reinstall ubuntu-desktop

You can??  Isn't that a meta package which depends on the entire mess of stuff I'm trying to avoid?  I was wondering if I could generate a customized ubuntu-desktop,  but now i have the clue I think.. do the minimal install for server, and then add stuff later.

---

### Post by panso on 2007-06-21
> **RTrev said:**
> I've found that in many cases "Mark for Removal" also causes the warning that ubuntu-desktop will be removed.  For example, try removing evolution-webcal.

i believe ubuntu-desktop is just a container package to install all the standard desktop items as dependencies. Its be safe to remove as it won't remove all the underlying packages. I have removed it without anything else missing.

---

### Post by RTrev on 2007-06-21
> **panso said:**
> i believe ubuntu-desktop is just a container package to install all the standard desktop items as dependencies. Its be safe to remove as it won't remove all the underlying packages. I have removed it without anything else missing.

And you still get notifications about new packages being available?

---

### Post by Apipote on 2007-06-21
Try Xubuntu

---

### Post by RTrev on 2007-06-21
> **Apipote said:**
> Try Xubuntu

I don't like Xubuntu.  I like Gnome.  This isn't an issue of having a low-powered machine.. I've got dual processors, 4G of RAM, and over a Terrabyte of disk.

This is an issue of wanting an installation just the way I want it, without a bunch of crud intermingled with it in such a way that it's almost impossible to tell what is what.  If I had the patience and knowledge, I might try Gentoo or Linux-from-Scratch, but I like Ubuntu a lot, and just want to clean it up.  I wish the install CD would ask some questions, or give some categories to choose from.  Basic Desktop would be what I'd choose.  I want it to come up and look just like the standard Ubuntu, but without the bloat.  All I would install would be Firefox, gFtp, the Pan News Reader, VLC, and vmware-server.  Probably some applets for the panel, like the sensors-applet.

I'm obsessive-compulsive about having the fastest, cleanest, lightest, most responsive OS I can possible have.. and then I can forget about it and just be productive.  :-)

I'm going to try the mini.iso for AMD 64, and see how that goes.

---

### Post by jputman01 on 2007-06-21
please let us know how the minimal disk goes, sounds like a good alternative i may have to give a try sometime

---

### Post by RTrev on 2007-06-21
> **jputman01 said:**
> please let us know how the minimal disk goes, sounds like a good alternative i may have to give a try sometime

Will do.  See you all on the other side.  :-)  And thanks again.

---

### Post by panso on 2007-06-21
Now that you mention it, I am not sure but I believe so. :)

I only removed it last week, or rather it was removed when I installed something else. However I do still receive updates, but I will monitor it compared to my other ubuntu and see if the updates are different.

---

### Post by RTrev on 2007-06-21
> **GrueTamer said:**
> The best way to install ubuntu and work your way up in terms of installing packages is most likely the minimal cd.  This will download the packages that you want to install from the internet, and will only get what you want it to get, instead of you downloading the ubuntu iso file and getting all the software on it.  You can learn more about it [here]("http://psychocats.net/ubuntu/minimal#barebones").

Before I get started on this, let me make sure I'm clear.  I want the Gnome desktop.  They give a command to get Icewm, which isn't the one I want I don't think.  If I want Gnome, and nothing else, would I substitute Gnome for Icewm?  Or will that get me OpenOffice, Evolution, and so on?

Thanks..

---

### Post by steve.horsley on 2007-06-21
My understanding is that the ubuntu-desktop package is a meta-package that contains no useful files (just a changelog and a copyright notice) but that has a lot of dependencies. This is so that installing the ubuntu-desktop feature calls in all the other packaged like OpenOffice that Ubuntu want to install by default.

Uninstalling OpenOffice therefore requires ubuntu-desltop because it is a dependency. But uninstalling the desktop doesn't actually do any harm - it just removes that changelog and copyright file again. So ubuntu-desktop is really nothing more than a shopping list for the default install. Once you've done your shopping, you can throw away the list.

---

### Post by John.Michael.Kane on 2007-06-21
Here's another option.
```
sudo aptitude install x-window-system-core gnome-core firefox synaptic gnome-app-install
```

---

### Post by RTrev on 2007-06-21
> **SD-Plissken said:**
> Here's another option.
```
sudo aptitude install x-window-system-core gnome-core firefox synaptic gnome-app-install
```

Hmm.  I think the best thing to do is create a virtual machine in vmware, and try it there first.  I'll see which combinations of commands result it what outcome.  Nice thing about virtual machines, just take a snapshot before you do something dumb, and then after you hose your system you roll back to the snapshot and try something different.  :-)

I'll try various things in the VM until I end up with what I want, and then do it for real.

---

### Post by RTrev on 2007-06-21
> **SD-Plissken said:**
> Here's another option.
```
sudo aptitude install x-window-system-core gnome-core firefox synaptic gnome-app-install
```

Okay, results so far.  It's been a weird experience.  :)

Using the line suggested above resulted in almost what I wanted, except for a couple of glitches that I don't understand.

1) All of the stuff came down, except that about 6 seconds before it was due to finish there was an error about the remote server had terminated the session.  I wasn't sure what it was I didn't get.

I tried a dpkg-reconfigure xserver-xorg and was told that it wasn't installed.  I thought, okay, no problem, and installed xorg.  The system then began systematically removing everything it had installed.. which on a DSL line takes a while.  It was removing things that I definately would be needing, like HAL, Gedit, all of the Gnome components along with what looked like many other things.

So I got close, and this is the first time ever that an install did **not**  force OpenOffice or Evolution on me, although I did see the Evolution-data-server come down.. it must be used for other things I guess.

So, can we patch up that install line so that I can configure xorg when we're done?  I kind of need it, because I run a dual head setup with Twinview.  And any thoughts as to why installing xorg would uninstall everything else?  Or might this all have worked if not for the glitch on the last file or two when I got disconnected?

Thanks, very close!

---

### Post by blackened on 2007-06-21
For a minimal install, the best way I've found is to first install the server edition (choose nothing when it asks what sort of server you want to run (LAMP etc.), then when you have a command prompt sudo apt-get install ubuntu-desktop. That should cover the basic stuff, and you can build from there.

---

### Post by RTrev on 2007-06-21
Ah, it must have been that fluke in the download.  I started it again, and this time it all worked except that gdm wasn't installed.  When I install that, it comes up and no garbage in the menus.

I think we've got it nailed.  Thanks for your help!!

---

### Post by D!mon on 2007-06-21
of course you will receive notifications without ubuntu-desktop package! There is some description in the package info complaining that it is better not to remove this package, but I always had it removed due to customizations I made and I even did dist-upgrade to feisty without any problems. Look, in debian you even don't have ubuntu-desktop but you are still notified about updates aren't you?;)

---

### Post by RTrev on 2007-06-21
> **blackened said:**
> For a minimal install, the best way I've found is to first install the server edition (choose nothing when it asks what sort of server you want to run (LAMP etc.), then when you have a command prompt sudo apt-get install ubuntu-desktop. That should cover the basic stuff, and you can build from there.

I thought I'd tried that a long time ago, and it brought down all of the dependencies of ubuntu-desktop, which left me with the same install I'd have if I'd done it normally.  Maybe it's changed in the meantime, but I'm where I want to be now, so no problems.

Thanks!

---

### Post by RTrev on 2007-06-21
> **D!mon said:**
> of course you will receive notifications without ubuntu-desktop package! There is some description in the package info complaining that it is better not to remove this package, but I always had it removed due to customizations I made and I even did dist-upgrade to feisty without any problems. Look, in debian you even don't have ubuntu-desktop but you are still notified about updates aren't you?;)

Well, after this last install, I don't have ubuntu-desktop anymore anyway, to I guess it's moot.  :-)

It still seems cleaner to me to not install some of the stuff in the first place than to try to remove it.  Synaptic does things like installing 9 files when you ask for a package,  but when you remove the package Synaptic leaves 8 of the files on the system.  

Anyway, I did this all in a virtual machine, so I think I'm going to do it on the bare metal this time.  Thanks, Bob

---

### Post by RTrev on 2007-06-22
> **jputman01 said:**
> please let us know how the minimal disk goes, sounds like a good alternative i may have to give a try sometime

All I can say is that I should have done this a LONG time ago!  My system used to take over 30 seconds to boot.. now we're looking at about 15 seconds.  It used to take (I never timed it) roughly the same 30 seconds to shut down... and now it's more like 10 seconds.

Everything is quicker and snappier, and I have some favorite speed-up tricks I haven't even used yet.

There are some downsides, but not many.  One is that various functions that I was used to on the menus are no longer there, so I have to figure out what they were and install them again.  

Also, there are some services that aren't running, which will partly explain the speedier boots and shutdowns, but some of those services I didn't want or need anyway.  I'll reinstall VMware server, and I have a virtual machine already set up of Gutsy, and see what those menu items are that I'm missing, 

One thing I'm doing this time that I never did before is using Aptitude exclusively for all installs and removals.  Since I installed most everything using it, it makes sense to keep using it.  I think it's a far better system.

So, I'm very happy.. and a big THANK YOU to all who helped and encouraged!  :-)  :-)  :-)

---

### Post by Brian96 on 2007-06-23
Does the mini.iso installation allow you to choose a partition on which to install? (I'd like to try the minimal install, but want to be *sure* I don't overwrite my windows partition.) --Thanks

---

### Post by RTrev on 2007-06-23
> **Brian96 said:**
> Does the mini.iso installation allow you to choose a partition on which to install? (I'd like to try the minimal install, but want to be *sure* I don't overwrite my windows partition.) --Thanks

Yep.  You just type in server and hit enter, and the rest of the install looks pretty much the same except in text mode.  The partitioning portion is just like the usual. 

Once booted, then you have to figure out what you want, which is interesting.  For me, x-window-system-core turned out to be a good start.  Enjoy.  You won't believe how much faster things run once you get the system set up.  Mine literally does an orderly shutdown in just a tad over 5 seconds!

Cheers,
Bob

---

### Post by Brian96 on 2007-06-23
> **RTrev said:**
> Yep.  You just type in server and hit enter, and the rest of the install looks pretty much the same except in text mode.  The partitioning portion is just like the usual. 

Once booted, then you have to figure out what you want, which is interesting.  For me, x-window-system-core turned out to be a good start.  Enjoy.  You won't believe how much faster things run once you get the system set up.  Mine literally does an orderly shutdown in just a tad over 5 seconds!

Cheers,
Bob

So you used the commands provided by sd-plissken, but added xorg?

---

### Post by RTrev on 2007-06-23
> **Brian96 said:**
> So you used the commands provided by sd-plissken, but added xorg?

Something odd happened the first time when I used those commands, so the second time I began doing them one at a time.  It seems that if you just do:

```

aptitude install x-window-system-core

```

..you get the other things automatically.  What I realized eventually was that there was a metafile called ubuntu-minimal.  The level I think I'm at now is ubuntu-standard.  That seems like the right place to be if you want a fast, clean system without all the crud.  It's possible that I could have just issued that one command and gotten to where I am now:

```

aptitude install ubuntu-standard

```

If you go to the next level, ubuntu-desktop, that's when all the heavy stuff comes piling in.. Evolution, OpenOffice, and a ton of other junk.  So, you might want to save yourself all of the hassle I went through slowly adding one package after another, and just do the standard.

Not being sure what your intended outcome is, it's hard to say.  I have things to where I want them, but maybe you should experiment and see what you want and what you'd rather not have.  It makes a *huge* difference on my system, which is a dual-core AMD with 4G of RAM and over a Terrabyte of disk.  Whether you'd see the same improvements on another machine I can't say, but my guess would be that a lower powered machine might see even *more* improvement.

Please report back.. and we'll get this down to a science.  Maybe it would even be worth a howto eventually, if other people find they aren't using all the software and would like a giant speed boost.

---

### Post by Brian96 on 2007-06-23
> **RTrev said:**
> Something odd happened the first time when I used those commands, so the second time I began doing them one at a time.  It seems that if you just do:

```

aptitude install x-window-system-core

```

..you get the other things automatically.  What I realized eventually was that there was a metafile called ubuntu-minimal.  The level I think I'm at now is ubuntu-standard.  That seems like the right place to be if you want a fast, clean system without all the crud.  It's possible that I could have just issued that one command and gotten to where I am now:

```

aptitude install ubuntu-standard

```

If you go to the next level, ubuntu-desktop, that's when all the heavy stuff comes piling in.. Evolution, OpenOffice, and a ton of other junk.  So, you might want to save yourself all of the hassle I went through slowly adding one package after another, and just do the standard.

Not being sure what your intended outcome is, it's hard to say.  I have things to where I want them, but maybe you should experiment and see what you want and what you'd rather not have.  It makes a *huge* difference on my system, which is a dual-core AMD with 4G of RAM and over a Terrabyte of disk.  Whether you'd see the same improvements on another machine I can't say, but my guess would be that a lower powered machine might see even *more* improvement.

Please report back.. and we'll get this down to a science.  Maybe it would even be worth a howto eventually, if other people find they aren't using all the software and would like a giant speed boost.

I'll think about minimal vs standard. Was that command INSTEAD of xorg/synaptic/...?

My issues are a little different from yours. I always end up using only a few of the standard apps, but adding a whole bunch more. I don't use Evolution, Gaim, yadda yadda. I don't want the default media players. Stuff like that.

I also would like to speed up boot time, etc.

Have you figured out the main differences between standard and minimal? I found this link for breezy: [http://packages.ubuntu.com/breezy/base/ubuntu-minimal](http://packages.ubuntu.com/breezy/base/ubuntu-minimal)

Again, please clarify whether you also had to manually install xorg (which I've read is the new package for x-window-system-core, hence your earlier issues).

---

### Post by Brian96 on 2007-06-23
After surfing a little more, ubuntu-standard and ubuntu-minimal are only listed under Breezy on the site I linked before. I am assuming that is not a problem, though. What do you think? If these are meta-packages, then they should, I would think, install current versions of the related packages, right?

Oh, one more question. This is AFTER you install server at the command line when booting from the minimal CD, right?

---

### Post by kerry_s on 2007-06-23
it goes like this

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

install the server/minimal
login
sudo su
apt-get install xorg gdm synaptic (your wm)
reboot(ctrl+alt+delete)
select your wm in the session menu and login
open synaptic, remove some more stuff if you want, otherwise just install what ever else you want.

i use->

apt-get install xorg gdm synaptic fluxbox 

which is just enough to get me into gui, after that then i remove/install what ever i want with synaptic. i'll usually grab a file manager first(emelfm or mc or both) than a gui editor(mousepad, i like it tells me when i'm using it as root). if you want to stay small mc is enough, it has it's own editor(mcedit) which can also be used instead of installing several editors, depends on how much function you want.

---

### Post by RTrev on 2007-06-23
> **Brian96 said:**
> I'll think about minimal vs standard. Was that command INSTEAD of xorg/synaptic/...?

My issues are a little different from yours. I always end up using only a few of the standard apps, but adding a whole bunch more. I don't use Evolution, Gaim, yadda yadda. I don't want the default media players. Stuff like that.

I also would like to speed up boot time, etc.

Have you figured out the main differences between standard and minimal? I found this link for breezy: [http://packages.ubuntu.com/breezy/base/ubuntu-minimal](http://packages.ubuntu.com/breezy/base/ubuntu-minimal)

Again, please clarify whether you also had to manually install xorg (which I've read is the new package for x-window-system-core, hence your earlier issues).

To answer your second question first, yes you will get the correct packages provided you downloaded the correct iso mini file.  

Here's what I suggest you try:

```

sudo aptitude install x-window-system-core

```

Then boot the system and see what you have.  Of course you will have to set up your X system if you want a gui, so that will be:

```

sudo dpkg-reconfigure xserver-xorg

```

Reboot again, and you'll find a super speedy boot, no uspash nonsense, virtually nothing but a bare bones Gnome system which will include:

You'll pull down the System menu, and find virtually nothing in it.  You won't be able to configure things the way you want without more packages.

And then, when you discover you miss a lot of the features that you had before, go to a command prompt and enter this:

```

sudo aptitude install ubuntu-standard

```

I **THINK** This will give you what I have now.  But I might be wrong.  I have the full ubuntu-standard, but I may also have other parts and pieces because I added individual packages as I needed them.  For example, I wanted USB devices to be recognized and mounted when inserted, so I had to look through the repos to find what I needed.  Some of the things I needed had dependencies which got installed also.  One thing I wanted was the Restricted Drivers Manager, because I run dual monitors with Twinview.  I could have just downloaded the nvidia-glx module of my choice, but this way I'll be notified if one gets updated.  And speaking of notified, I had to find the packages that handled notification, and so on.  I should have written it down, but it was a trial and error process.  I think I must still be missing one thing, because after the instantaneous boot, my mouse doesn't work for a few seconds after I log in.  Then it comes to life and all is well.  There's a piece missing in the USB detection and setup, I guess.

So, in my case I eventually wanted to see how close I was to ubuntu-standard, so I did this:

```

sudo aptitude -s install ubuntu-standard

```

The -s tells it to simulate what would happen but to not really do it.  I fould that it said nothing would happen.. no packages would be installed.  Meaning I was at that level already.  

So, I think you'd get a cleaner install by just doing the single install of ubuntu-standard, and then seeing how you like that.  I'm going to reinstall and try that next.

Mind you, I might be wrong.  You might end up with a lot of junk like the usplash screen and all of that, but I don't think so.  I think you'll get about what I have now, which is a standard system, which boots faster, does everything faster, and feels much more responsive.

One thing I noticed in studying this is that, even though I never used Openoffice for anything, it was being pre-loaded during every boot!  No wonder booting was slow!  It's stuff like that that we're getting rid of by doing the custom install.

Note to Ubuntu: Please consider adding an option on the install CD to let the user choose a standard install OR a full-blown one.  It would be simple, I think, to just ask if they want the default set of software or if they'd rather choose their own.

Regards,
Bob

---

### Post by RTrev on 2007-06-23
> **Brian96 said:**
> After surfing a little more, ubuntu-standard and ubuntu-minimal are only listed under Breezy on the site I linked before. I am assuming that is not a problem, though. What do you think? If these are meta-packages, then they should, I would think, install current versions of the related packages, right?

Oh, one more question. This is AFTER you install server at the command line when booting from the minimal CD, right?

**Okay, I was wrong about virtually everything I told you!**  <g>  Sorry!

Here's what I just did, on another disk.

1) Boot the mini disk and boot it as server

2) ```
sudo aptitude install gdm
```

3) ```
sudo aptitude install xorg
```

4) ```
sudo dpkg-reconfigure xserver-xorg
```

5) ```
sudo shutdown -r 0
```

This got me to the same place I was at *before* I began adding modules manually.  I even have the same problem with the mouse not responding for 5-10 seconds after the desktop is up and ready to go.  I was completely wrong about the levels.  When I first booted from the mini version, that installed the ubuntu-standard.  Just a very basic command-line system, ready to be set up as a server.

Installing GDM brought about everything with it, including even Firefox.  Installing XORG was the finishing step to having a basic no frills Ubuntu Gnome system.

Trying to install ubuntu-minimal at that point did nothing.. no packages to download.

At that point, I guess you just begin adding packages to do each of the things you want the system to be able  to do.

In short, as far as I can tell at this point in my exploration, there is no way to install a clean Ubuntu which runs fast and doesn't have the huge (and I'm sure in many people's case, unwanted)  packages added to it, preloading and slowing everything down.

I hope I'm wrong.  It's quite tedious to figure out each package you need for the functionality we're used to with Ubuntu.  System tools, notifications of updates, accessories like the archive manager, gedit, everything needs to be manually installed.. as far as I can tell now.

It's worth it, at least to me, but it's a pain.

There simply has to be a better way.

Evolution is supposed to be a great program, but I already have my email needs covered.  OpenOffice is supposed to be great, but I already have that covered too.  I don't want a dog-slow system, and I can't believe that Ubuntu apparently doesn't offer the option of a nice, fast system without all the extras.  We don't need usplash, for example.. it's much more interesting to use just the quiet option, and watch the steps the system takes as it comes up.

My next experiment is going to be to start from the other direction.  I'm going to install a full, normal Ubuntu, with all the baggage, and then see how hard it is to remove everything that's slowing things down without inadvertantly hosing the system.  If I can do it this way, and have it run as fast as the version I'm using right now runs, I'll post about it if anyone wants to know.

Having all of this stuff dragging down the system is like refusing to sell a Ferrari unless the customer agrees to always tow a big boat behind it.  :-)

Bob

---

### Post by kerry_s on 2007-06-23
> **RTrev said:**
> **Okay, I was wrong about virtually everything I told you!**  <g>  Sorry!

Here's what I just did, on another disk.

1) Boot the mini disk and boot it as server

2) ```
sudo aptitude install gdm
```

3) ```
sudo aptitude install xorg
```

4) ```
sudo dpkg-reconfigure xserver-xorg
```

5) ```
sudo shutdown -r 0
```

This got me to the same place I was at *before* I began adding modules manually.  I even have the same problem with the mouse not responding for 5-10 seconds after the desktop is up and ready to go.  I was completely wrong about the levels.  When I first booted from the mini version, that installed the ubuntu-standard.  Just a very basic command-line system, ready to be set up as a server.

Installing GDM brought about everything with it, including even Firefox.  Installing XORG was the finishing step to having a basic no frills Ubuntu Gnome system.

Trying to install ubuntu-minimal at that point did nothing.. no packages to download.

At that point, I guess you just begin adding packages to do each of the things you want the system to be able  to do.

In short, as far as I can tell at this point in my exploration, there is no way to install a clean Ubuntu which runs fast and doesn't have the huge (and I'm sure in many people's case, unwanted)  packages added to it, preloading and slowing everything down.

I hope I'm wrong.  It's quite tedious to figure out each package you need for the functionality we're used to with Ubuntu.  System tools, notifications of updates, accessories like the archive manager, gedit, everything needs to be manually installed.. as far as I can tell now.

It's worth it, at least to me, but it's a pain.

There simply has to be a better way.

Evolution is supposed to be a great program, but I already have my email needs covered.  OpenOffice is supposed to be great, but I already have that covered too.  I don't want a dog-slow system, and I can't believe that Ubuntu apparently doesn't offer the option of a nice, fast system without all the extras.  We don't need usplash, for example.. it's much more interesting to use just the quiet option, and watch the steps the system takes as it comes up.

My next experiment is going to be to start from the other direction.  I'm going to install a full, normal Ubuntu, with all the baggage, and then see how hard it is to remove everything that's slowing things down without inadvertantly hosing the system.  If I can do it this way, and have it run as fast as the version I'm using right now runs, I'll post about it if anyone wants to know.

Having all of this stuff dragging down the system is like refusing to sell a Ferrari unless the customer agrees to always tow a big boat behind it.  :-)

Bob


Why dont you just do it the right way in the first place, all you have to do is say what you want.
here is for a bare bones gnome.

> it goes like this

[http://archive.ubuntu.com/ubuntu/dis...tboot/mini.iso](http://archive.ubuntu.com/ubuntu/dis...tboot/mini.iso)

install the server/minimal
login
sudo su
apt-get install xorg gdm synaptic gnome-core
reboot(ctrl+alt+delete)
select gnome in the session menu and login
open synaptic, remove some more stuff if you want, otherwise just install what ever else you want.


Also if you really want a fast system you need to ditch the DE, using a simple WM like fluxbox,icewm,openbox, blackbox,wmaker,etc..
will give you a much faster system than even a minimal DE.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by RTrev on 2007-06-23
> **kerry_s said:**
> Why dont you just do it the right way in the first place, all you have to do is say what you want.
here is for a bare bones gnome.

lol.., I've been asking this for months, and the answer is never the same.  :-)  I'll try your way, thanks!

> 
Also if you really want a fast system you need to ditch the DE, using a simple WM like fluxbox,icewm,openbox, blackbox,wmaker,etc..
will give you a much faster system than even a minimal DE.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

DE is another name for Gnome?  Or short for Desktop Environment?

What I really want is something as close to Gnome as I can get, and which runs the same apps with no problems.  I normally use Gedit, Gftp, VLC, Pan, Firefox, GnomeBaker, and I'm quite comfortable with Nautilus, Archive Manager, and the other utilities.  What setup would you suggest?

Thanks,
Bob

---

### Post by kerry_s on 2007-06-23
You can run gnome apps(aka: gtk+ apps) in any environment. depending on the app and how tied in to gnome it is, running it in a less hoggish(is that a word?) environment can be a big difference.

> normally use Gedit, Gftp, VLC, Pan, Firefox, GnomeBaker, and I'm quite comfortable with Nautilus, Archive Manager, and the other utilities

gedit is okay but slow as hell, i reccommend you try geany.
gftp there are lots of ftp options, but this should be okay, it's not part of gnome and is gtk+
vlc, i use that all the time
pan is gtk2, no problems running anywhere
firefox is the smae thing, can be run in any WM
gnomebaker not the most dependable, try graveman
nautilus is a dog slow, try thunar the only difference you'll notice is speed. thunar is way faster.
archive manager, the last time used that it was very buggy. try unp no frills no thrills just speed. but if you must have it it works just fine in other WM's.

the problem is you've gotten so use to gnome that, you haven't bothered to try other things, some better some, some with the exact same features. live alittle, expand your mind. ;)

---

### Post by RTrev on 2007-06-24
> **kerry_s said:**
> You can run gnome apps(aka: gtk+ apps) in any environment. depending on the app and how tied in to gnome it is, running it in a less hoggish(is that a word?) environment can be a big difference.



gedit is okay but slow as hell, i reccommend you try geany.
gftp there are lots of ftp options, but this should be okay, it's not part of gnome and is gtk+
vlc, i use that all the time
pan is gtk2, no problems running anywhere
firefox is the smae thing, can be run in any WM
gnomebaker not the most dependable, try graveman
nautilus is a dog slow, try thunar the only difference you'll notice is speed. thunar is way faster.
archive manager, the last time used that it was very buggy. try unp no frills no thrills just speed. but if you must have it it works just fine in other WM's.

the problem is you've gotten so use to gnome that, you haven't bothered to try other things, some better some, some with the exact same features. live alittle, expand your mind. ;)

I'm saving a copy of this post, and will try out each one of those!  :tongue:

Actually, I'm using xfce right now, and I'm liking it a lot!  Would you say this one would be in the running for a good fast platform, or are there others that are far faster?  This is even pretty.. I was getting a bit tired of brown.  <g>  It's run everything I've tossed it at so far, and has all kinds of neat features.  Not all that much different than Gnome, really, except it feels light on its feet!  I think I may just grab the normal Xubuntu iso and give it a try for a while.  As it is, I've got a mishmash (is that a word?) of apps from my old install and Xfce all showing up, and it's hard to tell what's standard.  I clicked on a jpg and it opened in eog.

Hey, thanks for pulling me out of my rut!  :-)

Bob

---

### Post by Brian96 on 2007-06-24
Okay. Here are my thoughts.

1. I installed from the mini.iso. Unfortunately my DSL connection isn't the best, so I think next time I'll just burn the server CD and install from that. Otherwise I like this approach. (I guess it's pay me now or pay me later. I takes a while to download the server cd, but it also takes a while to download the packages the mini way. At work I think the mini will be fine.)

2. I sort of made a hybrid of psychocats.net and the suggestions on this thread and after installing the server and upgrading/updating ran >  sudo aptitude install xorg xterm gdm gnome-core menu firefox gksu synaptic gnome-app-install 

3. I think that menu is definitely unnecessary, and some of the others may be as well. Next time I think I'll just do the setup kerry_s posted (plus restricted-manager and a couple of others I know I'll want out of the box).

I agree that I, too, may be limiting myself because of my familiarity with Gnome. In the months to come I definitely intend to do my homework and work toward moving to something more streamlined than Gnome. (I love the look and feel of E17, can't wait until it stabilizes.) For now, though, this install did give me most of what I was looking for: Fewer pre-installed applications. I am not (yet) noticing much in the way of speed enhancements, though.

---

### Post by Brian96 on 2007-06-24
> **RTrev said:**
> I'm saving a copy of this post, and will try out each one of those!  :tongue:

Actually, I'm using xfce right now, and I'm liking it a lot!  Would you say this one would be in the running for a good fast platform, or are there others that are far faster?  This is even pretty.. I was getting a bit tired of brown.  <g>  It's run everything I've tossed it at so far, and has all kinds of neat features.  Not all that much different than Gnome, really, except it feels light on its feet!  I think I may just grab the normal Xubuntu iso and give it a try for a while.  As it is, I've got a mishmash (is that a word?) of apps from my old install and Xfce all showing up, and it's hard to tell what's standard.  I clicked on a jpg and it opened in eog.

Hey, thanks for pulling me out of my rut!  :-)

Bob

I ran into some of that when I played around with KDE a few weeks ago. Never did get a good feel for KDE itself. Keep us posted on Xfce. I toyed with using it, but your thread reinforced my Gnome-bias. ;)

---

### Post by RTrev on 2007-06-24
> **Brian96 said:**
> 
I agree that I, too, may be limiting myself because of my familiarity with Gnome. In the months to come I definitely intend to do my homework and work toward moving to something more streamlined than Gnome. (I love the look and feel of E17, can't wait until it stabilizes.) For now, though, this install did give me most of what I was looking for: Fewer pre-installed applications. I am not (yet) noticing much in the way of speed enhancements, though.

Just for kicks, since you'll be reinstalling anyway, try getting the xfce desktop and playing with that a bit.  I'm really liking it so far.  And Kerry is sure right.. Thunar is like lightning!  See what you think if you haven't already tried it.  It's funny, but I remember trying it a long time ago and not liking it.  Maybe they've spiffed it up a bit in the meantime.

Bob

---

### Post by Brian96 on 2007-06-24
> **RTrev said:**
> Just for kicks, since you'll be reinstalling anyway, try getting the xfce desktop and playing with that a bit.  I'm really liking it so far.  And Kerry is sure right.. Thunar is like lightning!  See what you think if you haven't already tried it.  It's funny, but I remember trying it a long time ago and not liking it.  Maybe they've spiffed it up a bit in the meantime.

Bob

I think I'll try it at work. Once I learn it and decide if I like it then I may go back and "aptitude remove" gnome-core and use it. I am curious to find out what it will be like to install a barebones Xfce (is there a minimal/core package for Xfce?) onto a server install.

Oh, by the way, the ubuntu-minimal and ubuntu-standard didn't work for me from the command line (although I see them in synaptic); that is why I went with gnome-core.

---

### Post by RTrev on 2007-06-24
> **Brian96 said:**
> I think I'll try it at work. Once I learn it and decide if I like it then I may go back and "aptitude remove" gnome-core and use it. I am curious to find out what it will be like to install a barebones Xfce (is there a minimal/core package for Xfce?) onto a server install.

Oh, by the way, the ubuntu-minimal and ubuntu-standard didn't work for me from the command line (although I see them in synaptic); that is why I went with gnome-core.

I'm thinking of going with the full Xfce to start with, Brian, so I'll be able to get some sense of what parts I want to keep and what parts I don't want.  Then later, if there's even a need to, play with a minimal install.  Everything is so fast now that I don't know that it would be worth the effort to go minimal.

I'm also figuring maybe Kerry will come back with a recommendation of some other one to try, so I think I'll just get some sleep now and play with this tomorrow.   You know, since the days of DOS, I haven't had fun with computers until Linux.  Windows was never fun.  :)

Bob

---

### Post by Brian96 on 2007-06-24
> **RTrev said:**
> I'm thinking of going with the full Xfce to start with, Brian, so I'll be able to get some sense of what parts I want to keep and what parts I don't want.  Then later, if there's even a need to, play with a minimal install.  Everything is so fast now that I don't know that it would be worth the effort to go minimal.

I'm also figuring maybe Kerry will come back with a recommendation of some other one to try, so I think I'll just get some sleep now and play with this tomorrow.   You know, since the days of DOS, I haven't had fun with computers until Linux.  Windows was never fun.  :)

Bob

I know what you mean about Windows. Although I have recently come across a couple of toys from M$ that I really like: There is an image-resizer toy that allows you to resize images (even multiple images at once) from a right-click menu on the image in a folder view. GREATLY simplifies shrinking images for e-mail. Then they have their sync-toy that synchronizes folders, and I've founded it a good bit easier to use than rsync. Oh, and then there is the toy that changes the ALT + TAB to thumbnail previews rather than just icons. (Didn't mean to hi-jack, but if anybody knows of Linux apps that will do these things, let me know.)

So, what command did you use to install Xfce?

---

### Post by RTrev on 2007-06-24
> **Brian96 said:**
> I know what you mean about Windows. Although I have recently come across a couple of toys from M$ that I really like: There is an image-resizer toy that allows you to resize images (even multiple images at once) from a right-click menu on the image in a folder view. GREATLY simplifies shrinking images for e-mail. Then they have their sync-toy that synchronizes folders, and I've founded it a good bit easier to use than rsync. Oh, and then there is the toy that changes the ALT + TAB to thumbnail previews rather than just icons. (Didn't mean to hi-jack, but if anybody knows of Linux apps that will do these things, let me know.)

So, what command did you use to install Xfce?

Can't help with the Windows part, but I'm sure someone else will be able to.  As for the Xfce, I just installed xubuntu-desktop.  Then you can select that to be either a one-time deal or your default desktop when you log in.  Use the options in the lower left before entering your username, etc.

Have fun!

---

### Post by kerry_s on 2007-06-24
brian, this can be cut down to save you some typing->

sudo aptitude install xorg xterm gdm gnome-core menu firefox gksu synaptic gnome-app-install
to
sudo aptitude install xorg gdm gnome-core firefox synaptic gnome-app-install

xterm is always installed and gksu is part of gdm, gnome has it's own menu thing.

---

### Post by kerry_s on 2007-06-24
> **Brian96 said:**
> I think I'll try it at work. Once I learn it and decide if I like it then I may go back and "aptitude remove" gnome-core and use it. I am curious to find out what it will be like to install a barebones Xfce (is there a minimal/core package for Xfce?) onto a server install.

Oh, by the way, the ubuntu-minimal and ubuntu-standard didn't work for me from the command line (although I see them in synaptic); that is why I went with gnome-core.

a bare bones xfce4 is->

apt-get install xorg gdm synaptic xfce4 mousepad xfce4-appfinder

when it starts up there won't be nothing but a empty launcher in the top right corner, so it's up to you to set up the bar. in case you don't know the easiest way to create launchers is to use the xfce4-appfinder, you just drag the app from the finder to the launcher properties window or desktop if you like icons on the desktop. i always liked xfce4 better than gnome, but somethings take work. i still go back to xfce4 from time to time. but right now my main system is down, needs a rebuild, so i'm just stuck with my trusty vaio 450mhz 256ram laptop, this thing needs all the help it can get, so nothing but light for now. :p

---

### Post by kerry_s on 2007-06-24
anyways you guys have fun, don't be afraid to try things, especially if you know your going to install a different setup anyways. before you wipe that setup your playing with try some app's, just open synaptic and browse through those 20,000+ apps and try some before you wipe and install another setup. there's just so man options it's ridiculous.

here's a pic of my plain ol no thrills minimal+fluxbox ;)

---

### Post by RTrev on 2007-06-24
> **kerry_s said:**
> a bare bones xfce4 is->

apt-get install xorg gdm synaptic xfce4 mousepad xfce4-appfinder


Okay, I'm realizing now that I'm really confused.  Isn't gdm the Gnome Display Manager?  

Let me see, we need an X environment, so we get xorg.  Where do things like GTK and Metacity fit in?  I'm really not sure of the basics here, but it sounds like xfce rides on Gnome's back?

> 
when it starts up there won't be nothing but a empty launcher in the top right corner, so it's up to you to set up the bar. in case you don't know the easiest way to create launchers is to use the xfce4-appfinder, you just drag the app from the finder to the launcher properties window or desktop if you like icons on the desktop. i always liked xfce4 better than gnome, but somethings take work. i still go back to xfce4 from time to time. but right now my main system is down, needs a rebuild, so i'm just stuck with my trusty vaio 450mhz 256ram laptop, this thing needs all the help it can get, so nothing but light for now. :p

What would you use if you had all the horsepower you wanted?  I mean, I'm sensing that these light setups are seen as compromises, but I'm not entirely clear on what one's losing.  Let me even pin you down and ask what you'd install on a dual-core AMD 3800+ with 4G and lots of disk?  I'm trying to settle on something fast and clean that I like, so I can forget about the operating system and just start being productive.  Linux has the advantage of unlimited choices, which can also be a curse!  :-)

---

### Post by Brian96 on 2007-06-24
> **RTrev said:**
> Okay, I'm realizing now that I'm really confused.  Isn't gdm the Gnome Display Manager?  

Let me see, we need an X environment, so we get xorg.  Where do things like GTK and Metacity fit in?  I'm really not sure of the basics here, but it sounds like xfce rides on Gnome's back?




I'm still learning, too, but from what I am coming to understand, GTK and Metacity would be part of your window manager/desktop environment. Gnome desktop environment uses Metacity as its window manager. When you install a WM instead of a DE, you are just getting the basics for xorg to display windows. GTK--as far as my mind can grasp it--is like a protocol for the graphics. That is, a GTK+ GUI was created using GTK. Gnome, XFCE, and others are based on GTK+. Still not sure of the implications for this.

In other news, I removed gnome-core and installed Xfce4 using Kerry-S' sample command and wasn't impressed. For one thing, it comes with its own media player, one of my nit-picky no-nos. Also, I found it more difficult to configure the panels (though there were a couple of advantages), in particular, I couldn't find a straight-forward way to make the panel transparent.

So, I'm back to gnome-core. It's not bad, and my startup time from the Session Manager window is much faster than with full Ubuntu-desktop. And I didn't get so many pre-installed apps. I'll keep playing around. I can see why Gnome is so heavy, as there are so many things you can do through the basic GUI. I'd like to find a lighter one, but I have some peculiar specifications.

One weird thing, though. When I change my themes in Gnome now, my window borders change their appearance but not their color. So I have everything in "glossy," but the window border is still brown. :(

---

### Post by John.Michael.Kane on 2007-06-24
> **RTrev said:**
> Okay, I'm realizing now that I'm really confused.  Isn't gdm the Gnome Display Manager?  

Let me see, we need an X environment, so we get xorg.  Where do things like GTK and Metacity fit in?  I'm really not sure of the basics here, but it sounds like xfce rides on Gnome's back?



What would you use if you had all the horsepower you wanted?  I mean, I'm sensing that these light setups are seen as compromises, but I'm not entirely clear on what one's losing.  Let me even pin you down and ask what you'd install on a dual-core AMD 3800+ with 4G and lots of disk?  I'm trying to settle on something fast and clean that I like, so I can forget about the operating system and just start being productive.  Linux has the advantage of unlimited choices, which can also be a curse!  :-)

Flux is a window manager for X.
 
Metacity is a compositing window manager for the GNOME desktop environment,and uses GTK+.

GTK+ GIMP Toolkit, is a widget toolkit for the X Window System used to create the graphical user interfaces.

xfce is based on the GTK+ 2.x toolkit, and It uses the Xfwm window manager.

RTrev if time is not an issue i would suggest you set up all three environments gnome/xfce/flux along with conk, and run them for a minimum of one to two weeks. This will allow you to see how each environment needs to be set up, and what each environment uses in the way of resources, 

Taking your system specs into account one can list it like this. 
1)gnome fast
2)xfce faster
3)flux fastest

Even with the lightest/cleanest/leanest setup, in the end it's going to depend on what programs you install, and what services you run.

---

### Post by Phixion on 2007-06-24
I have a Intel Core 2 Quad Extreme Edition QX6800 2.93GHz with 4GB RAM and I've been using server install for a while. 

It's just so much quicker than a default install and gives you more options when installing what you want.

I don't install due to a bad system - as you can see, but because I like to know whats on my system and not have my computer bloated with stuff it doesn't need.

---

### Post by Brian96 on 2007-06-24
> **Phixion said:**
> I have a Intel Core 2 Quad Extreme Edition QX6800 2.93GHz with 4GB RAM and I've been using server install for a while. 

It's just so much quicker than a default install and gives you more options when installing what you want.

I don't install due to a bad system - as you can see, but because I like to know whats on my system and not have my computer bloated with stuff it doesn't need.

That's what this thread is all about. :D

---

### Post by sourjax on 2007-06-24
I have not posted in this thread before, but I  must say that this thread has helped me alot in the last 24 hours (which is how long I've used Ubuntu).

I have Ubuntu installed as a Dual boot with Windows Vista on the PC I'm using "as we type". I'm trying to install Ubuntu on an HP Pavilion that was designed for Windows ME and I can't get it to install with the Regular disk so I'm trying the methods described in the thread.

So, I said all that to say this. 

Thank you.
SourJax

---

### Post by RTrev on 2007-06-24
> **Phixion said:**
> I have a Intel Core 2 Quad Extreme Edition QX6800 2.93GHz with 4GB RAM and I've been using server install for a while. 

It's just so much quicker than a default install and gives you more options when installing what you want.

I don't install due to a bad system - as you can see, but because I like to know whats on my system and not have my computer bloated with stuff it doesn't need.

Do you happen to remember which packages you installed?  When I got all done, I still had some strange things that weren't quite right, but I had no idea what I needed to fix them.  For example, in a terminal I would type sudo nautilus or sudo gedit and as I would work I kept seeing little warnings in the terminal window about (and I'm going by memory) /usr/bin/esd not found.

What would be nice would be a meta package pre-configured to install just what we want.  I wonder if that's possible?  Create it on our own system, burn to CD, tell Syntaptic to add that to the sources.lst file.  Then just select that and our custom install is recreated.  Hmm.

---

### Post by RTrev on 2007-06-24
> **SD-Plissken said:**
> Flux is a window manager for X.
 
Metacity is a compositing window manager for the GNOME desktop environment,and uses GTK+.

GTK+ GIMP Toolkit, is a widget toolkit for the X Window System used to create the graphical user interfaces.

xfce is based on the GTK+ 2.x toolkit, and It uses the Xfwm window manager.

RTrev if time is not an issue i would suggest you set up all three environments gnome/xfce/flux along with conk, and run them for a minimum of one to two weeks. This will allow you to see how each environment needs to be set up, and what each environment uses in the way of resources, 

Taking your system specs into account one can list it like this. 
1)gnome fast
2)xfce faster
3)flux fastest

Even with the lightest/cleanest/leanest setup, in the end it's going to depend on what programs you install, and what services you run.

Thanks.. that cleared it up quite a bit.  And good advice about trying them on for a while before making a decision.  I think I'll do just that.

BTW, when we talk about speed in this context, we are pretty much just talking about the responsiveness of the gui, right?  We aren't talking load time for application launches (assuming an application of the same size), or improved performance of the various programs we might run.  Gimp will take as long to load under flux as under Gnome or KDE, correct?

Thanks again,
Bob

---

### Post by Brian96 on 2007-06-26
I've run into a glitch. I installed Ubuntu on my work computer using the methods described in this thread. I initially installed gnome-core, then added other WMs. I decided I want to try a pure WM (without all the Gnome stuff in there), so I typed "sudo remove --purge gnome-core." The only thing it removed was gedit, gdb, eog, and maybe one other thing. The rest of the DE is still there.

I thought maybe some of the other WMs had tapped into gnome and become dependent on it, so I removed all of the other WMs and tried it again and it found nothing to uninstall. How can I get rid of gnome-core without typing the name of every package?

Later I may try reinstalling gnome-core and then uninstalling it. Think that might work?

--Thanks

---

### Post by RTrev on 2007-06-26
> **Brian96 said:**
> I've run into a glitch. I installed Ubuntu on my work computer using the methods described in this thread. I initially installed gnome-core, then added other WMs. I decided I want to try a pure WM (without all the Gnome stuff in there), so I typed "sudo remove --purge gnome-core." The only thing it removed was gedit, gdb, eog, and maybe one other thing. The rest of the DE is still there.

I thought maybe some of the other WMs had tapped into gnome and become dependent on it, so I removed all of the other WMs and tried it again and it found nothing to uninstall. How can I get rid of gnome-core without typing the name of every package?

Later I may try reinstalling gnome-core and then uninstalling it. Think that might work?

--Thanks

LOL!  I did the same thing.. or at least very similar.  I needed something that I knew how to do in Nauilus, but couldn't find any way to do manually.  So  sudo aptitude install nautilus.  It brings with it damn near ALL of Gnome.  When I sudo aptitude purge nautilus, it removed the one file.  I said something unprintable and reinstalled from scratch.  

I thought aptitude, and the later versions of Synaptic, were noted for being really good at this.  I'm not sure what happened, but I'm going to be more careful in the future.

Have you found something you like yet?  I'm having a bit of trouble because of my dual monitors, and most of the desktops tend to not grok dual monitors and position things right in the middle.  :)

---

### Post by Brian96 on 2007-06-26
> **RTrev said:**
> LOL!  I did the same thing.. or at least very similar.  I needed something that I knew how to do in Nauilus, but couldn't find any way to do manually.  So  sudo aptitude install nautilus.  It brings with it damn near ALL of Gnome.  When I sudo aptitude purge nautilus, it removed the one file.  I said something unprintable and reinstalled from scratch.  

I thought aptitude, and the later versions of Synaptic, were noted for being really good at this.  I'm not sure what happened, but I'm going to be more careful in the future.

Have you found something you like yet?  I'm having a bit of trouble because of my dual monitors, and most of the desktops tend to not grok dual monitors and position things right in the middle.  :)

At home I'm sticking with Gnome as the "base" because it keeps things simpler for the family, and because of Gnome's excellent language support.

At work I am thinking about going more nearly minimalist and going the WM-only route. For work I like fluxbox (for now) because its default configuration is so clean and I am comfortable navigating through the menus (I need more icons at home for the family). I tried icewm and wasn't thrilled. fvwm-crystal looks nice, but I don't have time to learn how to configure it from the command line. I REALLY like E17, which I think is aspiring to become a full desktop environment. So at home I switch between Gnome and E17 (though I have a few others installed). At work I plan to switch between fluxbox and E17.

Oh, and I wasn't real impressed with Xfce.  It is light for a desktop environment, and it might have fared better if the core did not include media players I don't want (that biased me against it right off the bat).

As for purging Gnome, I think I'm just gonna reinstall. That way I can get a better feel for the advantages of not installing a DE.

---

### Post by evaldas on 2007-07-02
I guess I can make some small input to this thread.

As I understand ubuntu-minimal package is the very very bare bones of the cmd-line system (no xorg, no etc, even no man pages)
ubuntu-standard - the comfortable working environment for command line (ubuntu-minimal plus man pages, etc; still no xorg). Right now I'm installing ubuntu-minimal, and later will upgrade to ubuntu-standard, and will post which packages got additionally installed.

Next thing, always use aptitude for installing packages. It will keep the history about installed packages and their dependencies (but you'll have to use aptitude from the very beginning), and when you want to remove package, it also removes dependencies. For example, to purge Gnome, try this:
```
$ sudo aptitude purge --purge-unused gnome-core
```

---

### Post by Brian96 on 2007-07-02
Here is another update:

I am using Xfce4 at work. It was easy to remove the "offending" media players (much easier than from a full install), and it is growing on me. Not sure I'll use it at home, though.

In general I much prefer this method of installation. The main benefits I have found are:
1. By installing the whole OS straight from the repositories you get the most recent versions of packages, whereas with a Live CD install you get whatever flavor there was when the disc was burned. So, unlike a Live CD install, I didn't have the "updates available" icon flashing the first time I booted up.
2. I MUCH prefer adding new packages to a slim install rather than trying to remove packages from a full install.
3. While booting up and so forth is not particularly faster in my case, I have noticed that my system is using a lot less memory.

Also, as evaldas noted, if you start off installing programs with aptitude it helps keep things a lot cleaner. What I've been doing is using Synaptic to research packages, finding out their features, dependencies, and names, then going into a terminal and installing the packages with aptitude (of course, you have to exit Synaptic first!).

I've been trying to find a session/desktop manager in the repositories I like. I tried GDM, but it is HUGE, and some themes have icon troubles. I've tried XDM, but it doesn't allow for selecting a WM session. KDM is, well, KDM. Not a whole lot smaller than GDM, and therefore no real advantage that I can see. I really, really like the look and feel (and small size) of Entrance (E17's manager), but 1) it turns off the shutdown/restart features in the X session, requiring you to log out before shutting down, and 2) it crapped out on me when I tried to install a new theme.

---

### Post by RTrev on 2007-07-02
> **Brian96 said:**
> Here is another update:

Also, as evaldas noted, if you start off installing programs with aptitude it helps keep things a lot cleaner. What I've been doing is using Synaptic to research packages, finding out their features, dependencies, and names, then going into a terminal and installing the packages with aptitude (of course, you have to exit Synaptic first!).


Hi Brian,

Do you know about the aptitude search and show commands?  Also about the -s qualifier?  Those things make if fairly easy and quick to just do everything from the command line.

I'm still undecided at this point, and other priorities have arisen, so this has been back-burnered for a bit.  I'll be back at it fairly soon though!  :)

Bob

---

### Post by Brian96 on 2007-07-02
> **RTrev said:**
> Hi Brian,

Do you know about the aptitude search and show commands?  Also about the -s qualifier?  Those things make if fairly easy and quick to just do everything from the command line.

I'm still undecided at this point, and other priorities have arisen, so this has been back-burnered for a bit.  I'll be back at it fairly soon though!  :)

Bob

I pretty much just use "install" and "remove --purge" or something along those lines. Haven't gotten too far into aptitude yet. Project du jour is actually capturing, editing, and burning DVDs from home movies. Still doing it (and tweaking it) in Windows, but planning to take a shot at Linux apps for this soon.

---

### Post by RTrev on 2007-07-02
> **Brian96 said:**
> I pretty much just use "install" and "remove --purge" or something along those lines. Haven't gotten too far into aptitude yet. Project du jour is actually capturing, editing, and burning DVDs from home movies. Still doing it (and tweaking it) in Windows, but planning to take a shot at Linux apps for this soon.

That's a riot.. this is the main project that has side-tracked me from exploring more OS installs.. copying all my DVDs and CDs to the system, so I have a backup.  Also, neat thing I found, VLC will play the .iso files just as if they were the DVD.  Much better playback, also, as there are no pauses from the DVD drive.

We seem to think along the same lines, eh?  :-)

Bob

---

### Post by kerry_s on 2007-07-02
> **Brian96 said:**
> Here is another update:

I am using Xfce4 at work. It was easy to remove the "offending" media players (much easier than from a full install), and it is growing on me. Not sure I'll use it at home, though.

In general I much prefer this method of installation. The main benefits I have found are:
1. By installing the whole OS straight from the repositories you get the most recent versions of packages, whereas with a Live CD install you get whatever flavor there was when the disc was burned. So, unlike a Live CD install, I didn't have the "updates available" icon flashing the first time I booted up.
2. I MUCH prefer adding new packages to a slim install rather than trying to remove packages from a full install.
3. While booting up and so forth is not particularly faster in my case, I have noticed that my system is using a lot less memory.

Also, as evaldas noted, if you start off installing programs with aptitude it helps keep things a lot cleaner. What I've been doing is using Synaptic to research packages, finding out their features, dependencies, and names, then going into a terminal and installing the packages with aptitude (of course, you have to exit Synaptic first!).

I've been trying to find a session/desktop manager in the repositories I like. I tried GDM, but it is HUGE, and some themes have icon troubles. I've tried XDM, but it doesn't allow for selecting a WM session. KDM is, well, KDM. Not a whole lot smaller than GDM, and therefore no real advantage that I can see. I really, really like the look and feel (and small size) of Entrance (E17's manager), but 1) it turns off the shutdown/restart features in the X session, requiring you to log out before shutting down, and 2) it crapped out on me when I tried to install a new theme.

you missed "wdm" it's like xdm but with the options of gdm. ;)
which by the way was made for wmaker, also a very interesting wm you should also try. :p
yes, it will work with xfce.

---

### Post by Brian96 on 2007-07-07
> **kerry_s said:**
> you missed "wdm" it's like xdm but with the options of gdm. ;)
which by the way was made for wmaker, also a very interesting wm you should also try. :p
yes, it will work with xfce.

On your advice I tried WDM. Wasn't real impressed, though. For one thing, it didn't get the Enlightenment script right (and I didn't feel like reconfiguring it).

Anyway, I am back to GDM. I guess I can live with it. Once I change the theme the icon problem works itself out anyway.

---

### Post by RTrev on 2007-07-09
> **Brian96 said:**
> On your advice I tried WDM. Wasn't real impressed, though. For one thing, it didn't get the Enlightenment script right (and I didn't feel like reconfiguring it).

Anyway, I am back to GDM. I guess I can live with it. Once I change the theme the icon problem works itself out anyway.

So Brian, have you got this down to a science yet?  If I want to try Enlightenment, what do I need to load to get the best setup?

Thanks,
Bob

p.s.  Do you also choose another kernel to install, rather than stay with the server kernel?

---

### Post by Brian96 on 2007-07-09
> **RTrev said:**
> So Brian, have you got this down to a science yet?  If I want to try Enlightenment, what do I need to load to get the best setup?

Thanks,
Bob

p.s.  Do you also choose another kernel to install, rather than stay with the server kernel?

Not a science, really, but I do prefer the mini.iso and server install to a full LiveCD install. Before, if I recall, Ubuntu loaded (before I opened any apps) using about 22% of my 1 GB of RAM. Now it loads at 9%. You do have to know a little about what you are doing to be sure you have the apps you need (I've found researching in Synaptic and then installing through Aptitude to be the best way for me). But if you want something lighter but still have the stability and community support of Ubuntu, this is a good way to go.

As for Enlightenment, there is a huge difference between E16 and E17, and I much prefer E17, though it is very unstable. Someday I may try to run it from a fresh server install as my only DE, but for now I have it added to my only kernel. I really don't like the file manager in E17, and there are a few things I don't know how to do, but it is light and it is really attractive. But it is not nearly as stable as Xfce, Gnome, or KDE. I installed it using this HowTo: [http://ubuntuforums.org/showthread.php?t=319336](http://ubuntuforums.org/showthread.php?t=319336)

I have an ATI sound card at home, so I am not able to get Beryl working properly without sacrificing some other functions I like. Otherwise I would use the same setup at home I use at school: Xfce with Beryl. It gives me the stability of a DE with the productivity and eye-candy enhancements of Beryl. At home I am using gnome-core lately as my main session, and really like the stability, especially as I've been doing a lot with the video capture-edit-burn stuff.

I kept 10 GB on my HDD unformatted so I can install another distro if I want. I may do another server install there and try something like E17 by itself. I'd also like to see what a full xubuntu-desktop and kubuntu-desktop looks like without having to commit to loading all the libraries and dependencies on my main partition.

Anyway, that is my update. I think this may be my favorite thread on this board. :)

---

### Post by RTrev on 2007-07-10
Wow, I really like E17!  Hard to believe it's so light and yet so aesthetically pleasing.

I may just do a custom mini-cd install of this on another disk and see what happens.  Thanks for the links and all.  And yes, this is a fun thread.. and whatever we end up with we'll have a more solid understanding of the whole system.  

Now just to be clear, the things I absolutely must have, when starting a mini CD install intended to run only E17, would be what?  I'm still a bit fuzzy on what is carrying what.  Xserver I think is a given, but do I need the whole GDM?  I wouldn't think so, but who knows.  I'll have to go back through all of this thread and see.. it's probably listed somewhere.

When I'm at the command line ready to begin, I guess I have to first add that extra repository for E17.  I usually do that with a text editor in /etc/apt/sources.list, but I'm not sure that directory will even exist at that point.  Well, we'll find out.  :)

If I could run this desktop with as little else running underneath it as possible, that would be close to ideal for my particular tastes.  Of course I have to see how often it blows up on me.  :-)

Very cool!

---

### Post by Seisen on 2007-07-10
The directory still exists but instead of using gedit or kate you can use vim or nano to edit the file.

---

### Post by Old Pink on 2007-07-10
> **wpshooter said:**
> Go into Synaptic, find the applications that you want to get rid of/uninstall and **mark for removal **but DON'T "**mark for complete removal**", so the dependencies do not get uninstalled.

Good luck.

Actually, mark for removal still removes dependencies. The only difference is mark for complete removal purges the application completely, leaving no configuration files behind.

Why not just remove everything you want, then run **sudo aptitude install ubuntu-desktop **afterwards? :)

---

### Post by RTrev on 2007-07-10
> **Old Pink said:**
> Actually, mark for removal still removes dependencies. The only difference is mark for complete removal purges the application completely, leaving no configuration files behind.

I must be a bit confused about the removal part.  If I install a package with aptitude, and then remove it again with purge, or any other method I've tried, I still find residue all over the disk that wasn't there before.  Icons, directories, config files, and things of that sort.  I've yet to find a way to remove everything without doing a search and then going through and deleting the stuff manually.  And of course if one of the files has an odd name that doesn't show up in my search, then it stays.

Doing this in Synaptic I find the same thing.  I might install k3b into my Gnome setup, and of course it brings a ton of libraries with it.  When I do mark for complete removal, it doesn't remove the libraries.. it just removes k3b itself.

What am I doing wrong?

tks,
Bob

---

### Post by RTrev on 2007-07-10
> **Seisen said:**
> The directory still exists but instead of using gedit or kate you can use vim or nano to edit the file.

Ah, okay.. sounds easy enough.  I'm going to try it later today or tomorrow.  Thanks.

---

### Post by stepan2 on 2007-07-10
get the alternate cd , isntall , and do apt-get install kdebase . that way you will have minimal kde

---

### Post by Nythain on 2007-07-10
so instead of installing ubuntu-desktop wich is going to install all the software from ubuntu that the user doesnt want... why not
A. start with a command line system install from an alternate iso
B. sudo aptitutde install gnome-desktop-environment
C. work from there... looking at the dependencies, the gnome-desktop-environment package seems to be a lot more minimal in what it installs than the full blown ubuntu-desktop package
D. if you want KDE then i would suggest the kde-core package, as it will install the very minimum required for a kde environment

just my two cents (though if you wanted a real minimal system you could just install x and fluxbox :) )

---

### Post by RTrev on 2007-07-10
> **Nythain said:**
> 
just my two cents (though if you wanted a real minimal system you could just install x and fluxbox :) )

That's more what I'm thinking, although I'm leaning more toward E17.  I'm running E now and it's already seg-faulted on me once, though, so maybe I need to use it a bit more and see how flaky it's going to be.  :-)

So, I'm thinking use the Mini-CD instead of the alternate, to get just a server install, and go from there.  Last time I did this, with just a minimal Gnome install, the system was incredibly light and fast.  Even with that weird Feisty bug they are trying to fix having to do with CDROM drives, my boot time was still under 20 seconds, and that was without doing any of the tweaks I've since learned about.. like profiling the boot, setting noatime, nodiratime, writeback, and so on.

I just have to figure out what E17 needs as an absolute minimum base to sit on top of.

Thanks,
Bob

---

### Post by Brian96 on 2007-07-10
> **RTrev said:**
> Wow, I really like E17!  Hard to believe it's so light and yet so aesthetically pleasing.

I may just do a custom mini-cd install of this on another disk and see what happens.  Thanks for the links and all.  And yes, this is a fun thread.. and whatever we end up with we'll have a more solid understanding of the whole system.  

Now just to be clear, the things I absolutely must have, when starting a mini CD install intended to run only E17, would be what?  I'm still a bit fuzzy on what is carrying what.  Xserver I think is a given, but do I need the whole GDM?  I wouldn't think so, but who knows.  I'll have to go back through all of this thread and see.. it's probably listed somewhere.

When I'm at the command line ready to begin, I guess I have to first add that extra repository for E17.  I usually do that with a text editor in /etc/apt/sources.list, but I'm not sure that directory will even exist at that point.  Well, we'll find out.  :)

If I could run this desktop with as little else running underneath it as possible, that would be close to ideal for my particular tastes.  Of course I have to see how often it blows up on me.  :-)

Very cool!

GDM: There is an E17 session manager called entrance which is in the repositories with E17. It was okay, but I disliked two things: 1) when I tried to install a theme I downloaded it crashed (it could have been the theme, but in any event I disliked that) and 2) it turned off the "shutdown" features in the x-session, meaning that I could only log out and then shut down from Entrance. Kind of annoying. GDM is pretty big, but it is stable and it already includes gksu for running GUI apps from root (don't know if you do that a lot anyway). Not sure I answered your question, but there are alternatives to GDM. I suppose it is possible to do without a session manager altogether and start the session from the command line in server. Not sure I'm ready for that, though.

An E17-only install: I would probably install xserver (or whatever the command is--can't remember right now), e17, gdm (or entrance or whatever), and synaptic. The apt/sources.list will already be present after a server install, so you should be able to edit it with nano from the command line.

I may try this on the weekend as well. I've wondered what E17 would be like without some of the Gnome stuff I already had installed underneath. I can't see it being my main session, though, especially as I really don't like its file manager.

---

### Post by Brian96 on 2007-07-10
> **Nythain said:**
> so instead of installing ubuntu-desktop wich is going to install all the software from ubuntu that the user doesnt want... why not
A. start with a command line system install from an alternate iso
B. sudo aptitutde install gnome-desktop-environment
C. work from there... looking at the dependencies, the gnome-desktop-environment package seems to be a lot more minimal in what it installs than the full blown ubuntu-desktop package
D. if you want KDE then i would suggest the kde-core package, as it will install the very minimum required for a kde environment

just my two cents (though if you wanted a real minimal system you could just install x and fluxbox :) )

A: Same principle, we just use the mini.iso and start off with the newest packages downloaded straight from the repos (rather than the versions that were fresh when the alternate CD was created and then updating when we reboot the first time).
B: We've found that gnome-core is a good, light Gnome. For newbies, this has given us something lighter but with the stability and familiarity of Gnome.

Fluxbox: I've played around with it and some of the other WM-only "ultralites" but there has been too much of a learning curve. I'm still stuck in a GUI-world for the most part and therefore have trouble with some of the configurations for these other WMs. Currently I'm really liking the Xfce4/Beryl combo. Good balance of stability, lightness, productivity tools, and eye candy.

---

### Post by RTrev on 2007-07-10
> **Brian96 said:**
> I may try this on the weekend as well. I've wondered what E17 would be like without some of the Gnome stuff I already had installed underneath. I can't see it being my main session, though, especially as I really don't like its file manager.

I see what you mean about that file manager!  Although, to be fair, I didn't explore how customizable it might be.  If it's going to insist on opening a new window every time I want to go into a sub-directory, then it isn't going to work for me.  What were they thinking?  :-)

Thanks for the help.. gonna go for it either tonight or tomorrow.  Want to make sure my ducks are lined up before I do this.

Not to take us off-topic, but one tweak I want is to be able to use mdadm software RAID-0 on my two Raptor system disks.  It's weird.. it worked perfectly while I experimented in a VMware Server machine, but then I tried it on the bare metal and it bombed big time.  ](*,)

Bob  :)

---

### Post by RTrev on 2007-07-16
> **Brian96 said:**
> GDM: There is an E17 session manager called entrance which is in the repositories with E17. It was okay, but I disliked two things: 1) when I tried to install a theme I downloaded it crashed (it could have been the theme, but in any event I disliked that) and 2) it turned off the "shutdown" features in the x-session, meaning that I could only log out and then shut down from Entrance. Kind of annoying. GDM is pretty big, but it is stable and it already includes gksu for running GUI apps from root (don't know if you do that a lot anyway). Not sure I answered your question, but there are alternatives to GDM. I suppose it is possible to do without a session manager altogether and start the session from the command line in server. Not sure I'm ready for that, though.

I've installed xorg, entrance, firefox, and e17, and I'm not finding the shutdown bug you describe.  However, when I pick shutdown, it just sits there, apparently doing nothing, and then suddenly the system is shut down.  Maybe you didn't wait long enough?

I'm doing all of this now in VirtualBox, but I'm building a test machine.. just a little 386 box with a couple of identical 4G drives so I can play with RAID and LVM, and  I think that's going to be a good way to find the ideal setup.  It's like in my software development days, I'd pick the slowest machine I had to develop my code.  If it ran nice and fast on that, then I figured I was home free on most any system.  <g>

One odd thing I've found, though.  In VirtualBox, Win XP Home SP2 boots in about 6 seconds.  The install of E17 boots in about 30 seconds.  I haven't explored this yet to find out where the slowdown is taking place.  I should also add that boot time isn't a big criteria for me, because I leave my machines running most of the time.  Except when I'm doing this kind of work.  <g>

---

### Post by Brian96 on 2007-07-17
> **RTrev said:**
> I've installed xorg, entrance, firefox, and e17, and I'm not finding the shutdown bug you describe.  However, when I pick shutdown, it just sits there, apparently doing nothing, and then suddenly the system is shut down.  Maybe you didn't wait long enough?



It could have been an artifact from adding and removing other session managers, but when I used entrance, my gnome and xfce sessions no longer had shutdown or restart options in the quit menu. The only option was to log out. So I always either logged out or control-alt-backspaced and shutdown from the login window.

Strange about your different boot times. I wonder if it has to do with the different hardware drivers for each setup on a virtual machine. I run Win XP home on bare metal and Win XP pro in a VM in Feisty and my boot times are similar. I've never run any other OS in a VM, though.

---

### Post by Brian96 on 2007-07-19
So I installed another instance of Feisty server on an extra partition on my harddrive. I decided to see what "default" Xubuntu looks like, so I installed xubuntu-desktop. I don't know if an Xubuntu Live CD does the same, but this package also installed Gnome. Do all the *ubuntus do this?

Xubuntu is a lot heavier than I was expecting. It is a little lighter than Ubuntu, but not to the extent I expected. I may wipe it and try kubuntu-desktop to see what that looks like. I'll probably also look at kde-core before trying E17 by itself.

Does anyone know if there is a mini.iso for Gutsy yet?

---

### Post by RTrev on 2007-07-19
> **Brian96 said:**
> So I installed another instance of Feisty server on an extra partition on my harddrive. I decided to see what "default" Xubuntu looks like, so I installed xubuntu-desktop. I don't know if an Xubuntu Live CD does the same, but this package also installed Gnome. Do all the *ubuntus do this?

Xubuntu is a lot heavier than I was expecting. It is a little lighter than Ubuntu, but not to the extent I expected. I may wipe it and try kubuntu-desktop to see what that looks like. I'll probably also look at kde-core before trying E17 by itself.

Does anyone know if there is a mini.iso for Gutsy yet?

I found the same thing, Brian.  Xubuntu dragged in a lot of Gnome material, and really I didn't see a significant speed difference.  It may be that we are running powerful enough machines that we aren't going to see much difference.  I'm setting up a low-powered machine to test on, and when that's ready I'll really be starting to do more experimenting.  My suspicion at this point is that with a high-horsepower machine, we might as well run whatever environment we find most comfortable, and trim it down so it isn't wasting resources running services we will never use.

I'm coming to suspect that the light-weight environments are not much of a boon to people with powerful systems.

Are you beginning to sense the same?

As to the mini, or even the alternate, CDs for Gutsy, I've failed to find them if they exist.  If anyone knows where to get them, please ping us.  I have a hunch those might only be produced once Gutsy is ready for release, but have no real knowledge of how they do it.

---

### Post by RTrev on 2007-07-19
You know, I just realized that we could probably install the current mini CD, change all references in /etc/apt/sources.list from "feisty" to "gutsy" and end up with about what we want.  I'll try that and see what happens.  <g>

---

### Post by RTrev on 2007-07-19
Well, that went over like the proverbial lead balloon.  I booted the the feisty mini CD, then changed the sources.list to all "gutsy" instead of "feisty."

Did a sudo aptitude update, rebooted, did an upgrade, rebooted, then did a dist-upgrade, and tried to reboot.

```

[  3268.581178] BUG: unable to handle kernel paging request at virtual address f88340e0
[  3628.581391]  printing eip:
[  3628.581590] c0105822
[  3628.581981] Recursive die() failure, output suppressed
[  3628.582599] Kernel panic - not syncing: Attempted to kill init!

```

And there it sits, frozen solid.  

This was in VirtualBox, and for all I know it might not be a problem on the bare hardware.

Living on the bleeding edge is kind of fun.  :)

---

### Post by revertex on 2007-07-20
first thing, the faster method to break things in ubuntu is to use aptitude.

aptitude plays very well with debian, but ubuntu packages are a bit different, and aptitude don't handle it very well.

second, there is no such thing like a minimal version of ubuntu, at least not like you want.

i've tryed several distros in the past, and i can assure you that ubuntu is not suited for frugal install, because ubuntu is tailored for inexperienced people.

it's not mean that experienced people can't  run ubuntu, but because the way ubuntu rely on dependencies and metapackages it's almost impossible.

as example, if you try to remove laptop detect, a useless package for desktop users, it will remove powernowd, removing laptop mode tolls will remove acpi-support.

also if you install acpid, it will install acpi-support that will install radeontoll, another useless crap for nvidia users.

if you can live with small annoyances go ahead, but if you can fell in control and have only what you need installed i suggest you archlinux or slackware, or even debian.

Arch is a great distro, well documented, therefore rely only on cli tools it's pretty easy to install and configure, and forums are very friendly.

---

### Post by Brian96 on 2007-07-20
> **revertex said:**
> first thing, the faster method to break things in ubuntu is to use aptitude.

aptitude plays very well with debian, but ubuntu packages are a bit different, and aptitude don't handle it very well.

second, there is no such thing like a minimal version of ubuntu, at least not like you want.

i've tryed several distros in the past, and i can assure you that ubuntu is not suited for frugal install, because ubuntu is tailored for inexperienced people.

it's not mean that experienced people can't  run ubuntu, but because the way ubuntu rely on dependencies and metapackages it's almost impossible.

as example, if you try to remove laptop detect, a useless package for desktop users, it will remove powernowd, removing laptop mode tolls will remove acpi-support.

also if you install acpid, it will install acpi-support that will install radeontoll, another useless crap for nvidia users.

if you can live with small annoyances go ahead, but if you can fell in control and have only what you need installed i suggest you archlinux or slackware, or even debian.

Arch is a great distro, well documented, therefore rely only on cli tools it's pretty easy to install and configure, and forums are very friendly.

Thanks for your input. On this thread we use "minimal" very relatively. We like the stability and community that Ubuntu offers, but we also like it a little leaner. This thread was born out of frustration with working backward from a full Ubuntu desktop installation to get a little bit lighter system.

But you are correct: if you are looking for a truly lean and mean setup, you need to look at another distro. This thread is for Ubuntu users who want to find a relatively straightforward way to jettison some of the features that we will never use.

---

### Post by Brian96 on 2007-07-20
> **RTrev said:**
> I found the same thing, Brian.  Xubuntu dragged in a lot of Gnome material, and really I didn't see a significant speed difference.  It may be that we are running powerful enough machines that we aren't going to see much difference.  I'm setting up a low-powered machine to test on, and when that's ready I'll really be starting to do more experimenting.  My suspicion at this point is that with a high-horsepower machine, we might as well run whatever environment we find most comfortable, and trim it down so it isn't wasting resources running services we will never use.

I'm coming to suspect that the light-weight environments are not much of a boon to people with powerful systems.

Are you beginning to sense the same?

As to the mini, or even the alternate, CDs for Gutsy, I've failed to find them if they exist.  If anyone knows where to get them, please ping us.  I have a hunch those might only be produced once Gutsy is ready for release, but have no real knowledge of how they do it.

I agree, with a decent system anything (even Windoze) should be fine. I like the idea of squeezing a little more efficiency out of my system, but what this endeavor is really about for me is the psychological effect of having a "cleaner" Ubuntu install.

Now I'm ready to jettison Xubuntu from my test partition. I hope uninstalls cleanly, If not I may overwrite it with another server install. I guess then I need to image that partition so that I can start over more efficiently next time.

---

### Post by allforcarrie on 2007-07-20
there is supposedly a distro called ubuntu lite but i can never get the website to work. I dont know if they stopped it or what.

---

### Post by RTrev on 2007-07-20
Hi Brian:

I *think* one way we could image our partitions is to simply use dd,  if there's sufficient disk space handy.  Don't hold me to this, but I've been told that a command like:

```

dd if=/dev/sdb3 of=some_file.name

```

Will give us a byte-for-byte copy, to a file, of a drive.  And vice-versa.  I have to play with that a bit and see if there are any gotchas.

When I ran into bugs with the Feisty Alternate CD partitioner, somebody told me a good way to wipe out a drive so that the partitioner wouldn't be able to access the data about it having been a RAID device or whatever in the past:

```

dd if=/dev/zero of=/dev/hda bs=512 count=63

```

This would completely blow away the entire first part of hda, which was what I needed at the time.  Seems a versatile command that might be perfect for snapshots of drives in certain states.  Of course be careful what you specify as the output.  It doesn't stop and give any friendly warnings about "Are you sure?"  :-)

Hi revetex:

Could you elaborate just a bit on the problems with using aptitude with Ubuntu?  I've never been quite clear why we have these seemingly largely redundant commands, and I've heard that apt has added most of the features we like in aptitude, such as being able to cleanly remove anything it installs.

Hi allforcarrie,

Was this Ubuntu Lite an official distribution of Ubuntu?  It sounds interesting, and like something Ubuntu should perhaps consider doing if they haven't already.

Thanks,
Bob

---

### Post by Brian96 on 2007-07-20
> **RTrev said:**
> Hi Brian:

I *think* one way we could image our partitions is to simply use dd,  if there's sufficient disk space handy.  Don't hold me to this, but I've been told that a command like:

```

dd if=/dev/sdb3 of=some_file.name

```

Will give us a byte-for-byte copy, to a file, of a drive.  And vice-versa.  I have to play with that a bit and see if there are any gotchas.

When I ran into bugs with the Feisty Alternate CD partitioner, somebody told me a good way to wipe out a drive so that the partitioner wouldn't be able to access the data about it having been a RAID device or whatever in the past:

```

dd if=/dev/zero of=/dev/hda bs=512 count=63

```

This would completely blow away the entire first part of hda, which was what I needed at the time.  Seems a versatile command that might be perfect for snapshots of drives in certain states.  Of course be careful what you specify as the output.  It doesn't stop and give any friendly warnings about "Are you sure?"  :-)

Hi revetex:

Could you elaborate just a bit on the problems with using aptitude with Ubuntu?  I've never been quite clear why we have these seemingly largely redundant commands, and I've heard that apt has added most of the features we like in aptitude, such as being able to cleanly remove anything it installs.

Hi allforcarrie,

Was this Ubuntu Lite an official distribution of Ubuntu?  It sounds interesting, and like something Ubuntu should perhaps consider doing if they haven't already.

Thanks,
Bob

I've been imaging my partitions for backup using the partimage/clonezilla live cd available here: [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)  I haven't tried restoring from an image yet, but I like that it also includes the tools for imaging NTFS partitions.

I'm toying with trying Elive, a debian distro with Enlightenment as the DE, on my test partition. It is supposedly designed with older rigs in mind. If I like it I may install it on an old box that I keep for emergencies.

At home I've been pretty much just using my Gnome session and at work Xfce with Beryl. It's funny, because the way I have the GUI configured in each is very different, but each feels right in their respective environments. Once I can use Beryl with the proprietary ATI drivers without having to do a workaround I will probably start using that at home as well. I like the ability to have absolutely nothing on the desktop, and so far I most like the way the Xfce/Beryl combination accomplishes this.

---

### Post by revertex on 2007-07-21
> **RTrev said:**
> 
Hi revetex:

Could you elaborate just a bit on the problems with using aptitude with Ubuntu?  I've never been quite clear why we have these seemingly largely redundant commands, and I've heard that apt has added most of the features we like in aptitude, such as being able to cleanly remove anything it installs.

Thanks,


Sure, see yourself this example:

```
aptitude install -s bugzilla
The following NEW packages will be installed:
  bugzilla dbconfig-common libappconfig-perl libchart-perl 
  libconvert-binhex-perl libdbd-mysql-perl libdbi-perl libgd-gd2-perl 
  libgd2-xpm libio-stringy-perl libmailtools-perl libmime-perl 
  libnet-daemon-perl libplrpc-perl libtemplate-perl libtimedate-perl 
  mysql-client mysql-client-5.0 mysql-server mysql-server-5.0
0 packages upgraded, 20 newly installed, 5 to remove and 0 not upgraded.

``````
apt-get install -s bugzilla
The following NEW packages will be installed:
  bugzilla dbconfig-common libappconfig-perl libconvert-binhex-perl
  libdbd-mysql-perl libdbi-perl libio-stringy-perl libmailtools-perl
  libmime-perl libnet-daemon-perl libplrpc-perl libtemplate-perl
  libtimedate-perl mysql-client mysql-client-5.0
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded

```as you can see, aptitude handle dependencies is a total different way than apt.
try the same comparsion with several packages and you will see.

it seems that aptitude was not well ported to handle ubuntu packages, and still handling as debian ones.

also the "autoremove" feature in the latest apt ubuntu versions can handle the removal of reverse dependencies pretty close atitude should do.

it's not the best way for sure, but apt-history can help you to track dependencies.

I did a  "hardcore" cleanup in my 6.10 install, everything was fine until i upgraded to 7.04, the updater rely strongly in some metapackages like ubuntu-desktop, until i reinstalled all the crap again i can't did the upgrade to feisty.

my only solution has reinstall all crapware again, upgrade, then remove all useless stuff again, kinda annoying.

that's the only thing in ubuntu that i dislike, i see the point to make packages dumbproof, but the lack of a better control over what you really want install is a weak point.

if not that wonderful package management and that huge number of packages avaliable, surely ubuntu is the distro have the greater number packages avaliable, i will leave it to archlinux.

pacman is perfect, but apt rules.

why in hell i need radeontools and laptop-mode?

---

### Post by RTrev on 2007-07-21
> **revertex said:**
> Sure, see yourself this example:

<snip>


Wow.. I never actually tested them side by side like that.  Thanks!

> 
my only solution has reinstall all crapware again, upgrade, then remove all useless stuff again, kinda annoying.


Yeah, although actually I usually do a clean install with new versions and then begin snipping and slicing.  We have a slow connection, so I really don't want to be getting routine updates to OpenOffice, and so on.  I do hope the installer gives more options in the future.

I tried the Archie Live CD and I was amazed at the speed.  Hopefully as Ubuntu matures it will offer lean and mean and fast as an install option. 

Thanks...
Bob

---

### Post by Brian96 on 2007-07-21
Well, I tried kde-core this morning. It has much to recommend it, particularly with its configuration console. Still leaning toward the Xfce/Beryl combination, though. After I finish playing around with Elive I may set up either gnome-core or xfce to see if I can get Beryl working without giving up too much else.

---

### Post by Brian96 on 2007-07-21
> **RTrev said:**
> Wow.. I never actually tested them side by side like that.  Thanks!



Yeah, although actually I usually do a clean install with new versions and then begin snipping and slicing.  We have a slow connection, so I really don't want to be getting routine updates to OpenOffice, and so on.  I do hope the installer gives more options in the future.

I tried the Archie Live CD and I was amazed at the speed.  Hopefully as Ubuntu matures it will offer lean and mean and fast as an install option. 

Thanks...
Bob

I guess I had missed that you also have a slow connection. I wonder if doing a server install from the Alternate CD would be better for you?

As I've said before, I definitely prefer building up from a server install to trying to pare down a full installation. I'm not necessarily looking for an ultra-slim setup, just want to avoid some of the extra apps I'll never use. The methods described in this thread accommodate this goal very nicely.

One thing I like about using gnome (over some of the other DEs and WMs) is that when I try to use a document or file for which I have not installed an application, it often looks for an application for me. Saves a little time here and there, especially as I am building up from a server install.

---

### Post by RTrev on 2007-07-21
> **Brian96 said:**
> I guess I had missed that you also have a slow connection. I wonder if doing a server install from the Alternate CD would be better for you?

As I've said before, I definitely prefer building up from a server install to trying to pare down a full installation. I'm not necessarily looking for an ultra-slim setup, just want to avoid some of the extra apps I'll never use. The methods described in this thread accommodate this goal very nicely.

One thing I like about using gnome (over some of the other DEs and WMs) is that when I try to use a document or file for which I have not installed an application, it often looks for an application for me. Saves a little time here and there, especially as I am building up from a server install.

I've never really gotten my head wrapped around the Alternate CD.  Sometimes it kicks into a mode where there is a menu displayed, allowing moving between the major sections like partitioning and so on, and other times it just behaves like the live CD installer and never gives many options.  Not sure what I'm doing wrong there.

I use the Alternate because it gives more partitioning options, like setting up RAID, but had to drop back to Edgy to do that because it seems to be broken in Feisty.

Got what I wanted by  installing Edgy via Alternate, with RAID, then upgrading, then dist-upgrading, and finally getting rid of OO and as much of the other stuff as I could.

What I need to do is learn how to set up the RAID myself after the mini install.

My download speed is about 190 KB / sec, with a favorable tail wind.  So the mini install is tedious, but not unworkable.  Doing it from any other type of CD might not help me much, because I'm still going to have to download all the updates..?

---

### Post by revertex on 2007-07-21
> **Brian96 said:**
> 
One thing I like about using gnome (over some of the other DEs and WMs) is that when I try to use a document or file for which I have not installed an application, it often looks for an application for me. Saves a little time here and there, especially as I am building up from a server install.

maybe you sould take a look at command_not_found package.

---

### Post by Brian96 on 2007-07-21
> **RTrev said:**
> I've never really gotten my head wrapped around the Alternate CD.  Sometimes it kicks into a mode where there is a menu displayed, allowing moving between the major sections like partitioning and so on, and other times it just behaves like the live CD installer and never gives many options.  Not sure what I'm doing wrong there.

I use the Alternate because it gives more partitioning options, like setting up RAID, but had to drop back to Edgy to do that because it seems to be broken in Feisty.

Got what I wanted by  installing Edgy via Alternate, with RAID, then upgrading, then dist-upgrading, and finally getting rid of OO and as much of the other stuff as I could.

What I need to do is learn how to set up the RAID myself after the mini install.

My download speed is about 190 KB / sec, with a favorable tail wind.  So the mini install is tedious, but not unworkable.  Doing it from any other type of CD might not help me much, because I'm still going to have to download all the updates..?

Your download speed seems better than mine! I've never figured that out. I'm going to look for an answer and if I can't find it I may post a thread on it. When I run a download speed test I usually get about 1.5 MB/s (which is wonderful, considering that is the max my service is supposed to accommodate). However, I am lucky if I get 150 KB/s when actually downloading stuff, at least according to the metrics in Synaptic, aptitude, or my torrent client (which I rarely use).

I am using Elive now. I really like it. It does have a lot of applications pre-installed--worse than Ubuntu in my opinion. On the other hand, E17 seems much better. The file manager is not that crappy thing we got from the repos, it's an actual useful file manager. The configurations are a little different as well. Not sure if it will become my new distro, but so far I like it. And as it is based on Debian it is not far out of my comfort zone.

---

### Post by Brian96 on 2007-07-21
> **revertex said:**
> maybe you sould take a look at command_not_found package.

Thanks, I'll check that out.

---

### Post by RTrev on 2007-07-21
> **Brian96 said:**
> Your download speed seems better than mine! I've never figured that out. I'm going to look for an answer and if I can't find it I may post a thread on it. When I run a download speed test I usually get about 1.5 MB/s (which is wonderful, considering that is the max my service is supposed to accommodate). However, I am lucky if I get 150 KB/s when actually downloading stuff, at least according to the metrics in Synaptic, aptitude, or my torrent client (which I rarely use).

Are you sure about that upper case "B" versus a lower case "b"?  I would guess you've got 1.5 M**b** per second download, meaning mega bits.  Divide by 8, for mega BYTES, and it puts you in the 150-200 KB/sec download range.  I suspect we have the same connection, only I might have gotten lucky and had cleaner phone lines or something.

> 
I am using Elive now. I really like it. It does have a lot of applications pre-installed--worse than Ubuntu in my opinion. On the other hand, E17 seems much better. The file manager is not that crappy thing we got from the repos, it's an actual useful file manager. The configurations are a little different as well. Not sure if it will become my new distro, but so far I like it. And as it is based on Debian it is not far out of my comfort zone.


I'll have to take a look at Elive.

I took a quick peek at Arch, and their demo "Archie" live CD blew me away.. everything happens instantly.  Nice clean Xfce desktop.  But it looks like it might be a bit hairy for a noob like me to install.

---

### Post by Brian96 on 2007-07-22
> **RTrev said:**
> Are you sure about that upper case "B" versus a lower case "b"?  I would guess you've got 1.5 M**b** per second download, meaning mega bits.  Divide by 8, for mega BYTES, and it puts you in the 150-200 KB/sec download range.  I suspect we have the same connection, only I might have gotten lucky and had cleaner phone lines or something.



I'll have to take a look at Elive.

I took a quick peek at Arch, and their demo "Archie" live CD blew me away.. everything happens instantly.  Nice clean Xfce desktop.  But it looks like it might be a bit hairy for a noob like me to install.

You are probably right about the download speed thing. Glad I didn't make a thread on it!

The Elive install was a little funky. For one thing, the English is not all that great. It fpes give you a lot of configuration options, but unfortunately not much in the way of application options. I have not yet tried to use synaptic to remove some of the programs I don't want, however. But if you really liked E17 it might be wort looking into.

I wish I could figure out how to get a main menu with a mouse click on the desktop in Gnome. I'm thinking it must be a Metacity thing, but can't figure out how to change that configuration. Both Xfce and KDE made it very simple and straight-forward to change this setting. Strange that Gnome would make it so difficult.

---

### Post by RTrev on 2007-07-22
> **Brian96 said:**
> You are probably right about the download speed thing. Glad I didn't make a thread on it!

The Elive install was a little funky. For one thing, the English is not all that great. It fpes give you a lot of configuration options, but unfortunately not much in the way of application options. I have not yet tried to use synaptic to remove some of the programs I don't want, however. But if you really liked E17 it might be wort looking into.

I wish I could figure out how to get a main menu with a mouse click on the desktop in Gnome. I'm thinking it must be a Metacity thing, but can't figure out how to change that configuration. Both Xfce and KDE made it very simple and straight-forward to change this setting. Strange that Gnome would make it so difficult.

I've always heard that the main thing people dislike about Gnome is its lack of config options.  I saw a thread once where Linus Torvalds was arguing with the Gnome folks, and basically telling them how much he preferred KDE because he could make it behave the way he wanted.  I just never cared much for KDE.. maybe it's an acquired taste.

I'm downloading Elive now.. getting about 140-180 KB/sec.  Probably my wife is doing something downstairs that's eating up some bandwidth.  :-)

Did you find that Elive download to be a bit irritating?  How much is it worth to me to download Elive?  How do I know until I've tried it?  I almost walked away, but it sounded good enough to be worth 5 bucks to play with it for a while.  Cheaper than going to a movie.  :-)

---

### Post by Brian96 on 2007-07-22
> **RTrev said:**
> I've always heard that the main thing people dislike about Gnome is its lack of config options.  I saw a thread once where Linus Torvalds was arguing with the Gnome folks, and basically telling them how much he preferred KDE because he could make it behave the way he wanted.  I just never cared much for KDE.. maybe it's an acquired taste.

I'm downloading Elive now.. getting about 140-180 KB/sec.  Probably my wife is doing something downstairs that's eating up some bandwidth.  :-)

Did you find that Elive download to be a bit irritating?  How much is it worth to me to download Elive?  How do I know until I've tried it?  I almost walked away, but it sounded good enough to be worth 5 bucks to play with it for a while.  Cheaper than going to a movie.  :-)

I found a thread on here somewhere that had links to free torrents of Elive, so that is what I used. I did find the "how much is it worth to you" business a bit arrogant.

Elive is pretty, but it seems a bit buggy. It also takes a long time to boot on my system. But it does seem to offer a better E17 than what I got through the Ubuntu repos. I think it may be because it is older than the one in the repos, but who knows.

I kind of wish I had more than one test partition. I'm not ready to completely jettison Elive yet, but I'm getting curious to try to get Beryl working on this system (but don't want to tinker with my "stable" partition to do it).

---

### Post by koganinja89 on 2007-07-22
Just get slax or something... what the heck is not needed anyway. It is kind of already minimal

---

### Post by RTrev on 2007-07-22
> **Brian96 said:**
> I found a thread on here somewhere that had links to free torrents of Elive, so that is what I used. I did find the "how much is it worth to you" business a bit arrogant.


Wish I'd asked first.  :)  As it is, it's kind of neat, but going to their forum was quite disappointing.  A bunch of people saying "Hey! Is anybody here??"  I'm spoiled by the Ubuntu forums.

> 
Elive is pretty, but it seems a bit buggy. It also takes a long time to boot on my system. But it does seem to offer a better E17 than what I got through the Ubuntu repos. I think it may be because it is older than the one in the repos, but who knows.


Slow on mine too.  I haven't looked to figure out why yet.  It's got potential, but I was disappointed.  I'll keep playing with it, though.

> 
I kind of wish I had more than one test partition. I'm not ready to completely jettison Elive yet, but I'm getting curious to try to get Beryl working on this system (but don't want to tinker with my "stable" partition to do it).

You might want to do what I've done.  We go to flea markets and whatnot, and find entire machines for 5-10 bucks.  Bring them home, and use the parts for this and that.  One of the "that's" is that I'm setting up a cheapo test machine.  It'll have two small (4 or 8G) drives, and will be sitting next to my main machine.  Just swivel my chair and I'll be able to play on real hardware without risking my good machine.

Two reasons for this.  One is that I loaded Elive as a Live CD, and found that it had auto-mounted all of my drives.  That's the sort of behavior I expect from Windows.. "any hardware I find is mine."  And two, I've found that virtual machines, which was my first plan, just don't tell you what you really need to know.  Good example was setting up RAID with the Feisty Alternate CD.  Worked great in the VM, trashed my whole system when I tried it on the hardware.  Grrrrr.  So now nothing gets near my real machine until it's been vetted on the test box.  I think of it as a "sheep dip" machine.  Just a tiny little POS (technical term) box that can be used for nothing but testing and experimenting, and if I blow it away I couldn't care less.  Good way to learn, without disrupting real work.  I've got a stable system now on the real machine that works great.. a very stripped down Ubuntu running RAID-0 on two Raptors, pretty fast and does what I want.  Not going to risk having to rebuild this setup, but still want to play.

If you can spare the download bandwidth, try the Archie Live CD..

---

### Post by Brian96 on 2007-07-22
> **RTrev said:**
> Wish I'd asked first.  :)  As it is, it's kind of neat, but going to their forum was quite disappointing.  A bunch of people saying "Hey! Is anybody here??"  I'm spoiled by the Ubuntu forums.



Slow on mine too.  I haven't looked to figure out why yet.  It's got potential, but I was disappointed.  I'll keep playing with it, though.



You might want to do what I've done.  We go to flea markets and whatnot, and find entire machines for 5-10 bucks.  Bring them home, and use the parts for this and that.  One of the "that's" is that I'm setting up a cheapo test machine.  It'll have two small (4 or 8G) drives, and will be sitting next to my main machine.  Just swivel my chair and I'll be able to play on real hardware without risking my good machine.

Two reasons for this.  One is that I loaded Elive as a Live CD, and found that it had auto-mounted all of my drives.  That's the sort of behavior I expect from Windows.. "any hardware I find is mine."  And two, I've found that virtual machines, which was my first plan, just don't tell you what you really need to know.  Good example was setting up RAID with the Feisty Alternate CD.  Worked great in the VM, trashed my whole system when I tried it on the hardware.  Grrrrr.  So now nothing gets near my real machine until it's been vetted on the test box.  I think of it as a "sheep dip" machine.  Just a tiny little POS (technical term) box that can be used for nothing but testing and experimenting, and if I blow it away I couldn't care less.  Good way to learn, without disrupting real work.  I've got a stable system now on the real machine that works great.. a very stripped down Ubuntu running RAID-0 on two Raptors, pretty fast and does what I want.  Not going to risk having to rebuild this setup, but still want to play.

If you can spare the download bandwidth, try the Archie Live CD..

The last release of Archie was 2005? That seems kind of old for Linux-world. What is it about Archie that you like?

---

### Post by RTrev on 2007-07-22
> **Brian96 said:**
> The last release of Archie was 2005? That seems kind of old for Linux-world. What is it about Archie that you like?

Clean and fast.  Gives some idea of what the goal might be here.  For example, loads GIMP in 4 seconds, **from the CD**.  The whole Arch approach seems to be to add nothing unless there's a reason for it.

---

### Post by Brian96 on 2007-07-22
> **RTrev said:**
> Clean and fast.  Gives some idea of what the goal might be here.  For example, loads GIMP in 4 seconds, **from the CD**.  The whole Arch approach seems to be to add nothing unless there's a reason for it.

Where did you download it from? I can't get the link on the archie.dotsrc.org website to work. I downloaded a torrent I found elsewhere, but can't get it to work.

---

### Post by RTrev on 2007-07-22
> **Brian96 said:**
> Where did you download it from? I can't get the link on the archie.dotsrc.org website to work. I downloaded a torrent I found elsewhere, but can't get it to work.

[http://darkstar.ist.utl.pt/archlinux/other/archie/archie-0.4.1-xfce.iso](http://darkstar.ist.utl.pt/archlinux/other/archie/archie-0.4.1-xfce.iso)

I just stumbled over it.  Didn't even know about Archie, but someone here mentioned Arch so I went searching.  Will be interested in your thoughts if you try it.

---

### Post by Brian96 on 2007-07-22
> **RTrev said:**
> [http://darkstar.ist.utl.pt/archlinux/other/archie/archie-0.4.1-xfce.iso](http://darkstar.ist.utl.pt/archlinux/other/archie/archie-0.4.1-xfce.iso)

I just stumbled over it.  Didn't even know about Archie, but someone here mentioned Arch so I went searching.  Will be interested in your thoughts if you try it.

I found a torrent that purports to be 0.6. The problem I had before is that I'm still learning about torrents and had not downloaded it properly. It is downloading now, so hopefully I'll be able to try it next weekend.

I am a little nervous about trying a new distro. Archie isn't based on Debian is it?

---

### Post by RTrev on 2007-07-22
> **Brian96 said:**
> I found a torrent that purports to be 0.6. The problem I had before is that I'm still learning about torrents and had not downloaded it properly. It is downloading now, so hopefully I'll be able to try it next weekend.

I am a little nervous about trying a new distro. Archie isn't based on Debian is it?

You're a few steps ahead of me.  I've never used a torrent in my life.  And no, as far as I can tell Arch has no lineage from Debian.  But I could be wrong.  I'm just a newbie splashing around in the shallow end of the pool.  Arch looks like it's going to be a bear to install for a noob, because part of the install routine starts right out by asking you to configure your rc.local and things of that sort.  But once we get our heads wrapped around that we'll have a pretty good understanding of the basics, I think.  Many people seem to suggest Arch as a good distro for those who want to learn.

What I liked about Archie was that I could get a peek at what an Arch install might look like when one gets it working.

Ubuntu is my first love in Linux, and I'm pretty dedicated to Ubuntu because of what they've done to further Linux world-wide.  But I don't think it hurts to peek at other distros and maybe learn how to do some of the things Ubuntu does automatically for us.  If there were an "Ubuntu Lean and Mean Performance" release, I'd probably just live happily with that, and I'll bet the Ubuntu wizards could put together something that would blow the socks off of other distros, but I suspect that such a distro is a ways down the road.

---

### Post by Brian96 on 2007-07-22
> **RTrev said:**
> You're a few steps ahead of me.  I've never used a torrent in my life.  And no, as far as I can tell Arch has no lineage from Debian.  But I could be wrong.  I'm just a newbie splashing around in the shallow end of the pool.  Arch looks like it's going to be a bear to install for a noob, because part of the install routine starts right out by asking you to configure your rc.local and things of that sort.  But once we get our heads wrapped around that we'll have a pretty good understanding of the basics, I think.  Many people seem to suggest Arch as a good distro for those who want to learn.

What I liked about Archie was that I could get a peek at what an Arch install might look like when one gets it working.

Ubuntu is my first love in Linux, and I'm pretty dedicated to Ubuntu because of what they've done to further Linux world-wide.  But I don't think it hurts to peek at other distros and maybe learn how to do some of the things Ubuntu does automatically for us.  If there were an "Ubuntu Lean and Mean Performance" release, I'd probably just live happily with that, and I'll bet the Ubuntu wizards could put together something that would blow the socks off of other distros, but I suspect that such a distro is a ways down the road.

Sounds scary. I'll go ahead and download it, but I'm not sure I'm ready to do much learning anytime soon. ;)

I am comfortable with Debian-based things because of my familiarity with Synaptic and apt-get. I'm not sure if only Debian uses these, but I am a little nervous about having to learn a new package manager.

If you find yourself needing (or wanting) to use torrents, the torrent software that comes default in gnome is very easy to use (may be called gnome-torrent; I'm in XP and can't look it up). It's pretty much just like downloading any other file from the internet. My problem is that I got fancy and installed a different torrent client and got myself confused. :confused:

Maybe I should just go back to tweaking gnome-core and xfce. I have decent stability there. Elive has good eye candy, but it is not very stable for me so far. This is the problem with Linux: unlimited opportunities to experiment and tinker. Definitely a double-edged sword.

---

### Post by RTrev on 2007-07-22
> **Brian96 said:**
> S
Maybe I should just go back to tweaking gnome-core and xfce. I have decent stability there. Elive has good eye candy, but it is not very stable for me so far. This is the problem with Linux: unlimited opportunities to experiment and tinker. Definitely a double-edged sword.

I expect that's where I'll stay also.  But seeing Archie run gave me a little different perspective on what the end result could be.. which is I suppose what they intended.  Now maybe you won't be impressed, and if that's the case then I apologize for dragging you into it.  But it sounds like we're looking for about the same thing.. something fast and light and with only the components we want.. and it appears that it will be worth it when we get there.  The mini install brings with it more stuff than I would really want....

---

### Post by capink on 2007-07-22
for those interested in doing a minimal install by removing packages, here is a script that might help:

[http://ubuntuforums.org/showthread.php?t=442974]("http://ubuntuforums.org/showthread.php?t=442974")

---

### Post by RTrev on 2007-07-22
> **capink said:**
> for those interested in doing a minimal install by removing packages, here is a script that might help:

[http://ubuntuforums.org/showthread.php?t=442974]("http://ubuntuforums.org/showthread.php?t=442974")

Wow.. that's wild!  I'll have to try it, rather than pester you with questions.. of which I have many of course.  :-)

Thanks!

---

### Post by RTrev on 2007-07-23
> **capink said:**
> for those interested in doing a minimal install by removing packages, here is a script that might help:

[http://ubuntuforums.org/showthread.php?t=442974]("http://ubuntuforums.org/showthread.php?t=442974")

Well, I had some interesting experiences playing with this.  It's a super idea, but I must be doing something wrong.  I was working in VMware Server, if that makes a difference.

First, I did a full install of the Ubuntu Feisty Live CD, which gave me the whole Gnome system, with all of the junk.

Then I ran your system, thinking I would end up with a clean XFCE install.  All I changed in your choice of software was the language support -- change to -en.  During the run, all looked good, and it was removing OpenOffice, etc.  It hit a couple of files it couldn't find, like the audacious-plugins-extra, and one other I forget, but they seemed like things I could figure out later.

When it finished, I rebooted and my desktop was a plain gray, with nothing I could do.. no mouse clicks did anything, and there were no panels, etc.

So then I thought I'd try it with an XFCE install, and installed the Xubuntu Live CD.  This time when I ran it, it wanted to **install** OpenOffice and a bunch of other junk.  

I love the concept, and it seems well-written.. I suspect it's some dumb error on my part.  Any ideas?

One suggestion for a feature, if you are interested and if it can be done.  It would be neat to have it create the list of software that is *currently* installed, and then we could go through that list and remove things we knew we didn't want.  This would perhaps be easier than having to know the package names of the things we need to have.  Perhaps an option like --create-current, or something along those lines?

Thanks.. this is nice.. I just need to figure out what I'm doing wrong here.  :-)

Bob

---

### Post by capink on 2007-07-23
Some Points:

1. Don't forget to add gdm to the install list, it is not in  my install list because I don't use it. I user mingetty to autologin. If you did not add gdm to the install list, try installing it from the console and see if that fixes your problems. To get to the command line press alt+ctrl+f1 and login

2. I added my install list as an example or as starting point. Some of the pacakages there are present on local repositories on my hard drive. this is why it cannot install audacious-plugins-extra on you system because the repositories in your sources.lst don't have this package. It is not important and you can remove it from your install list.

3. Adding the option for installed packages is easy. The problem is you will have to read through more than 1000 packages to decide what to keep and what to remove

4. If you typed the command 

```
script
```

before starting you should have a log on your home directory called typescript. Maybe we can examine that.

---

### Post by RTrev on 2007-07-23
> **capink said:**
> Some Points:

1. Don't forget to add gdm to the install list, it is not in  my install list because I don't use it. I user mingetty to autologin. If you did not add gdm to the install list, try installing it from the console and see if that fixes your problems. To get to the command line press alt+ctrl+f1 and login

2. I added my install list as an example or as starting point. Some of the pacakages there are present on local repositories on my hard drive. this is why it cannot install audacious-plugins-extra on you system because the repositories in your sources.lst don't have this package. It is not important and you can remove it from your install list.

3. Adding the option for installed packages is easy. The problem is you will have to read through more than 1000 packages to decide what to keep and what to remove

4. If you typed the command 

```
script
```

before starting you should have a log on your home directory called typescript. Maybe we can examine that.

Okay, thanks.. I'll try it again tonight and post the output of that script command.  And I see your point about listing all installed packages!  :-)  Maybe if other people try it, we can start sharing our lists and come up with some nice combinations.

---

### Post by Brian96 on 2007-07-23
So does the server install still contain a lot of packages that we don't want?

---

### Post by Brian96 on 2007-07-23
Bob, have you seen this discussion yet? [http://ubuntuforums.org/showthread.php?t=411664](http://ubuntuforums.org/showthread.php?t=411664)

Post #24 seems particularly relevant to our discussion.

I had not thought ahead about upgrading from our custom install. Apparently it is not straightforward. Of course, I don't really mind reinstalling, but it would be nice if that were not required.

---

### Post by Brian96 on 2007-07-23
> **Brian96 said:**
> I know what you mean about Windows. Although I have recently come across a couple of toys from M$ that I really like: There is an image-resizer toy that allows you to resize images (even multiple images at once) from a right-click menu on the image in a folder view. GREATLY simplifies shrinking images for e-mail. Then they have their sync-toy that synchronizes folders, and I've founded it a good bit easier to use than rsync. Oh, and then there is the toy that changes the ALT + TAB to thumbnail previews rather than just icons. (Didn't mean to hi-jack, but if anybody knows of Linux apps that will do these things, let me know.)

So, what command did you use to install Xfce?

Thought I would update this post.

There is an image-resizer utility for Gnome: nautilus-image-converter is the name of the package. I highly recommend it if you find yourself often resizing images (but nothing else). It also seems to support resizing multiple images at once.

Grsync is not significantly harder to use than the M$ synctoy. I'm still not sure what all the options are in rsync, but it is more a learning curve thing than anything else (the M$ descriptions of options were more intuitive; on the other hand M$ synctoy leaves an index file on the source and destination folder--annoying).

I have ALT + TAB thumbnail previews at work. I'm running Beryl over Xfce, so I can't remember if it is a function of Beryl or Xfce.

---

### Post by RTrev on 2007-07-24
> **Brian96 said:**
> Bob, have you seen this discussion yet? [http://ubuntuforums.org/showthread.php?t=411664](http://ubuntuforums.org/showthread.php?t=411664)

Post #24 seems particularly relevant to our discussion.

I had not thought ahead about upgrading from our custom install. Apparently it is not straightforward. Of course, I don't really mind reinstalling, but it would be nice if that were not required.

Hi Brian,

Got wrapped up in some other things for a while, and both VMware and VirtualBox are misbehaving for me.  Not sure why, as the host is rock-solid.  I'm accelerating my efforts to get my little test machine built so I can play with this stuff some more.

That thread is interesting.  I think the Ubuntu developers have heard the request and will probably address it when they can.  I suspect that you and I are atypical Ubuntu users.  The folks who really know Linux can build whatever system they want, and the ones who don't are probably content with having some extra packages installed.  We seem to be in a fairly small subset, and I suspect what we're looking for isn't super high on the developer's priority list.  :)

I have to run, but will be back in a bit.  Maybe I can either get that little box running today or figure out why the VMs are misbehaving.  ;-)

Bob

---

### Post by capink on 2007-07-24
> **RTrev said:**
> Okay, thanks.. I'll try it again tonight and post the output of that script command.  And I see your point about listing all installed packages!  :-)  Maybe if other people try it, we can start sharing our lists and come up with some nice combinations.

Here is a command to list all installed packages:

```
dpkg -l | grep '^.i' | awk '{print $2}'
```

---

### Post by RTrev on 2007-08-05
> **Brian96 said:**
> So does the server install still contain a lot of packages that we don't want?

Hi Brian.. I'm back.  :cool:

So many things came up at once that this had to be back-burnered for a while.

Not sure how long I can play with this, as we have a bunch of trips and whatnot coming up, but for now I've freed up one of my boot disks and started in again last night.

Are you  still happy with your Xfce/Beryl combination?

I've got just the server installed now, and will go through it first and see what it has that we don't need.  For one thing, I loads *all* of the video drivers for every oddball video card.. and I have no idea why because it should have the information it needs about which card we're running.  So all of that crud can go.  I'll see what else is there that could go.

I don't suppose you have the list of what you installed for the XFCE/Beryl combination?  Just xorg, XFCE4, compiz, beryl?  Maybe xdm or gdm or something for a graphical login as opposed to typing startx each login?  Any other critical parts to get started, beside synaptic and some apps?

A problem I'm having is that the lightweight window managers don't seem to be aware of or respect the dual-head Twinview setup.  They're always opening something right across  the center division of the two monitors.. which is too annoying to live with.  So maybe XFCE will be the lightest I can reasonably go until E is ready.

Tried something interesting the other day.. Vector Linux.  Supposed to be super fast, clean, minimalist.  Compared to my Gnome Ubuntu install, I found that 'buntu booted in 25 secs versus 30 for Vector, both used exactly 2.1G of disk, Vector could only see about 2 of my 4G (it's still in the 32-bit world), and nothing was noticeably faster.  After all, if you load Gimp, it's going to take x amount of time to be read from the disk, so any speedup is only seen in trivial things like it might take 1/4 second to open a terminal window where ubuntu would take 1/2 second.  Not meaningful.  So, for my use, plain old Ubuntu Gnome, stripped of the bloat, seems as good as anything I've tried.  But I do want to see the XFCE/Beryl combo before I decide to stay where I am.

I'm becoming more and more convinced that light-weight window and desktop managers are a great boon for old, slow machines, but for even a medium power machine like mine I see very little real-world benefit.  Others may find that not to be the case, but it's what keeps striking me.

Tks,
Bob

---

### Post by Brian96 on 2007-08-06
> **RTrev said:**
> Hi Brian.. I'm back.  :cool:

So many things came up at once that this had to be back-burnered for a while.

Not sure how long I can play with this, as we have a bunch of trips and whatnot coming up, but for now I've freed up one of my boot disks and started in again last night.

Are you  still happy with your Xfce/Beryl combination?

I've got just the server installed now, and will go through it first and see what it has that we don't need.  For one thing, I loads *all* of the video drivers for every oddball video card.. and I have no idea why because it should have the information it needs about which card we're running.  So all of that crud can go.  I'll see what else is there that could go.

I don't suppose you have the list of what you installed for the XFCE/Beryl combination?  Just xorg, XFCE4, compiz, beryl?  Maybe xdm or gdm or something for a graphical login as opposed to typing startx each login?  Any other critical parts to get started, beside synaptic and some apps?

A problem I'm having is that the lightweight window managers don't seem to be aware of or respect the dual-head Twinview setup.  They're always opening something right across  the center division of the two monitors.. which is too annoying to live with.  So maybe XFCE will be the lightest I can reasonably go until E is ready.

Tried something interesting the other day.. Vector Linux.  Supposed to be super fast, clean, minimalist.  Compared to my Gnome Ubuntu install, I found that 'buntu booted in 25 secs versus 30 for Vector, both used exactly 2.1G of disk, Vector could only see about 2 of my 4G (it's still in the 32-bit world), and nothing was noticeably faster.  After all, if you load Gimp, it's going to take x amount of time to be read from the disk, so any speedup is only seen in trivial things like it might take 1/4 second to open a terminal window where ubuntu would take 1/2 second.  Not meaningful.  So, for my use, plain old Ubuntu Gnome, stripped of the bloat, seems as good as anything I've tried.  But I do want to see the XFCE/Beryl combo before I decide to stay where I am.

I'm becoming more and more convinced that light-weight window and desktop managers are a great boon for old, slow machines, but for even a medium power machine like mine I see very little real-world benefit.  Others may find that not to be the case, but it's what keeps striking me.

Tks,
Bob

Have you tried Beryl or Compiz Fusion with Gnome?

I had Xfce installed first, so it just happened to be there when I installed Beryl and then Compiz Fusion.

I am now using Compiz Fusion at home as well. I did lose some functionality because of my ATI graphics card, but it does look nice.

There are two basic ways to do the Beryl/Compiz thing. One is to install Beryl and the Beryl settings manager (can't remember if those are the actual package names) with apt-get or Synaptic. Beryl is the stable version. The other version is a Beryl/Compiz joint effort called Compiz Fusion. It is not stable, but there are howtos on here to tell you how to install it.

So far I like the Ubuntu server install with either Gnome or Xfce as well. Like you said, it removes some of the worst bloat, and the gains are minimal to pare down much more, at least with a decent system. I think I've more or less decided on Gnome for now. At home I like my panel, so getting the right-click menu has become less important. At work, where I only run a couple of apps at a time, the clean interface is fine.

I may yet try a Debian server install. I downloaded Debian-Edu to see if it would be suitable as a distro for my preschooler (it wasn't) and it has WAY more bloat than Ubuntu. But I want to try Debian server at some point. I guess the main difference will be  the repositories.

---

### Post by RTrev on 2007-08-06
> **Brian96 said:**
> Have you tried Beryl or Compiz Fusion with Gnome?

Yep, tried it with both.  Under PCLinuxOS/TR4 it worked without a hitch.  Under a previous Feisty Gnome install I had problems.. the window borders disappeared so that a window couldn't be moved, and I got no special effects.  But I later tried it again and it worked fine.  I have no idea what the issue was then, but I have the same thing with XFCE now.

> 
I had Xfce installed first, so it just happened to be there when I installed Beryl and then Compiz Fusion.


Maybe that's the issue.. I had thought the two had merged into one.  I just did an install of Beryl, because the description of the package said it would pull in the compositing stuff..

> 
So far I like the Ubuntu server install with either Gnome or Xfce as well. Like you said, it removes some of the worst bloat, and the gains are minimal to pare down much more, at least with a decent system. I think I've more or less decided on Gnome for now. At home I like my panel, so getting the right-click menu has become less important. At work, where I only run a couple of apps at a time, the clean interface is fine.


I seem to keep "coming home" to Gnome too.  I'll try something that seems fast and clean, and then time the same thing in my normal Gnome install and it's either the same of slightly faster in Gnome.  Maybe it's because it's where I started, but I just feel most comfortable in Gnome.

> 
I may yet try a Debian server install. I downloaded Debian-Edu to see if it would be suitable as a distro for my preschooler (it wasn't) and it has WAY more bloat than Ubuntu. But I want to try Debian server at some point. I guess the main difference will be  the repositories.

I tried Sid, a while back, because someone told me they were getting the best video from it they'd ever had.  It didn't work out.  I can't recall exactly why, but I had no luck getting Twinview working, which is a showstopper for me, and then I ran into IceWeasel and started laughing and deleted the whole mess.  ;)

I think I've largely gotten it out of my system now.  I'll stick with Ubuntu, with Gnome, and strip out the stuff I don't want.  I ran into a problem with the server install routine yesterday that was a bit puzzling.  I never had this happen before.  I have my "daily driver" install on sda, and wanted to play on sdb.  So I created a swap and a root on sdb, and then told the installer I was done partitioning.  No matter what I did, it told me it was going to use the two I'd just created but was also going to use the swap from sda.  I let it, as I saw no harm in it, but I couldn't get it to stay away from sda.  I'm now inclined to use the alternate, and put up with the updating after the install.

Of course all of this may change drastically in a couple weeks, if Gutsy is still on schedule.  :rolleyes:

---

### Post by RTrev on 2007-08-07
p.s.  Have you googled for Fluxbuntu?  Looks like it may come out with Gutsy or thereafter if I'm understanding correctly.  

[http://fluxbuntu.org/en/node/36](http://fluxbuntu.org/en/node/36)

---

### Post by Brian96 on 2007-08-07
> **RTrev said:**
> p.s.  Have you googled for Fluxbuntu?  Looks like it may come out with Gutsy or thereafter if I'm understanding correctly.  

[http://fluxbuntu.org/en/node/36](http://fluxbuntu.org/en/node/36)

I looked into it a while ago, but I wasn't real thrilled with fluxbox. Sure, it is lean and mean, but to really configure it you need to use the CLI (and I'm definitely a GUI person). I think I'll stick with Gnome for a while (especially until I find an alternative to the nautilus-image-converter, that's a great tool if you upload a lot of digital images to send to people).

---

### Post by Brunellus on 2007-08-07
The alternate CD has a "Command-line only" option.  That installs only the core ubuntu packages:  no Xserver, no nothing, no kidding.

From that point forward it should be pretty easy to customize your install one package at a time.  

also, please consult this wiki page:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Brian96 on 2007-08-09
> **Brunellus said:**
> The alternate CD has a "Command-line only" option.  That installs only the core ubuntu packages:  no Xserver, no nothing, no kidding.

From that point forward it should be pretty easy to customize your install one package at a time.  

also, please consult this wiki page:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

How is that installation different from the "server" install on the mini.iso?

---

### Post by Brunellus on 2007-08-09
> **Brian96 said:**
> How is that installation different from the "server" install on the mini.iso?
"command-line only" comes with no services or daemons running

---

### Post by Brian96 on 2007-08-09
> **Brunellus said:**
> "command-line only" comes with no services or daemons running

Interesting. Do you know if that option is available through the mini.iso? One thing I like about doing the server install from mini.iso is that it downloads the latest versions of apps from the repos, so there is no updating or upgrading needed when you first boot up. But from what you are saying it sounds like the CLI-only option may be even slightly more streamlined than the server install.

If the services and daemons are not running, does that mean they are also not installed?

---

### Post by Brunellus on 2007-08-10
> **Brian96 said:**
> Interesting. Do you know if that option is available through the mini.iso? One thing I like about doing the server install from mini.iso is that it downloads the latest versions of apps from the repos, so there is no updating or upgrading needed when you first boot up. But from what you are saying it sounds like the CLI-only option may be even slightly more streamlined than the server install.

If the services and daemons are not running, does that mean they are also not installed?
I don't believe so.  "command-line only" installs only the ubuntu-base metapackage, as I recall.

---

### Post by sourjax on 2007-08-18
I think what we need is a minimal Live CD/installer. A Live CD that has only enough to boot and run a command line. No Gnome, Firefox, OpenOffice.org, Nautilus, etc. That way we can build whatever we want on top of that. I've tried re-mastering the Ubuntu Live CD to get this, but when I start removing packages the Live CD doesn't work at all.

---

### Post by RTrev on 2007-08-18
> **sourjax said:**
> I think what we need is a minimal Live CD/installer. A Live CD that has only enough to boot and run a command line. No Gnome, Firefox, OpenOffice.org, Nautilus, etc. That way we can build whatever we want on top of that. I've tried re-mastering the Ubuntu Live CD to get this, but when I start removing packages the Live CD doesn't work at all.

How would your live installer differ from the Mini CD or the command line install of the Alternate CD?  Do you mean something that would let you say yes or no to each package?

I have an old Pentium 2 here which didn't have the resources to run the Live CD, so I just installed the Mini CD, and then added what i wanted on this box.

I wanted to try a light version of Gnome, so I issued these two commands:

sudo aptitude update
sudo aptitude install xorg gdm synaptic firefox pan gftp

I ended up with an Ubuntu that's running in 96M of RAM.  I could have gone for a lot lighter desktop, but this works for what I want at the moment.

Regards,
Bob

---

### Post by sourjax on 2007-08-18
It would boot *directly* into the Command Line instead of the boot prompt. the Mini.iso takes way too long to install. Neither the mini.iso or the alternate are really live CD's. You have to install them **before** you can use them at all.

Maybe, this would allow you to test the different package combinations before having to install it to you HDD.

I'd build the Live CD I'm wanting , but I don't know what packages I can and cannot remove without breaking it.

---

### Post by RTrev on 2007-08-18
> **sourjax said:**
> It would boot *directly* into the Command Line instead of the boot prompt. the Mini.iso takes way too long to install. Neither the mini.iso or the alternate are really live CD's. You have to install them **before** you can use them at all.

Maybe, this would allow you to test the different package combinations before having to install it to you HDD.

I'd build the Live CD I'm wanting , but I don't know what packages I can and cannot remove without breaking it.

Oh, I get you.  You want a live CD but with a lot more options about what does and doesn't start running once the GUI display is up and running.  In other words, it might ask if you need Open Office, if you want the CUPS printer support, if you need the Bluetooth stuff, and so on.

Am I understanding you correctly?

I've never heard of any such thing, but I keep asking for it.  I think it would be super to be allowed to not install a whole bunch of stuff that comes by default.  I usually run the alpha and beta of Ubuntu systems, and I can't tell you how many times I've groaned because I see yet another version of Open Office being downloaded.. using both Ubuntu's bandwidth and my bandwidth, and I don't *want* the package.  :)  I leave it until the final release of the version, just so I can test it as they intend it to be, but then I remove it immediately.  ;-)

All I can suggest is that you convey this desire to the developers, and we'll all hope they come up with a way to do precision installs rather than shotgun ones.  :-)

---

### Post by sourjax on 2007-08-18
> **RTrev said:**
> Oh, I get you.  You want a live CD but with a lot more options about what does and doesn't start running once the GUI display is up and running.  In other words, it might ask if you need Open Office, if you want the CUPS printer support, if you need the Bluetooth stuff, and so on.

Am I understanding you correctly?

I've never heard of any such thing, but I keep asking for it.  I think it would be super to be allowed to not install a whole bunch of stuff that comes by default.  I usually run the alpha and beta of Ubuntu systems, and I can't tell you how many times I've groaned because I see yet another version of Open Office being downloaded.. using both Ubuntu's bandwidth and my bandwidth, and I don't *want* the package.  :)  I leave it until the final release of the version, just so I can test it as they intend it to be, but then I remove it immediately.  ;-)

All I can suggest is that you convey this desire to the developers, and we'll all hope they come up with a way to do precision installs rather than shotgun ones.  :-)

Sorta, I've been playing w/ the Knoppix Live CD, mainly because I love the idea behind Damn Small Linux, and would love "Dang Small Ubuntu". Knoppix has boot options that allows me to boot into DE's other than KDE (e.g. I can boot into Fluxbox instead) it would be nice to be able to do that with Ubuntu and after you get done customizing everything you want, then install it to your PC. If only I could get a list of non-essential packages, I would at least attempt to build a Mini Live CD that would fit our needs, but as I said in an earlier post every time I start removing packages such as gnome or evolution the Live CD stop working. I would love to remove gnome, evolution, etc from the Live CD and use Fluxbox, IceWM, or whatever and have only my specific choice packages instead the current default, that way I don't have to go through the long and tedious install process I go through now.

BTW: Do you like the idea of Konqueror being a File/Web browser? It's almost got me hooked, if only FireFox was the same way.

---

### Post by RTrev on 2007-08-18
> **sourjax said:**
> Sorta, I've been playing w/ the Knoppix Live CD, mainly because I love the idea behind Damn Small Linux, and would love "Dang Small Ubuntu". Knoppix has boot options that allows me to boot into DE's other than KDE (e.g. I can boot into Fluxbox instead) it would be nice to be able to do that with Ubuntu and after you get done customizing everything you want, then install it to your PC. If only I could get a list of non-essential packages, I would at least attempt to build a Mini Live CD that would fit our needs, but as I said in an earlier post every time I start removing packages such as gnome or evolution the Live CD stop working. I would love to remove gnome, evolution, etc from the Live CD and use Fluxbox, IceWM, or whatever and have only my specific choice packages instead the current default, that way I don't have to go through the long and tedious install process I go through now.

I think at the moment the best you can do is probably to pick up a hard disk for $2 at a flea market, run SpinRite on it, and then plug that in when you want to experiment.  I've got an old Pentium 2 sitting beside me that was free.  I wouldn't hold your breath for a live CD as you're hoping for, but it would be nice.  OTOH, install to the hard drive and then play.  Two ways.. start with full install and trim stuff away, or start with command line install and carefully add things one at a time.

> BTW: Do you like the idea of Konqueror being a File/Web browser? It's almost got me hooked, if only FireFox was the same way.

I don't like KDE period.  Can't really put my finger on why.  Seems slow, seems buggy, seems like Windows.  ;-)

And Konqueror strikes me as a bad idea, the same way Windows Explorer and Internet Explorer being joined at the hip seems a bad idea.  I'd much rather have one small, tight, fast program, which is good at what it does.  And then another for some other job.  But what do I know?  Linus Torvalds likes KDE.  Which of us are you going to listen to?  ;-)

Oh, and Google for "Fluxbuntu".  Seems to be a project that might be coming along at some point relatively soon.

---

### Post by sourjax on 2007-08-18
My thing is I don't like going through the same long drawn out installation process just to get what I want. So I'd like to make my own Ubuntu based distro/derivative so that I don't have to go through that long drawn out process.

I also hate KDE as well, but I love the idea behind Konqueror. Konqueror as a web browser sucks but I like the ability to surf the web or my files with one App. Gnome is nice but it's just too big for my older PC, the one I'm using now I bought back in Feb and it works great but my other PC drags with 384 MB RAM. I'm like you I want a super clean Ubuntu with only the apps I need and not all the other junk that comes with all the distros out there, DSL is supposed to be a minimal distro but even it has things I don't need or want.

---

### Post by RTrev on 2007-08-18
> **sourjax said:**
> My thing is I don't like going through the same long drawn out installation process just to get what I want. So I'd like to make my own Ubuntu based distro/derivative so that I don't have to go through that long drawn out process.

I also hate KDE as well, but I love the idea behind Konqueror. Konqueror as a web browser sucks but I like the ability to surf the web or my files with one App. Gnome is nice but it's just too big for my older PC, the one I'm using now I bought back in Feb and it works great but my other PC drags with 384 MB RAM. I'm like you I want a super clean Ubuntu with only the apps I need and not all the other junk that comes with all the distros out there, DSL is supposed to be a minimal distro but even it has things I don't need or want.

Have you played with Virtual Machines at all?  It's an interesting way to do a "real" install, but still be able to have complete control over things.  For example, install the mini CD into a VM, take a snapshot so that you can always get back to that point to start over, and then play.  

I like to do things like that, or just plug in a small disk to play with for a while.  Eventually you'll find just the combination that works for you, and then you can just jot down the names of the packages you installed and use it for future installs.

Also, if you look back up the thread a little ways, there is that little script which allows you to just create a file of which packages you want installed.  Sorry, I forgot the chap's name. I had trouble with it, but it was probably my own fault.  :)

I figure that Ubuntu will continue to evolve, and it will eventually make it easier for people to pick and choose packages.  In the meantime, I've decided to just use the default Ubuntu as it comes, because it works fine for me.  And I'll look forward to them trimming the fat from it at some point with a more intelligent installer, etc.  I don't mind living on the bleeding edge, so I'm running 7.10 as my main daily driver, and have the 32-bit install of 7.04 on another disk to fall back on if needed.  So far I'm finding no show-stoppers, and just a handful of things that are a little weird.  It's fun to watch what the developers come up with, so I like a front-row seat.  :)  It will just keep getting better, and it's fine as it is.  Yeah, I'd like to be rid of some junk I don't need, but I've stopped fighting it for now.  :)

---

### Post by sourjax on 2007-08-18
> **RTrev said:**
> Have you played with Virtual Machines at all?  It's an interesting way to do a "real" install, but still be able to have complete control over things.  For example, install the mini CD into a VM, take a snapshot so that you can always get back to that point to start over, and then play.  


I have VirtualBox installed and use it to test my combinations, I haven't used it long so I didn't know how the snapshot feature worked. I'll have to keep that in mind.

> **RTrev said:**
> 
I like to do things like that, or just plug in a small disk to play with for a while.  Eventually you'll find just the combination that works for you, and then you can just jot down the names of the packages you installed and use it for future installs.

Also, if you look back up the thread a little ways, there is that little script which allows you to just create a file of which packages you want installed.  Sorry, I forgot the chap's name. I had trouble with it, but it was probably my own fault.  :)


I'll have to look for that script.

> **RTrev said:**
> 
I figure that Ubuntu will continue to evolve, and it will eventually make it easier for people to pick and choose packages.  In the meantime, I've decided to just use the default Ubuntu as it comes, because it works fine for me.  And I'll look forward to them trimming the fat from it at some point with a more intelligent installer, etc.  I don't mind living on the bleeding edge, so I'm running 7.10 as my main daily driver, and have the 32-bit install of 7.04 on another disk to fall back on if needed.  So far I'm finding no show-stoppers, and just a handful of things that are a little weird.  It's fun to watch what the developers come up with, so I like a front-row seat.  :)  It will just keep getting better, and it's fine as it is.  Yeah, I'd like to be rid of some junk I don't need, but I've stopped fighting it for now.  :)

I may try running 7.10 somewhere to get a feel for what direction Ubuntu is going. I really wish I could help develop and give back to the community but it all over my head right now.

---

### Post by RTrev on 2007-08-18
> **sourjax said:**
> I really wish I could help develop and give back to the community but it all over my head right now.

We'll get there.  The first step is probably just getting involved in helping to track bugs.  I think by the time this cut is released I'll be comfortable enough to begin finding places where I can help out some.

Remember, you don't have to be a programmer to help out.  You just have to find a niche where you feel comfortable and where you feel like you can make a difference.  It may be a little late in the Gutsy development cycle, but I think I'm going to try to jump in somewhere soon.

---

### Post by Brian96 on 2007-09-06
Well, I've been doing a little bit of distro-hopping. I tried PCLinuxOS, which I really like, and Damn Small Linux. I didn't really give DSL a fair shake because I was having trouble with my VM, but I found something interesting in PCLOS.

Someone over there is working on a distro he calls TinyMe, based on PCLOS. It is a minimal PCLOS, and it installed on my harddrive with a full GUI (using openbox as the WM) and virtually no superfluous stuff (no bluetooth, palm, etc garbage running) at about 800 MB. I installed Gnome (which I prefer) on top of it and it was still barely 1 GB. If PCLOS's repos were better this might be the way to go.

Next I may try DSL or another small, Debian-based system.

How big is just a CLI/Server install of Ubuntu? I'd like to make some comparisons.

As has been discussed on other threads, one thing I really like about PCLOS is their control center. I did not have to go to the command line once to do all the configuration I needed. It was wonderful. Also, although they use RPMs for packaging, they use Synaptic and APT as the front-end, so I didn't have to learn a new system.

Anyway, just thought this may give us some more food for thought.

---

### Post by graigsmith on 2007-09-06
personally i would just leave all the stuff you dont want installed,  just hide it in the menu with the menu editor.  i mean, it doesn't take up much memory.

---

### Post by Brian96 on 2007-09-06
> **graigsmith said:**
> personally i would just leave all the stuff you dont want installed,  just hide it in the menu with the menu editor.  i mean, it doesn't take up much memory.

Tried that, and in fact, all of the solutions we have found so far demand a little of that. However, there are still processes running in a full install that are a waste of resources for many of us.

As has been pointed out earlier in the thread, we are kind of caught in a "no man's land." We know enough about Linux to know that there are a lot of scalability options. But we either lack the time or the expertise (or both) to just build our own distro from scratch. And for the most part we like the stability and support of Ubuntu (or at least Debian), so we don't want to wander too far afield. But the full Ubuntu, and to a lesser extent even a server install, still dumps more on our computers than we really want.

---

### Post by ron999 on 2007-09-06
Brian96 and RTrev etc
I've been following this thread on and off for a few weeks now, it's interesting.
There's a lnk here, forgive me if you've already covered it.
What do you think of this here:- [http://www.psychocats.net/ubuntu/minimal#standard]("http://www.psychocats.net/ubuntu/minimal#standard")
Edit. I refer to the 'Barebones Installation'

---

### Post by Brian96 on 2007-09-06
> **ron999 said:**
> Brian96 and RTrev etc
I've been following this thread on and off for a few weeks now, it's interesting.
There's a lnk here, forgive me if you've already covered it.
What do you think of this here:- [http://www.psychocats.net/ubuntu/minimal#standard]("http://www.psychocats.net/ubuntu/minimal#standard")
Edit. I refer to the 'Barebones Installation'

Variations of what psychocats has described there is essentially what we've come to as the simplest way to get a barebones install out of Ubuntu. Most of the variations come into play in determining what packages to add to the CLI base.

Interestingly, the install seems to be even easier than he described there, as I did not edit my sources list but had no trouble installing everything I needed. The other point of variation is whether to use the mini.iso or alternative CD. Mini.iso installs ALL packages from the internet, so you end up with the most recent packages right off the bat, BUT this method depends on your internet connection speed.

Thanks for your interest.

---

### Post by RTrev on 2007-10-28
Seems that things have changed with Gutsy.  I install xorg, gdm, gnome-core, etc., but the windows can't be moved, have no border, no way to close them except File | Quit.  Anybody have any suggestions about what package I'm missing?

---

### Post by RTrev on 2007-10-29
> **RTrev said:**
> Seems that things have changed with Gutsy.  I install xorg, gdm, gnome-core, etc., but the windows can't be moved, have no border, no way to close them except File | Quit.  Anybody have any suggestions about what package I'm missing?

Ah, I see one has to install compiz to make everything work.  It's set to NO effects, but it needs to be there as it's apparently handling all window activity.  Everything works fine now.

---

### Post by richardjennings on 2007-11-19
I haven't read the whole thread because I'm looking for something else, noticed this and maybe my two cents might be usefull.

I started working on an Ubuntu install which I am designing to fit the characteristics of the Eee pc

So my first job was a minimal install. I used dapper drake.

Here's what I did.

1) Install Dapper Drake Server without LAMP
2) boot into shell
3) edit sources.list to enable all repositories 
4) apt-get everything else I wanted:

xserver-xorg-core, gdm, gnome-core

gnome-core needs multiverse? I think. A repository that is disabled by default anyhow.

You then have a very bare but working gnome install at around 900mb


Notice no mention of ubuntu-desktop!

And there you have it, a very bare but low memory small install.


First thing I did after that was install synaptic :)

hope that is of use to someone at somepoint.

---

### Post by RTrev on 2007-11-19
> **richardjennings said:**
> I haven't read the whole thread because I'm looking for something else, noticed this and maybe my two cents might be usefull.

I started working on an Ubuntu install which I am designing to fit the characteristics of the Eee pc

So my first job was a minimal install. I used dapper drake.

Here's what I did.

1) Install Dapper Drake Server without LAMP
2) boot into shell
3) edit sources.list to enable all repositories 
4) apt-get everything else I wanted:

xserver-xorg-core, gdm, gnome-core

gnome-core needs multiverse? I think. A repository that is disabled by default anyhow.

You then have a very bare but working gnome install at around 900mb


Notice no mention of ubuntu-desktop!

And there you have it, a very bare but low memory small install.


First thing I did after that was install synaptic :)

hope that is of use to someone at somepoint.

Thanks.  That's pretty much what I do for a minimal install these days too.  I use Gutsy, though.  Still distro-hopping, since I haven't found the ideal yet.  Fiesty was broken in a lot of ways, and now Gutsy is broken in other ways.. maybe I'll do what you did and go back a few revisions.  Thanks for the ideas!

---

### Post by Brian96 on 2007-11-21
> **RTrev said:**
> Ah, I see one has to install compiz to make everything work.  It's set to NO effects, but it needs to be there as it's apparently handling all window activity.  Everything works fine now.

I'm having trouble with Gutsy as well. My problem, though, is that I can't get past the "Running local boot scripts" line of startup. I get hung up there just with the base install, as well, but it didn't matter because I could just hit enter to log in and install other packages. But it is a problem now that I've installed other packages and want to get into a GUI.

I've done this with a server install off of the Alternate CD and off of the Mini CD. If I do a regular install with either disk I have no trouble, just the server install.

I have also tried it after installing the "xorg gnome-core gdm" packages and the "xorg xfce4 gdm" packages off of clean server installs. Any suggestions?

---

### Post by Brian96 on 2007-11-21
> **Brian96 said:**
> I'm having trouble with Gutsy as well. My problem, though, is that I can't get past the "Running local boot scripts" line of startup. I get hung up there just with the base install, as well, but it didn't matter because I could just hit enter to log in and install other packages. But it is a problem now that I've installed other packages and want to get into a GUI.

I've done this with a server install off of the Alternate CD and off of the Mini CD. If I do a regular install with either disk I have no trouble, just the server install.

I have also tried it after installing the "xorg gnome-core gdm" packages and the "xorg xfce4 gdm" packages off of clean server installs. Any suggestions?

Okay, I got it working by first installing xserver-xorg-core, then manually installing xfonts-base and discover1. This solved the font error message and helped the xserver autodetect my video card so I got the right drivers. Then I ran startx and got x running, so I went back and installed gnome-core and gdm. It is still a little buggy, but I can at least get into the GUI.

---

### Post by RTrev on 2007-11-21
> **Brian96 said:**
> Okay, I got it working by first installing xserver-xorg-core, then manually installing xfonts-base and discover1. This solved the font error message and helped the xserver autodetect my video card so I got the right drivers. Then I ran startx and got x running, so I went back and installed gnome-core and gdm. It is still a little buggy, but I can at least get into the GUI.

I was scratching my head over this one.  I haven't had it do that.. ever.  And, I thought xserver-xorg-core was history.  Guess not.

Glad you got it working.  BTW, you don't find you need to install compiz before your window borders show up and the desktop is manageable?  I haven't gotten a bare-Bones Gutsy install to work yet, without it.

Bob

---

### Post by Brian96 on 2007-11-21
> **RTrev said:**
> I was scratching my head over this one.  I haven't had it do that.. ever.  And, I thought xserver-xorg-core was history.  Guess not.

Glad you got it working.  BTW, you don't find you need to install compiz before your window borders show up and the desktop is manageable?  I haven't gotten a bare-Bones Gutsy install to work yet, without it.

Bob

There 3 main xserver packages that I have found: xorg (biggest) xserver-xorg (slightly smaller) and xserver-xorg-core (smallest). Not sure of the relative merits of each, but I couldn't get it working with just xorg, but I did with xserver-xorg-core plus the two packages I mentioned.

As for compiz, I can't figure it out. I did have to install compiz to get borders, but on my laptop (which runs a full Ubuntu install and also can't handle compiz) I have uninstalled ALL compiz packages and still have borders, even after a reboot. I'm not sure what the deal is with that.

However, I would like to get compiz working on this other machine, which is why I went ahead and installed it. I did a test install of full Ubuntu before playing with the minimal install, and compiz worked then, but doesn't work now. Not sure what I'm missing.

---

### Post by RTrev on 2007-11-21
> **Brian96 said:**
> There 3 main xserver packages that I have found: xorg (biggest) xserver-xorg (slightly smaller) and xserver-xorg-core (smallest). Not sure of the relative merits of each, but I couldn't get it working with just xorg, but I did with xserver-xorg-core plus the two packages I mentioned.

As for compiz, I can't figure it out. I did have to install compiz to get borders, but on my laptop (which runs a full Ubuntu install and also can't handle compiz) I have uninstalled ALL compiz packages and still have borders, even after a reboot. I'm not sure what the deal is with that.

However, I would like to get compiz working on this other machine, which is why I went ahead and installed it. I did a test install of full Ubuntu before playing with the minimal install, and compiz worked then, but doesn't work now. Not sure what I'm missing.

I didn't know about the three xorg packages.. thanks!  That will something interesting to play with.

I had the same experience.. removed compiz entirely from a full install, and things kept working fine (almost.. see below).  In the minimal installs, Metacity was there, and I'm told that Metacity takes over when compiz is turned off.  :confused:

I did, however, note that some odd things happened on my full install when compiz was deleted.  For example, I lost the ability to customize my panel (I only use a top panel in Gnome.)  I was no longer able to choose a solid color and then make it partially opaque.  But I could live with that.  I didn't see any improvements, however, so reinstalled it and just left it turned off (no effects.)

I'm about to try it again, so will have to think about which options to pick this time.  I'll try your minimal xorg package, for one thing.

Wouldn't it be great if there were an Ubuntu install CD/DVD which would ask questions about applications?  Do you need laptop support?  Do you want a mail client, and if so which one?  Do you want OpenOffice, Abiword, or neither?  Do you need language support and fonts beyond just English?  Do you want the games?  Do you need Samba?  And on and on.  When we got done, it would figure out the dependencies and install the system we want.

Why they haven't done this mystifies me.  Kind of like the way it mystifies me that it detects the video card correctly, but then proceeds to install the drivers for every card ever made.  And after that, I *still* have to go and get the driver I *really* need.  It's these silly things that are irritating, and that we've been struggling to overcome throughout this entire thread.

---

### Post by Brian96 on 2007-11-21
> **RTrev said:**
> I didn't know about the three xorg packages.. thanks!  That will something interesting to play with.

I had the same experience.. removed compiz entirely from a full install, and things kept working fine (almost.. see below).  In the minimal installs, Metacity was there, and I'm told that Metacity takes over when compiz is turned off.  :confused:

I did, however, note that some odd things happened on my full install when compiz was deleted.  For example, I lost the ability to customize my panel (I only use a top panel in Gnome.)  I was no longer able to choose a solid color and then make it partially opaque.  But I could live with that.  I didn't see any improvements, however, so reinstalled it and just left it turned off (no effects.)

I'm about to try it again, so will have to think about which options to pick this time.  I'll try your minimal xorg package, for one thing.

Wouldn't it be great if there were an Ubuntu install CD/DVD which would ask questions about applications?  Do you need laptop support?  Do you want a mail client, and if so which one?  Do you want OpenOffice, Abiword, or neither?  Do you need language support and fonts beyond just English?  Do you want the games?  Do you need Samba?  And on and on.  When we got done, it would figure out the dependencies and install the system we want.

Why they haven't done this mystifies me.  Kind of like the way it mystifies me that it detects the video card correctly, but then proceeds to install the drivers for every card ever made.  And after that, I *still* have to go and get the driver I *really* need.  It's these silly things that are irritating, and that we've been struggling to overcome throughout this entire thread.

I started a new thread to find out why Compiz won't work for me on my minimal install. Based on your experience it sounds like I may end up having to reinstall compiz on my laptop. I haven't gotten around to playing with panels yet.

If you use the xserver-xorg-core package, be sure to add xfonts-base to it (or at least I had to; I guess you could wait and see what happens, if you get a "fonts" error when trying to startx then that package may work for you; it also was easier to configure the xserver with discover1 installed). Unfortunately the xserver-xorg-core package STILL install ALL the video drivers. I imagine they are miniscule packages anyway, but it does boggle the mind.

I can see your point about a step-by-step install, but I think I would grow impatient with one and still use this method. This way is buggy, but it is pretty darn minimal! I'm not sure, but I feel like gnome-core in Gutsy is even slightly more minimal than in Feisty. Could be my imagination, though.

Funny thing is that I thought I was done with minimal installs and was going to stick to full installs. Then I installed and saw all the garbage I didn't want--and realized that there were STILL a lot of packages I wanted to ADD that weren't included--so I went back to the minimal install. :KS

---

### Post by RTrev on 2007-11-21
> **Brian96 said:**
> 
Funny thing is that I thought I was done with minimal installs and was going to stick to full installs. Then I installed and saw all the garbage I didn't want--and realized that there were STILL a lot of packages I wanted to ADD that weren't included--so I went back to the minimal install. :KS

I thought I was done too, but now have a bunch of antique P2 128M machines to set up with *something* and so am back at it again.  

Tried Fluxbuntu, but it's the slowest distro I've ever seen.  It takes ages to install, ages to boot, and then gives me a black screen until I reconfigure things..  and then it's still unusable.

Tried DSL, PCFlucboxOS, Antix, Vector.. all have problems with these boxes.  So, I'm back at it again.  And I'll probably do another minimal Gnome for my mail machine.  Have you tried the boot option of cli-expert?  I didn't yet, except to explore it, because I'm not sure the chipsets on these old boxes, but may try that for my regular machine.  It gives quite precise control as far as I took it..

---

### Post by RTrev on 2007-11-22
Just a quick update, Brian.  I installed the xserver-xorg-core and xfce4.  Configured xorg, and it ran like a charm.  Had to add a few apps of course, like the appfinder, but it works just fine with only those two installs.  Of course you log in at the command line and then type startx, but that's no big deal.  For a light and quick install, this isn't bad!

Bob

---

### Post by anticapitalista on 2007-11-22
> **RTrev said:**
> 

Tried DSL, PCFlucboxOS, Antix, Vector.. all have problems with these boxes. 

Care to let me know what the problem with antiX was? So I can keep it for reference.

TIA

---

### Post by capink on 2007-11-22
> **RTrev said:**
> Of course you log in at the command line and then type startx, but that's no big deal.  For a light and quick install, this isn't bad!

Bob


You can automate this by installing mingetty and using it to autologin as follows:

1. Install mingetty

```
sudo apt-get install mingetty
```

2. Make mingetty handle automatic login by editing the file  /etc/event.d/tty1

```
sudo gedit /etc/event.d/tty1
```

Note: Replace gedit with your favorite editor

3. Replace the following line:

```
exec /sbin/getty 38400 tty1
```

With

```
exec /sbin/mingetty --autologin [COLOR="Red"]username[/COLOR] tty1
```

[COLOR="Red"]Note: Replace username with appropriate name[/COLOR]

The previous three steps will take care of autologging.

To start x automatically, append the following line to you ~/.profile :

```
startx -- :1
```

Note: Sometimes the file is called .bash_profile depending on the Ubuntu version you are running.

---

### Post by RTrev on 2007-11-22
> **anticapitalista said:**
> Care to let me know what the problem with antiX was? So I can keep it for reference.

TIA

Well, the problem with all of the lightweight Flux distros I've tried must stem from something weird on this hardware; they all come up thinking they should be running at 1280xwhatever rather than the 1024x768 which is the max this monitor can handle.

Consequently, they all boot me into a black screen.  This can usually be fixed by just adjusting xorg, but on Antix, for some reason, I could never get *out* of the black screen so that I could fix it.  The others would allow some key combination to take me to a terminal where I could work, but Antix either has no such key combination, or was too hosed by that point to respond, or something.

If the distro will at least let you work in it you can probably try it out.. but I never found a way to get anywhere with Antix.

Fluxbuntu did the same thing, but then I could at least get to a terminal to (sort of) fix it.  Once I had it running, however, the *applications* themselves still thought they were at the higher resolution.  Not sure how to fix that.  And is was S L O W.  I never saw anything boot as slowly as Fluxbuntu.  My xfce will boot in 1/3 the time of Fluxbuntu.. no idea if other people have that problem.

Hope that helps.

Bob

---

### Post by anjilslaire on 2007-11-22
Sorry for not reading the entire thread, but you can install the server version (no gui), then just 
sudo apt-get install gnome

This wil give you the basic gnome GUI without all the extra fluff that comes with gnome-desktop like open office, etc.

Of course, insert kde/xfce/enlightenment/desktop of choice if desired.

---

### Post by RTrev on 2007-11-22
> **anjilslaire said:**
> Sorry for not reading the entire thread, but you can install the server version (no gui), then just 
sudo apt-get install gnome

This wil give you the basic gnome GUI without all the extra fluff that comes with gnome-desktop like open office, etc.

Of course, insert kde/xfce/enlightenment/desktop of choice if desired.

Yes, we do that a lot.. I usually choose gnome-core for the basis of those installs.  Thanks..

---

### Post by RTrev on 2007-11-22
> **capink said:**
> You can automate this by installing mingetty and using it to autologin as follows:

1. Install mingetty

```
sudo apt-get install mingetty
```

2. Make mingetty handle automatic login by editing the file  /etc/event.d/tty1

```
sudo gedit /etc/event.d/tty1
```

Note: Replace gedit with your favorite editor

3. Replace the following line:

```
exec /sbin/getty 38400 tty1
```

With

```
exec /sbin/mingetty --autologin [COLOR="Red"]username[/COLOR] tty1
```

[COLOR="Red"]Note: Replace username with appropriate name[/COLOR]

The previous three steps will take care of autologging.

To start x automatically, append the following line to you ~/.profile :

```
startx -- :1
```

Note: Sometimes the file is called .bash_profile depending on the Ubuntu version you are running.

Hey, thanks!  I don't like auto-logins, but an auto-start of X which then prompted for the credentials to log in would be good.  I didn't think that was possible without loading GDM or something like that.

Bob

---

### Post by capink on 2007-11-22
just use the last step and x will start automatically after you login. But you will still have to login at the terminal.

---

### Post by anticapitalista on 2007-11-23
> **RTrev said:**
> Well, the problem with all of the lightweight Flux distros I've tried must stem from something weird on this hardware; they all come up thinking they should be running at 1280xwhatever rather than the 1024x768 which is the max this monitor can handle.

Consequently, they all boot me into a black screen.  This can usually be fixed by just adjusting xorg, but on Antix, for some reason, I could never get *out* of the black screen so that I could fix it.  The others would allow some key combination to take me to a terminal where I could work, but Antix either has no such key combination, or was too hosed by that point to respond, or something.

If the distro will at least let you work in it you can probably try it out.. but I never found a way to get anywhere with Antix.

Fluxbuntu did the same thing, but then I could at least get to a terminal to (sort of) fix it.  Once I had it running, however, the *applications* themselves still thought they were at the higher resolution.  Not sure how to fix that.  And is was S L O W.  I never saw anything boot as slowly as Fluxbuntu.  My xfce will boot in 1/3 the time of Fluxbuntu.. no idea if other people have that problem.

Hope that helps.

Bob

Thanks for the feedback.
For the antiX livecd at the grub menu, hit F3 and choose the resolution.
If installed, add to the grub menu xres=1024x768
If you get the BlackSD, Ctrl Alt F1 or F2 should put you into the non-gui login screen.
There is also a nogui cheat option you could add to the grub menu.

Thanks once again for the info

---

### Post by Brian96 on 2007-11-24
> **RTrev said:**
> Ah, I see one has to install compiz to make everything work.  It's set to NO effects, but it needs to be there as it's apparently handling all window activity.  Everything works fine now.

I see what you mean, now. I found out today that although I had uninstalled compiz on my laptop, the xserver had not been restarted. On reboot borders were gone!

I did find, though, that the "gnome-compiz" package pulls in just enough to get borders working, and is a couple of packages short of the full "compiz" install. I also discovered that I can't get Compiz working on my laptop because of the laptop display's native resolution.

Still can't get Compiz working on my other machine, though. Apparently folks using pure Xubuntu have the same problem, and haven't found a true solution. It doesn't make sense for a workaround to be required. Surely there is just a missing package or something that full Ubuntu installs that doesn't get pulled when you manually install compiz.

Also, is it just me, or do gnome-core and xfce4 seem to be smaller than they were in the Feisty repositories? I seem to get much less crap with them than I remember getting last time around. I like it!

Now, if I could just get Compiz working.

---

### Post by RTrev on 2007-11-24
> **Brian96 said:**
> 
Still can't get Compiz working on my other machine, though. Apparently folks using pure Xubuntu have the same problem, and haven't found a true solution. It doesn't make sense for a workaround to be required. Surely there is just a missing package or something that full Ubuntu installs that doesn't get pulled when you manually install compiz.

You were quite happy, if I recall correctly, with a setup of Xubuntu and Compiz, no?  So in Gutsy that broke?

> Also, is it just me, or do gnome-core and xfce4 seem to be smaller than they were in the Feisty repositories? I seem to get much less crap with them than I remember getting last time around. I like it!

I wish I had taken better notes, but it seems you're right.  I've run both so far on this 128M antique, and they both run very close to as well as Flux.  They're eating more memory, of course, but they're providing more.  Just finding the right balance is the trick.  I don't really want to have to learn to hand-configure Fluxbox unless I'm really going to be needing to use it a lot.  So far I don't see the need.  Probably if this machine had 64M I'd need to drop back.

> Now, if I could just get Compiz working.


I haven't done a full Xubutu install of Gutsy.. but does it include the options to enable Compiz?  One confusing thing about xfce is that you have the option to have it control the desktop, and also to do compositing.  Perhaps if you turned those options off then Compiz would be able to run?

---

### Post by Brian96 on 2007-11-24
> **RTrev said:**
> You were quite happy, if I recall correctly, with a setup of Xubuntu and Compiz, no?  So in Gutsy that broke?

Correct. Actually, it was just xfce4, not full Xubuntu, and it was Beryl, not Compiz-fusion. In Gutsy, I haven't been able to get Compiz-fusion working with anything less than a full install.


> I haven't done a full Xubutu install of Gutsy.. but does it include the options to enable Compiz?  One confusing thing about xfce is that you have the option to have it control the desktop, and also to do compositing.  Perhaps if you turned those options off then Compiz would be able to run?

I haven't done a full Xubuntu Gutsy install either. There are others on here who have and they report not getting Compiz to work unless they install a full Ubuntu first, then add xubuntu-desktop later.

The compositing features in xfce4 are off by default, so I don't think that is the problem. I get the same error message trying to run compiz in an xfce4 install as I do the gnome-core install (and also the same error messages people running full Xubuntu report), so I don't think that is the problem. I am currently using the xfce4 compositing features and in some ways I like them better than Compiz. But I REALLY miss the scale feature of compiz or beryl, and to a lesser extent the desktop cube.

Also, for some reason my xfce4 minimal install is pretty sluggish, much more so than with Feisty. I'm not sure what the deal is.

---

### Post by Brian96 on 2007-11-24
Actually, I just figured out that my xfce4 install is sluggish because of the compositing effects. When I turn them off it runs fine. :(

---

### Post by RTrev on 2007-11-24
> **Brian96 said:**
> Actually, I just figured out that my xfce4 install is sluggish because of the compositing effects. When I turn them off it runs fine. :(

You know, I was thinking xfce was slower now too.  Your finding that the compositing was the cause prompted me to try *not* letting xfce manage the desktop, and things also seem quicker here now.  I didn't have the compositing turned on, because this is just a little 14" monitor on a 0 GHz P2 and I didn't even think of trying it.  The only things I installed were the minimal xorg and xfce4, so I'm not sure what's managing the desktop at the moment!  Maybe Metacity got pulled in somehow.. I'll have to check that.

Also, as soon as SpinRite is finished working on my disks on the good machine, I'm going to try Linux Mint.

[http://www.linuxmint.com/rel_daryna.php](http://www.linuxmint.com/rel_daryna.php)

There is another thread running here somewhere in which people are saying it's based on Gutsy but has none of the problems people are having with Gutsy.  Can't hurt to look.. and they have light versions, can use the Gutsy repositories, etc.  Sounds like it's worth at least exploring.  All it costs is a blank CD.  :)

---

### Post by Brian96 on 2007-11-25
> **RTrev said:**
> You know, I was thinking xfce was slower now too.  Your finding that the compositing was the cause prompted me to try *not* letting xfce manage the desktop, and things also seem quicker here now.  I didn't have the compositing turned on, because this is just a little 14" monitor on a 0 GHz P2 and I didn't even think of trying it.  The only things I installed were the minimal xorg and xfce4, so I'm not sure what's managing the desktop at the moment!  Maybe Metacity got pulled in somehow.. I'll have to check that.

Also, as soon as SpinRite is finished working on my disks on the good machine, I'm going to try Linux Mint.

[http://www.linuxmint.com/rel_daryna.php](http://www.linuxmint.com/rel_daryna.php)

There is another thread running here somewhere in which people are saying it's based on Gutsy but has none of the problems people are having with Gutsy.  Can't hurt to look.. and they have light versions, can use the Gutsy repositories, etc.  Sounds like it's worth at least exploring.  All it costs is a blank CD.  :)

I may check out LinuxMint, too. I noticed, though, that the "light" version just has proprietary stuff left off. Everything else is still there.

---

### Post by RTrev on 2007-11-25
> **Brian96 said:**
> I may check out LinuxMint, too. I noticed, though, that the "light" version just has proprietary stuff left off. Everything else is still there.

Well, I looked, and the show-stopper for me was that they don't have a 64-bit version.  I use 4G so I can feed lots of it to virtual machines, and 32-bit just doesn't cut it.

I'm going to temporarily pause this experimenting while I get some other things done, and while my wife builds a new machine (so I'll have her old one for a test box.) <g>

In the meantime, I did a fresh install from the alternate CD on my good machine, using two 74G Raptors in RAID-0 as the system disk, and two 500G Caviars in RAID-1 for the data disk.  Boy is this baby flying now!  :)  One second to load Firefox.  :)

---

### Post by Brian96 on 2007-12-15
Thought I'd update:

So I'm using our minimal install method with 7.10 on my computer at work, and am very happy with it. I found solutions to my Compiz problems, so I am using XFCE4 with a completely naked desktop (except for Orage, a sticky notes program, and cairo-clock, which autostart). I open programs with the desktop right-click menu and navigate using the Compiz "scale" feature.

At home I installed a full default Ubuntu 7.10 to play around with, and I am really happy with it as well, so I've pretty much migrated to it as my main OS. For some reason all the extra programs I don't use are not causing me as much distress as last time around. :) Also, some things, like it or not, just seem to work better, with less configuration, in a full install. That is probably the only downside to the minimal install: Trying to figure out which packages you need to install to get X, Y, or Z working.

I have been really impressed with how much has "just worked" for me with 7.10. The only real issue I have is with my ATI card limiting some options (such as Compiz). Also, it may be my imagination, but 7.10 does not seem to use as much system memory as 7.04 did.

---

### Post by DUDE_2000 on 2007-12-15
Look what I found
[http://minibuntu.crealabs.it/](http://minibuntu.crealabs.it/)

---

### Post by Brian96 on 2008-01-19
So, RTrev, did you ever try Zenwalk? I thought I'd give it a shot, but 5.0 is having trouble discovering my virtual disk in VMWare.

---

### Post by RTrev on 2008-01-19
> **Brian96 said:**
> So, RTrev, did you ever try Zenwalk? I thought I'd give it a shot, but 5.0 is having trouble discovering my virtual disk in VMWare.

Hi Brian,

No, I'm not even sure what it is.. but the name rings a bell.  I'll try it in VirtualBox and see if can run there.  Maybe take a while, but I'll report back either way.

bob

---

### Post by RTrev on 2008-01-19
Hi again Brian,

Well, I thought I was going to be able to report success, as the partitioning seemed to work fine in VirtualBox, and it proceeded to begin installing stuff.. for half an hour or so.. and then it suddenly started hitting errors.. said it couldn't install this and that, including xfce, and finally it failed to install Lilo.  At that point, it was all over.. a reboot of the VM of course failed.

Did you get that far?  I gave it a 8G disk, and told it to take the whole thing and do whatever it wanted with it.  Seems that this should have sufficed, no?

It kept suggesting that perhaps the install media was faulty, but I was installing from the ISO file on the hard disk, and the md5 value was in fact WRONG.

I'm starting a new download, and will see what happens this time.  I've never had a bad md5 on the ISO file itself, without having to burn it to a CD, so I didn't think to check.  My bad!

I'll report in tomorrow and see if I can at least verify the download before I try it again.  This time I'm downloading from a different site, figuring maybe the file was corrupted on the original site.  Did you check your md5's?

Let me know if your problems occurred in the same way mine did.  I have come to prefer VirtualBox over VMware, and I suspect this failure was completely my fault.  But, that remains to be seen.  <g>

Best,
Bob

---

### Post by RTrev on 2008-01-20
Well, I got the md5's to match, and the install went smoothly, albeit a bit amusingly.  They pop up messages about what they're installing, and there's a paragraph or two to read.  You have approximately 2 seconds to read it before it's changed.  <g>

So, everything went fine until it came time to install LILO.  I tried the MBR option, and it failed.  It didn't say why it failed.  Then I tried the "expect" option, and did my best, and it failed again.

It says I should be able to boot it off the CD, but so far I just get a blank screen.  Maybe I'll burn an actual CD rather than just using the ISO file like I have been.. although it doesn't seem it should matter.

Looks like a nice distro, but I sure wish people would standardize on either GRUB or LILO.. 

Almost there.  But going to bed now.  <g>  

Bob

---

### Post by Brian96 on 2008-01-20
Thanks for reporting back. I didn't even get as far as you did. I am using VMWare, and after I setup the Keymap, when I click on Partition or Autoinstall I get an error that no disk was selected. I am using an old VM that I created to testdrive Linux distros.

I read on the Zenwalk forum where someone had had a similar problem with an older version, and it was attributed to a problem with the kernel in that particular release. I also have vague memories of trying to install something else that couldn't find the virtual disk, but I can't remember what the fix was.

I wanted to try Zenwalk because everyone talks about how blazing fast it is. It seems like the kind of distro I'd like to learn, but I have a feeling the learning curve will be pretty steep for me, as I haven't really used anything yet that doesn't use aptitude/apt-get/synaptic. But if it is really that light and fast, it may be worth the effort.

---

### Post by RTrev on 2008-01-20
Well, I got tied up and the experiments had to be postponed, but I did a little Googling and it seems that it won't run in the version of VirtualBox that's in the Ubuntu repositories right now.. although it did work fine for the partitioning.  Then again, it's failure to install LILO in the MBR of the VM makes me wonder about that virtual disk.

I got the impression that we wouldn't be too "far from home" with this Debian-based distro.  But I could be wrong.  :)

May just burn a CD and install it on the old test machine and see what happens.

One thing about the Linux world, nothing stays the same for long.  If it won't install today, it probably will tomorrow.  <g>

Bob

---

### Post by Brian96 on 2008-01-21
> **RTrev said:**
> Well, I got tied up and the experiments had to be postponed, but I did a little Googling and it seems that it won't run in the version of VirtualBox that's in the Ubuntu repositories right now.. although it did work fine for the partitioning.  Then again, it's failure to install LILO in the MBR of the VM makes me wonder about that virtual disk.

I got the impression that we wouldn't be too "far from home" with this Debian-based distro.  But I could be wrong.  :)

May just burn a CD and install it on the old test machine and see what happens.

One thing about the Linux world, nothing stays the same for long.  If it won't install today, it probably will tomorrow.  <g>

Bob

One correction--Zenwalk is Slackware-based, not Debian-based. Damn Small Linux, which I previously explored, is Debian-based, however. Can't remember what I didn't like about it.

---

### Post by RTrev on 2008-01-21
> **Brian96 said:**
> One correction--Zenwalk is Slackware-based, not Debian-based. Damn Small Linux, which I previously explored, is Debian-based, however. Can't remember what I didn't like about it.

Thanks for spotting the error.  I'd have sworn I saw something about Debian in the startup screens, but I must have misread it.

I think I'll try DSL again myself, because I also cannot remember what I didn't like about it.  I have a strange new test box, however, which is causing some perplexing errors.  After booting of the CD and getting any 'buntu install well underway, the installer then claims that it can't find any CD drive.

Perhaps just a hardware problem.  I've only been playing with this box today.  But *nothing* will run on it *except* DSL.  None of the live CDs I've tried work.

Will have to figure that out before I can go much further in exploring anything.  <g>

Bob

---

### Post by kelavine on 2008-01-22
> **Brian96 said:**
> Thought I'd update:

So I'm using our minimal install method with 7.10 on my computer at work, and am very happy with it. I found solutions to my Compiz problems, so I am using XFCE4 with a completely naked desktop (except for Orage, a sticky notes program, and cairo-clock, which autostart). I open programs with the desktop right-click menu and navigate using the Compiz "scale" feature.

At home I installed a full default Ubuntu 7.10 to play around with, and I am really happy with it as well, so I've pretty much migrated to it as my main OS. For some reason all the extra programs I don't use are not causing me as much distress as last time around. :) Also, some things, like it or not, just seem to work better, with less configuration, in a full install. That is probably the only downside to the minimal install: Trying to figure out which packages you need to install to get X, Y, or Z working.

I have been really impressed with how much has "just worked" for me with 7.10. The only real issue I have is with my ATI card limiting some options (such as Compiz). Also, it may be my imagination, but 7.10 does not seem to use as much system memory as 7.04 did.

I've been following the thread and was wondering if you could let us know what your "apt-get/aptitude" install is.

---

### Post by Brian96 on 2008-01-23
> **kelavine said:**
> I've been following the thread and was wondering if you could let us know what your "apt-get/aptitude" install is.

I'm not sure I understand your question. Are you asking what packages did I install using the apt-get command after installing the server/base system of 7.10?

---

### Post by RTrev on 2008-01-23
Say Brian, I know now why I thought it was Debian-based.  It has the IceWeasel nonsense, and whatever the other one is.  <g>

Got it installed on a test box, and tried to copy some files in Thunar and the thing froze up

On another topic, when using the mini CD, do you use cli-expert mode?

---

### Post by Brian96 on 2008-01-24
> **RTrev said:**
> Say Brian, I know now why I thought it was Debian-based.  It has the IceWeasel nonsense, and whatever the other one is.  <g>

Got it installed on a test box, and tried to copy some files in Thunar and the thing froze up

On another topic, when using the mini CD, do you use cli-expert mode?

No, I don't. I think, if I recall correctly, I just type "server" at the prompt and let it load the default core system. I don't feel I am near knowledgeable enough to make informed choices in the expert mode.

---

### Post by kelavine on 2008-01-28
> **Brian96 said:**
> I'm not sure I understand your question. Are you asking what packages did I install using the apt-get command after installing the server/base system of 7.10?

Yes, exactly

Thanks

---

### Post by Brian96 on 2008-01-29
> **kelavine said:**
> Yes, exactly

Thanks

Working from memory, with some prompts by going back through this thread, what I did to get a basic system was:

Installed "server" option from the mini.iso CD. After the CLI system was installed and booted up, I installed xserver-xorg-core, gdm, xfce4, xfonts-base, and discover1. The last two packages were required to get Xorg working properly. I cannot remember if synaptic is already installed or if that is one of the things I had to manually install. In any event, it doesn't hurt to include packages you know you'll need; if they are already there it will just ignore the command.

That got the base system. From there I added things like printer support and the like. I also had to dig around in the forums to get Compiz working (I found the 3D features in XFCE to be painfully slow). There is a link elsewhere in this thread that I posted to the fix for this.

Let us know if you have any questions.

---

### Post by Brian96 on 2008-01-29
> **DUDE_2000 said:**
> Look what I found
[http://minibuntu.crealabs.it/](http://minibuntu.crealabs.it/)

Has anybody tried this yet? I wonder if it really is smaller on the backend.

---

### Post by kelavine on 2008-01-30
> **Brian96 said:**
> Working from memory, with some prompts by going back through this thread, what I did to get a basic system was:

Installed "server" option from the mini.iso CD. After the CLI system was installed and booted up, I installed xserver-xorg-core, gdm, xfce4, xfonts-base, and discover1. The last two packages were required to get Xorg working properly. I cannot remember if synaptic is already installed or if that is one of the things I had to manually install. In any event, it doesn't hurt to include packages you know you'll need; if they are already there it will just ignore the command.

That got the base system. From there I added things like printer support and the like. I also had to dig around in the forums to get Compiz working (I found the 3D features in XFCE to be painfully slow). There is a link elsewhere in this thread that I posted to the fix for this.

Let us know if you have any questions.

Thanks!

I've been playing around and following a "server" install have tried
xorg, compiz, gnome-core, gksu, synaptic, deskbar-applet, ubuntu-artwork, human-theme, vino

SYNAPTIC was more to find out about packages.  Ended up using a hair more the 1Gb of disk.

---

### Post by Brian96 on 2008-02-04
> **Brian96 said:**
> Working from memory, with some prompts by going back through this thread, what I did to get a basic system was:

Installed "server" option from the mini.iso CD. After the CLI system was installed and booted up, I installed xserver-xorg-core, gdm, xfce4, xfonts-base, and discover1. The last two packages were required to get Xorg working properly. I cannot remember if synaptic is already installed or if that is one of the things I had to manually install. In any event, it doesn't hurt to include packages you know you'll need; if they are already there it will just ignore the command.

That got the base system. From there I added things like printer support and the like. I also had to dig around in the forums to get Compiz working (I found the 3D features in XFCE to be painfully slow). There is a link elsewhere in this thread that I posted to the fix for this.

Let us know if you have any questions.

A couple of corrections/additions. I actually use the "cli" command on the mini.iso CD (Gutsy) to install a base system. Also, "compiz-core" is required to get the window decorations working in Metacity (not sure about Xfwm).

---

### Post by Brian96 on 2008-03-05
RTrev, what ever happened with your experiment with Arch/Archie? I'm thinking about venturing out a little bit.

I tried Zenwalk the other day and wasn't uber-impressed. If a fast system is your goal, it seems our cli install plus core packages is as good or better than a full install of any of the "lightweight" distros I've tried.

If anyone is looking for an Ubuntu-based system that has all the bells and whistles but "just works," the Fluxbox flavor of Linux Mint was pretty cool.

And if fvwm-crystal was somehow configured to automatically update my menus when I install new packages, I would probably just use that on top of a cli install of Ubuntu.

---

### Post by RTrev on 2008-03-05
> **Brian96 said:**
> RTrev, what ever happened with your experiment with Arch/Archie? I'm thinking about venturing out a little bit.

I tried Zenwalk the other day and wasn't uber-impressed. If a fast system is your goal, it seems our cli install plus core packages is as good or better than a full install of any of the "lightweight" distros I've tried.

If anyone is looking for an Ubuntu-based system that has all the bells and whistles but "just works," the Fluxbox flavor of Linux Mint was pretty cool.

And if fvwm-crystal was somehow configured to automatically update my menus when I install new packages, I would probably just use that on top of a cli install of Ubuntu.

Hey Brian,

Been crazy times here, so haven't explored as much as I might have liked.  Two deaths, two births, and we bought a new BMW for the coming motorcycle season.  <g>

I would agree about crystal, and may even try it again on the test box, but truthfully I've found that the full install of Ubuntu on my powerful machine, and the full install of Xubuntu on the garbage machine, works out well, let's me move stuff back and forth easily, seems sufficient on the slow box and outstanding on the fast box.

I remember Crystal fondly, though...  Hmm...

You've got me thinking again!  :)

Bob

---

### Post by vigi1 on 2008-03-06
> **RTrev said:**
> Before I get started on this, let me make sure I'm clear.  I want the Gnome desktop.  They give a command to get Icewm, which isn't the one I want I don't think.  If I want Gnome, and nothing else, would I substitute Gnome for Icewm?  Or will that get me OpenOffice, Evolution, and so on?

Thanks..

I generated this post yesterday before seeing this thread.
I would like to do the same thing.

[http://ubuntuforums.org/showthread.php?t=716559&highlight=minimal+desktop+install](http://ubuntuforums.org/showthread.php?t=716559&highlight=minimal+desktop+install)

Its a matter of starting with a minimum graphical desktop and building a customized system.

I tried mandrake some years ago, and the installation allowed you to choose exactly what you wanted to install.

 :guitar:

---

### Post by Brian96 on 2008-03-06
> **vigi1 said:**
> I generated this post yesterday before seeing this thread.
I would like to do the same thing.

[http://ubuntuforums.org/showthread.php?t=716559&highlight=minimal+desktop+install](http://ubuntuforums.org/showthread.php?t=716559&highlight=minimal+desktop+install)

Its a matter of starting with a minimum graphical desktop and building a customized system.

I tried mandrake some years ago, and the installation allowed you to choose exactly what you wanted to install.

 :guitar:

Theoretically one could use the packages here: [http://minibuntu.crealabs.it/](http://minibuntu.crealabs.it/)   to create your own custom Ubuntu install CD. Unfortunately, I have no idea where to begin. If I knew how to do it, I would make a handful of isos for a minimal gnome, a minimal kde, and a minimal xfce, in the spirit of this thread. These would include gdm (or kdm for kde) and synaptic and little else. Then you could install, boot into a GUI, and then build the rest of your system with synaptic.

In reality, though, the methods described here are really quite simple, even for newies (which I basically still am). The "recipe" has to be tweaked with each Ubuntu release (e.g., having to add xfonts-base and compiz-core to a Gutsy minimal install to get the x-server and Gnome to work), but if you give us a couple of weeks after each new release, we'll have the updated "recipe" of packages to "apt-get install" on this thread.

Of course, many of us have found that as the newer releases get more efficient, we have less need for a minimal system.(RTrev and myself are both apparently using full Gutsy installs for our main systems.) But it is still fun to tweak every once in a while. :popcorn:

---

### Post by capink on 2008-03-07
If you want to create you own custom cd you can look [here]("http://ubuntuforums.org/showthread.php?t=688872"). Using this guide you have the choice of creating a custom cd from a hard drive installation, but you can also create a custom cd from scratch using debootstrap.

If you any questions I am happy to answer.

---

### Post by Brian96 on 2008-03-07
> **capink said:**
> If you want to create you own custom cd you can look [here]("http://ubuntuforums.org/showthread.php?t=688872"). Using this guide you have the choice of creating a custom cd from a hard drive installation, but you can also create a custom cd from scratch using debootstrap.

If you any questions I am happy to answer.

We've kicked stuff like this around on here before, but it seems that the simplest solution is to just install a cli system and add the 3 or 4 packages we want to get a basic GUI system up and running.

Thanks for the link, though. I did look into this for a couple of hours last night, but then realized that the effort it would take to make a custom live or install CD of our minimal system is really not worth it in light of how easy it is to do it from a traditional cli install.

---

### Post by Brian96 on 2008-04-28
So, anybody tried a minimal Hardy install yet? It's gonna be a while before I play around with that. I don't even have time to do a full install on my new desktop, which I also don't have time to set up! Argh! Grad school!

---

### Post by RTrev on 2008-04-28
> **Brian96 said:**
> So, anybody tried a minimal Hardy install yet? It's gonna be a while before I play around with that. I don't even have time to do a full install on my new desktop, which I also don't have time to set up! Argh! Grad school!

Grad school??  I didn't know you were in school.  What's your major?

No, I haven't tried anything but the normal Hardy install.  Actually, I installed back when it was still alpha, and just kept upgrading.  <g>

Hardy is my daily driver.  Seems fine, although I confess that I haven't put in the work necessary to understand Pulse audio.

Keep us posted as you explore this, studies permitting.  <g>

Best,
Bob

---

### Post by olejorgen on 2008-04-28
Is server edition = minimal edition?

---

### Post by RTrev on 2008-04-28
> **olejorgen said:**
> Is server edition = minimal edition?

Not exactly.  The server edition gives you only the command line system that you'd need to run a server.

What we do is install this bare-bones system, and then slowly add packages to it until we have a GUI system of some sort that meets out needs.  Our goal is to minimize services running if we don't need them, to minimize software installed if we don't use it, etc.

If you can see Ubuntu as built for the masses, with everything that anyone might possibly want, then you can see how some people might like a trimmed-down system with only the components they'll actually use and with no bloat.

I haven't yet done this with Hardy.. been off on other areas of interest in my life.. but will no doubt return to this arena in due time and have more fun.  <g>

Bob

---

### Post by olejorgen on 2008-04-29
Ok, so there isn't a official "bare-bone" ubuntu then. I'm kinda stuck with ubuntu, bacause I havent't gotten suspend to work in debian yet.

---

### Post by RTrev on 2008-04-29
> **olejorgen said:**
> Ok, so there isn't a official "bare-bone" ubuntu then. I'm kinda stuck with ubuntu, bacause I havent't gotten suspend to work in debian yet.

No, no bare-bones version, although creating one's own isn't really too hard.  Scan back over this thread (I can't believe how big it's gotten!)  Try the first few pages, and you'll perhaps hit on just what you need in the way of "recipes" various of us have tried or recommended.

I really wish Ubuntu would add some options to the installer.  For example, "Do you need a word processor?"  "Do you need an email client?"  "Do you plan to print from this system?"  "Do you have any BlueTooth devices [choose yes if you aren't sure]?" and things of that sort.

Bob

---

### Post by Brian96 on 2008-04-30
> **olejorgen said:**
> Ok, so there isn't a official "bare-bone" ubuntu then. I'm kinda stuck with ubuntu, bacause I havent't gotten suspend to work in debian yet.

If I remember correctly, the alternate.iso (or maybe mini.iso) for Gutsy had a "CLI" install version that was different from the server install. That is what I used for the base of my Gutsy minimal install. If you look back through these posts you will find the packages we installed to get a basic desktop environment on top of the CLI install for Gutsy. This was a little different from what we used for Feisty, so we may have to tweak it for Hardy.

Let us know if you have any specific questions.

---

### Post by Brian96 on 2008-06-24
For the record, the recipe we recommend on this thread for a minimal install of Gutsy also works with Hardy (including having to manually install xfonts-base and discover1 to get X to run properly).

---

