---
title: "Start alternate program on iPod mount?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Scwounch on 2007-04-02
Is there a way to start another media player (instead of Rhythmbox) or no player at all to start when an iPod is connected?  I'm just not thrilled by the default and would rather have a different prog or no prog at all start when I connect it.

I noticed that I can't remove Rhythmbox altogether without also removing some gnome desktop thing also.  It's strange to me that they're so tightly integrated.  Thanks in advance!

---

### Post by dfreer on 2007-04-03
System > Preferences > Removable Drives and Media
Multimedia > Portable Music Players
Either uncheck it so that no music players start, or enter the path to the program you want to start (say, Amarok? :D )

---

### Post by Scwounch on 2007-04-03
Sounds good.  I can't test it yet, but when I get home from work, I surely will.  Thanks so much!  Are you an Amarok fan?  My first thought was to install Amarok, but I want to sort of shop around.  How does it compare to say... Banshee?

---

### Post by galroth on 2007-04-03
I'm a HUGE Amarok fan.  I use it with my IPOD, as well as my default music player.

---

### Post by Delkster on 2007-04-03
> **Scwounch said:**
> I noticed that I can't remove Rhythmbox altogether without also removing some gnome desktop thing also.  It's strange to me that they're so tightly integrated.  Thanks in advance!

It's hard to say exactly without knowing the exact name of the desktop package you refer to but it's probably a so-called metapackage. That means it's only purpose is that it's been intentionally set to be dependent on a certain set of other packages, thus binding them together. So, for example, by having the package ubuntu-desktop installed you can make sure that you have everything that belongs to the default Ubuntu installation. That's completely intentional.

If it's a metapackage, it doesn't contain any software itself. Removing it doesn't directly cause the removal of any other packages either. Thus, removing the ubuntu-desktop package won't cause your desktop to disappear, but having such metapackages to bind stuff together is useful if you want to make sure that you have at least the basic utilities installed, and it's also a good idea to have ubuntu-desktop installed if/when you upgrade to a new release of Ubuntu.

Just to clear things up a bit.

---

### Post by Scwounch on 2007-04-03
Thanks for the responses, everyone.

Delkster:  I see what you're getting at and it makes a lot of sense.  All the extraneous software that comes with Edgy isn't too heavy, so I guess for some sense of safety and compatability, I'll leave it alone.  My only real reason for wanting it removed so badly in the first place was to keep it from popping up when I didn't want it to anyway.

By the way, is there a place in Ubuntu/Linux where file type associations can be edited?  I noticed that if I look at a file's properties, I can change that type's program association, but I'd like to manage them all at once.

---

### Post by Delkster on 2007-04-03
> **Scwounch said:**
> so I guess for some sense of safety and compatability, I'll leave it alone
It can be removed safely. Just make sure to install it again just in case before upgrading to a new release. That's probably mentioned in the upgrading instructions anyway.

> By the way, is there a place in Ubuntu/Linux where file type associations can be edited?  I noticed that if I look at a file's properties, I can change that type's program association, but I'd like to manage them all at once.
Probably not in Gnome. I think KDE has something like that.

I've been wishing for a way to change the associations for all audio file types or all images at once myself.

---

### Post by Scwounch on 2007-04-05
I just found a program that might serve this purpose.  Try Galternatives:

sudo apt-get install galternatives

---

