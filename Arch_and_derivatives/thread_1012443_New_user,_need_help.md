---
title: "New user, need help"
date: 2008-12-15
forum: Arch and derivatives
---

### Post by inxygnuu on 2008-12-15
Hello, I just installed Arch, because i heard it was ridiculously fast, and sounded neat. So i plopped in the cd, and The partitioner would not work, so I did a clean install (format too) and I have to say: I LOVE IT!! It is utterly confusing, and a new leaning experience:p. as a new user, what should I install through pacman, and how? I have the beginners guide right in a tab here if you need me to reference to that. 

Thanks in advance,
3v4n

---

### Post by cardinals_fan on 2008-12-15
Well, the whole point of Arch is that you install only what you want.  Either install the apps you usually use or go for a very lean system.  If you choose the latter, I can post some suggestions for light apps.

---

### Post by SuperSonic4 on 2008-12-15
The Arch wiki will be your best friend if it is not already. From running arch I've learnt more about what makes Linux tick so to speak.

[http://wiki.archlinux.org/index.php/Post_Installation_Tips](http://wiki.archlinux.org/index.php/Post_Installation_Tips)

As said, just pick what you want. For me that was

amarok-base
firefox
k3b

(I picked KDE4mod in case there was any doubt after those apps :p)

---

### Post by hardyn on 2008-12-15
i was looking at arch, reading some of readmes... it says it uses a classic bsd style init and a minimal set of startup scrips; now i am cool with this but does a GUI environment bring along all the nice things like notebook special keys and all those other good things or will i have to dump scrips for special keys, FN combination from my ubuntu install?

Thanks for any help... sorry about the thread hijack.

---

### Post by inxygnuu on 2008-12-15
I like all the quick responses, but what should i install? gnome, or KDE? i have tried them both, and like them both, and how do I get my desktop to look like (as fancy) the ones in the desktop thread? I simply want suggestions.

Thanks,
3v4n

---

### Post by Rumor on 2008-12-15
Well, that's pretty much up to you. if you like gnome, use it, if you prefer KDE, use it. 

To my way of thinking, Gnome is more customizable than KDE looks-wise, but Openbox is more customizable still. If you want to really tweak every little thing, install FVWM and go to town. In the Arch forums are several screenshot threads, many with config files and settings that you can try out.

In the end, what looks good to me may not impress you very much, so pick what you like and start looking at how you can tweak it the way you want it.

---

### Post by crimesaucer on 2008-12-15
> **hardyn said:**
> i was looking at arch, reading some of readmes... it says it uses a classic bsd style init and a minimal set of startup scrips; now i am cool with this but does a GUI environment bring along all the nice things like notebook special keys and all those other good things or will i have to dump scrips for special keys, FN combination from my ubuntu install?

Thanks for any help... sorry about the thread hijack.

If you install Gnome it might have "notebook mulimedia keys" out of the box. My brand new HP DV9920US had the volume slider, mute, stop, play, pause, forward, and back..... all of the LED lights worked.


If you install xfce4 you might have to install an app like "Keytouch": [http://wiki.archlinux.org/index.php/Keytouch](http://wiki.archlinux.org/index.php/Keytouch)

Extra_Keyboard_Keys: [http://wiki.archlinux.org/index.php/Extra_Keyboard_Keys](http://wiki.archlinux.org/index.php/Extra_Keyboard_Keys)


Since I only use xfce4 now I use keytouch..... and I like it better than the default Gnome bind-keys. This way I have my volume and mute with alsamixer, and my start/stop,pause,forward,back all work with my totem-xine using custom commands. You could do this with any app or just use the defaults.


You can even create new binded keys to open other apps like Firefox homepage or do other commands like pm-suspend (I haven't tried this but it should be possible).

---

### Post by Dr Small on 2008-12-15
> **inxygnuu said:**
> I like all the quick responses, but what should i install? gnome, or KDE? i have tried them both, and like them both, and how do I get my desktop to look like (as fancy) the ones in the desktop thread? I simply want suggestions.

Thanks,
3v4n
Go for a lightweight window manager, if you have tried the DE's and want to try something different. I prefer Openbox with pypanel, feh, and conky. But others use Fluxbox, blackbox, wmii, IceWM and others.

---

### Post by handy on 2008-12-15
> **inxygnuu said:**
> I like all the quick responses, but what should i install? gnome, or KDE? i have tried them both, and like them both, and how do I get my desktop to look like (as fancy) the ones in the desktop thread? I simply want suggestions.

Thanks,
3v4n

I used to use Gnome, had to use KDE on some distro's, went to Arch & used Gnome, then Openbox, which is fast & light, takes a little scripting to setup, & now I use Xfce, & I've never been happier with a desktop or window manager, ever.

Xfce is fast, light & simple.  It installs in a couple of minutes.  You still have the same problems as with anything else that uses GTK as far as theming in concerned, & to get deep into menu editing requires editing script.  I don't have enough app's installed on my machine to have needed to edit the menu script I could satisfactorily do all I need from the Settings/ Menu Editor GUI.

In Arch/Xfce I use:

Worker
Firefox
FileZilla
Transmission
Mousepad
Gcolor2
Gwenview
Mirage
Avidemux
NeroLinux
VLC
Zenmap
Vidalia
Zenmap
ePDFViwer
Htop

---

### Post by Sorivenul on 2008-12-15
Arch is fast, even with GNOME or KDE, but I suggest stepping away from the major two, at least for some time.  Xfce is a nice alternative that isn't too far from the "norm", IceWM is a fine piece of work, as are the *box WM's already mentioned, among others.  You may learn you appreciate something new. As far as applications go, search the Arch repos, and try things.  Nothing says you have to keep anything around if you don't like it.

Install "yaourt", the pacman wrapper for using the AUR.  If you don't know what these things are yet, you will, and you will probably love them. Look them up in the documentation.

Above all, have fun!

---

### Post by inxygnuu on 2008-12-16
what about effects? Like compiz? I know I sound dumb, but just a few questions. I want my arch to be fast, but fancy too.

---

### Post by namegame on 2008-12-16
> **inxygnuu said:**
> what about effects? Like compiz? I know I sound dumb, but just a few questions. I want my arch to be fast, but fancy too.

[http://wiki.archlinux.org/index.php/Compiz](http://wiki.archlinux.org/index.php/Compiz)

The arch wiki has almost everything you'll ever need to know about arch.

---

### Post by inxygnuu on 2008-12-16
I have looked, but can xfce work with compiz? It seems so, but I am not sure. *note* when answering these, please realize that I am young, new to this, and simply want to try it out, this is simply a test machine.

---

### Post by cardinals_fan on 2008-12-16
> **inxygnuu said:**
> I have looked, but can xfce work with compiz? It seems so, but I am not sure. *note* when answering these, please realize that I am young, new to this, and simply want to try it out, this is simply a test machine.
Absolutely!  Compiz will run fine on Xfce.

[http://wiki.archlinux.org/index.php/Compiz_Fusion#Xfce](http://wiki.archlinux.org/index.php/Compiz_Fusion#Xfce)

The wiki is very much your friend :D

---

### Post by handy on 2008-12-16
I never use Compiz, though it does work in Xfce, as Xfce is based on Gtk which is under Gnome.

***[Edit:]** Here is a link to a how-to on Compiz, it is a good idea to bookmark the How-to's index as there is a lot of great help files listed alphabetically there.*

[B][I][U][http://wiki.archlinux.org/index.php/Compiz](http://wiki.archlinux.org/index.php/Compiz)

[http://wiki.archlinux.org/index.php/Category:HOWTOs_(English](http://wiki.archlinux.org/index.php/Category:HOWTOs_(English))[/U][/I][/B]

Here is an easy how-to for setting up Xfce on Arch:

***_[http://archux.com/page/installing-and-setting-xfce](http://archux.com/page/installing-and-setting-xfce)_***

---

### Post by inxygnuu on 2008-12-16
When I install, it always askes me to remove initscripts. I am guessing is shouldn't do this. right?

---

### Post by handy on 2008-12-16
> **inxygnuu said:**
> When I install, it always askes me to remove initscripts. I am guessing is shouldn't do this. right?

When your not sure about deleting something, find it on your system & rename it by sticking something on the end of it like .old .  Then if you do find that you need it all you have to do is give it back its real name.

---

### Post by inxygnuu on 2008-12-16
wait... I just upgraded it, and installed something, no error message!:KS
I have xfce, and the extras, what should I install now?

---

### Post by handy on 2008-12-16
Have a look here:

***_[http://wiki.archlinux.org/index.php/Post_Installation_Tips#Configure_dhcpcd](http://wiki.archlinux.org/index.php/Post_Installation_Tips#Configure_dhcpcd)_***

Then spend some time looking through the alphabetic How-To list in the Arch Wiki:

*_**[http://wiki.archlinux.org/index.php/Category:HOWTOs_(English](http://wiki.archlinux.org/index.php/Category:HOWTOs_(English)) **_*

---

### Post by inxygnuu on 2008-12-16
(knew it would happen;)) Now my system is stuck at "loading udev events" any ideas?

---

### Post by crimesaucer on 2008-12-16
> **inxygnuu said:**
> (knew it would happen;)) Now my system is stuck at "loading udev events" any ideas?

My HP laptop will do this when booting with my battery power. (it doesn't happen with the AC power adapter plugged in.)


It also gets stuck on ACPI. If I press "enter" a few times it loads those and moves on with the boot up process. Same thing when shutting down.


This has been an issue for me with all Kernel version since 2.6.27 (for a HP dv9920us laptop..... this didn't happen with 2.6.26 and 2.6.25 versions). Plus, I use my own vanilla AMD64 kernel patched with zen3-sources patch and it also does this. So it's more of a kernel26 2.6.27 thing than an Arch thing. (stock -ARCH kernel does this also)


So see if the "enter" button moves the boot-up past udev loading.

---

### Post by wolfvorkian1 on 2008-12-17
> **inxygnuu said:**
> (knew it would happen;)) Now my system is stuck at "loading udev events" any ideas?

I don't what you mean by "stuck". Mine invariably "hangs" there for a couple seconds, sometime longer but invariably finishes booting. I don't even know what udev means but I don't worry about it. It has never failed to not boot.

---

### Post by inxygnuu on 2008-12-17
> **crimesaucer said:**
> My HP laptop will do this when booting with my battery power. (it doesn't happen with the AC power adapter plugged in.)


It also gets stuck on ACPI. If I press "enter" a few times it loads those and moves on with the boot up process. Same thing when shutting down.


This has been an issue for me with all Kernel version since 2.6.27 (for a HP dv9920us laptop..... this didn't happen with 2.6.26 and 2.6.25 versions). Plus, I use my own vanilla AMD64 kernel patched with zen3-sources patch and it also does this. So it's more of a kernel26 2.6.27 thing than an Arch thing. (stock -ARCH kernel does this also). Besides, i tried everything, nothing would work.


So see if the "enter" button moves the boot-up past udev loading.

Oh, i am sorry, My HP runs Ubuntu and vista. and i have the same problem as you, i have to press a button for it to load. No, this is on my Inxygnuu-1 (pre-alpha/test) machine

---

### Post by inxygnuu on 2008-12-17
> **wolfvorkian1 said:**
> I don't what you mean by "stuck". Mine invariably "hangs" there for a couple seconds, sometime longer but invariably finishes booting. I don't even know what udev means but I don't worry about it. It has never failed to not boot.

It wouldn't load. It is okay, since I didn't get too far, I simply did a fresh install only a couple minutes anyway!;) This time, i am going to install things in a different order.

---

### Post by crimesaucer on 2008-12-17
> **inxygnuu said:**
> Oh, i am sorry, My HP runs Ubuntu and vista. and i have the same problem as you, i have to press a button for it to load. No, this is on my Inxygnuu-1 (pre-alpha/test) machine

My HP runs ARCH and my Vista partition perfectly..... it is only an issue with the current 2.6.27 kernel that messed something up.


Everything boots (super fast) when plugged into the AC adapter.


If I boot up with only the battery power the boot up process will stop at UDEV and ACPI unless I press enter to "load" it manually..... then it boots up and works normally with the battery power. (no fails)


What kernel version is your Ubuntu using?

---

### Post by inxygnuu on 2008-12-17
Newest stable version (ends with 9-27 somewhere). Is there a fix to it?

---

### Post by handy on 2008-12-17
It is one of those bugs that will eventually pass.

I'd just put up with it, then one day after an -Syu you will find it is gone. :-)

I'm waiting (amongst quite a few other users) on one of those to go away from the Catalyst driver.

---

### Post by crimesaucer on 2008-12-17
> **inxygnuu said:**
> Newest stable version (ends with 9-27 somewhere). Is there a fix to it?

I see that you have Ubuntu 8.10 so that would be the 2.6.27-7 version of kernel26.... I think the problem I have is specific to the HP dv9000 series (mine is a dv9920us).

The -ARCH kernel is now at version 2.6.27.8-1 but I'm sure that it will be moving along to 2.6.27.9-1 soon.


Good luck with your problem.

---

### Post by inxygnuu on 2008-12-17
Well, I just did a reinstall, so problem gone :D.

---

