---
title: "GPG/PGP &amp; Seahorse Support in Ubuntu 5.04?"
date: 2005-06-20
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-06-20
I found GPG in Kubuntu, but after switching to Ubuntu, I can find no mention of it anywhere in packet management.

How do I get GPG or PGP in Ubuntu, and how do I install Seahorse to manage it in Gnome?

Thanks for any help.

---

### Post by polo_step on 2005-06-20
Ah!  Digging about, I found GPG, but not a frontend for it.

Can I apt-get Seahorse?

---

### Post by intangible on 2005-06-20
It's **gnupg** in synaptic, to get seahorse, you'll either have to download it manually (Try searching [http://packages.ubuntu.com](http://packages.ubuntu.com)) or enable the universe repository to show it in synaptic.  Here's instructions on how to enable the universe repositories.  [https://wiki.ubuntu.com//AddingRepositoriesHowto](https://wiki.ubuntu.com//AddingRepositoriesHowto)

Oh, and then just start seahorse-agent in gnome to make it manage your gpg keys (like for evolution).

---

### Post by polo_step on 2005-06-20
[QUOTE=intangible]It's **gnupg**...[/QUOTE]

OK, but is there a graphical frontend installed somewhere in 5.04?

---

### Post by polo_step on 2005-06-20
[QUOTE=intangible]It's **gnupg** in synaptic, to get seahorse, you'll either have to download it manually (Try searching [http://packages.ubuntu.com](http://packages.ubuntu.com)) or enable the universe repository to show it in synaptic.  Here's instructions on how to enable the universe repositories.  [https://wiki.ubuntu.com//AddingRepositoriesHowto](https://wiki.ubuntu.com//AddingRepositoriesHowto)

Oh, and then just start seahorse-agent in gnome to make it manage your gpg keys (like for evolution).[/QUOTE]
OK, I did all that successfully, except I don't know how to do that last line, starting seahorse-agent in Gnome.

Seahorse shows up as active in Synaptic, so I'm probably well on my way. :smile: 

Thanks for any help

---

### Post by jdong on 2005-06-20
See [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Add the two Backports lines for an updated Seahorse ;)

---

### Post by intangible on 2005-06-20
To make sure seahorse-agent is running do this: **System->Preferences->PGP Preferences** then **Password Cache** and it will let you know if seahorse-agent is running, it also has a button to start it.  If it doesn't start automagically when you log in, you may have to add it to startup in your session manually (the command to add is just "seahorse-agent").  Seahorse agent has to be running to use GPG properly from Evolution.

Have Fun :D

---

### Post by polo_step on 2005-06-20
[QUOTE=intangible]Seahorse agent has to be running to use GPG properly from Evolution.[/QUOTE]
Hmm.  I was wondering why I was only getting key management.

I'm not using Evolution at the moment, but rather Thunderbird.  I'm assuming that Thunderbird doesn't support this?

---

### Post by intangible on 2005-06-20
You'll need to install the enigmail support for thunderbird to make it do GPG.

I haven't used it personally, but I've seen it used, so I know it works :D

**sudo apt-get install mozilla-thunderbird-enigmail**

---

### Post by polo_step on 2005-06-20
[QUOTE=intangible]
**sudo apt-get install mozilla-thunderbird-enigmail**[/QUOTE]

Hmm... *That* was a little strange!:

anonymous@beatdown:~$ sudo apt-get install mozilla-thunderbird-enigmail
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  mozilla-thunderbird-enigmail
0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
Need to get 0B/297kB of archives.
After unpacking 1331kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter


Preconfiguring packages ...
Selecting previously deselected package mozilla-thunderbird-enigmail.
(Reading database ... 58965 files and directories currently installed.)
Unpacking mozilla-thunderbird-enigmail (from .../mozilla-thunderbird-enigmail_0.90.2-1_i386.deb) ...
Setting up mozilla-thunderbird-enigmail (0.90.2-1) ...
Updating mozilla-thunderbird chrome registry...done.

---

### Post by polo_step on 2005-06-20
Enigmail is in Thunderbird now, but it's pretty screwy as that sort of thing goes.

Dang, is it too much to ask to just have a GnuPG tool that will encrypt or decrypt from clipboard so I can cut & paste? Even Kgpg would do that.

There's gotta be a simple solution I'm overlooking here...

---

### Post by intangible on 2005-06-20
There's gpgp but I don't care for it too much because it's gtk1 based.

---

### Post by polo_step on 2005-06-20
It seems utterly impossible to me that there isn't a simple clipboard function for this somewhere.  It's so freakin' obvious compared to all that other monkey-motion.

If not, this is fatal and Ubuntu (or at least Gnome) goes, unfortunately.

---

### Post by polo_step on 2005-06-20
According to [another site,](http://www.ecn.org/crypto/soft/frontends.phtml) 

"Seahorse is a Gnome front end for GnuPG, the GNU Privacy Guard program. It is a tool for secure communications and data storage. Data encryption and digital signature creation can easily be performed through a GUI and Key Management operations can easily be carried out through an intuitive interface." 

So...supposedly I can do encryption with this thing somehow -- yet, incredibly, there appears to be no documentation for this program *anywhere,* including the Seahorse [site.](http://seahorse.sourceforge.net/)

---

### Post by intangible on 2005-06-20
Ah, I knew it existed, had a hard time finding it though, "gpa" seems to do more of what you want a little better, but it doesn't seem to do copy+paste either.

You can install and use kgpg in Gnome, you don't have to run KDE to use it.

If you think this is a serious feature Ubuntu should have, why not suggest it for Breezy Badger?

Here is a link to the forum for suggestions: [http://www.ubuntuforums.org/forumdisplay.php?f=70](http://www.ubuntuforums.org/forumdisplay.php?f=70)

---

### Post by polo_step on 2005-06-20
[QUOTE=intangible]
You can install and use kgpg in Gnome, you don't have to run KDE to use it.[/quote]
But...but...isn't that *heresy?*  Won't something explode?  Will I be endangering my mortal soul?  

OK, I'll give it a try.

> If you think this is a serious feature Ubuntu should have, why not suggest it for Breezy Badger?
I think it's a pretty rudimentary need, but it may be covered already by something that's there I don't know how to use properly...like Seahorse.

Thanks for your help.

---

### Post by polo_step on 2005-06-20
Kgpg seems to have installed OK and works.

Seems weird, but there it is!

Thanks again!

---

### Post by intangible on 2005-06-20
So it's been about an hour, has your computer exploded yet? :D

Well I'm glad you got something working :)

I used to remember Nautilus automatically having a built in option for handling things with GPG around 2.3 time-frame... but it's not in there anymore... seems like someone thought adding too much to the file-manager was a bad idea.  It sure was nice to have right-click access to all the GPG functions back then.

Something else you may want to look into is Nautilus-Scripts.   You can write your own scripts to handle encrypting and decrypting files and have them show up on a right-click.

Anyway, if you come up with a kewl Nautilus script, let the rest of us know :D

---

### Post by polo_step on 2005-06-21
[QUOTE=intangible]So it's been about an hour, has your computer exploded yet? :D

Well I'm glad you got something working :)
[/QUOTE]
Oy, I spoke too soon.  On rebooting, when I try to invoke Kgpg I get:

"The use of GnuPG Agent is enabled in GnuPG's configuration file (/home/anonymous/.gnupg/gpg.conf).
However, the agent does not seem to be running. This could result in problems with signing/decryption.
Please disable GnuPG Agent from KGpg settings, or fix the agent."

Hmm.  What next? :neutral:

---

### Post by intangible on 2005-06-21
Looks like you'll have to run an agent for GPG after all, just try this, "seahorse-agent" and then "kgpg" and see if it works.  If so, just make sure to put seahorse-agent in your startup programs.

---

### Post by polo_step on 2005-06-21
[QUOTE=intangible]Looks like you'll have to run an agent for GPG after all, just try this, "seahorse-agent" and then "kgpg" and see if it works.  If so, just make sure to put seahorse-agent in your startup programs.[/QUOTE]
The bizarre part of this is that Kgpg works anyway...though I get an error screen at desktop load that says the icon for it can't be found.

Works OK, but needs some cleaning up somewhere -- maybe getting rid of conflicting or redundant programs like Seahorse.  I guess the icon is somewhere in an uninstalled suite of KDE icons, or Kgpg is looking for it in a directory that doesn't exist under Gnome...or ???

At boot today, after using Kgpg a bit last night to send & receive/encrypt & decrypt, the only error I have now it from its inability to find an icon.  Apparently the other part auto-configured or something.  :-?

---

### Post by intangible on 2005-06-22
It doesn't happen to say what icon it is looking for does it?

You could always try "strace" (apt-get install strace)
"strace kgpg" and see you you can see what file it is looking for.   (BEWARE, strace will give you lots of useless/useful information, it may be difficult to dig through)

If you can find the filename it is looking for, then you can do a search for it at [http://packages.ubuntu.com](http://packages.ubuntu.com)  and install the package with it.

---

### Post by polo_step on 2005-06-22
[QUOTE=intangible]It doesn't happen to say what icon it is looking for does it?[/quote]

No, but there's a blank where the icon should be displayed in the "Launcher Properties" pulldown screen. 

> You could always try "strace" (apt-get install strace)
"strace kgpg" and see you you can see what file it is looking for.   (BEWARE, strace will give you lots of useless/useful information, it may be difficult to dig through)

I installed and ran it and then cut & pasted it into the text editor so I could search for "icon" -- nothing came of it, nor did I find anything conspicuous just rooting through it.  I don't now what the Linux extension is for an icon file.

> If you can find the filename it is looking for, then you can do a search for it at [http://packages.ubuntu.com](http://packages.ubuntu.com)  and install the package with it.
I figured there would be an option like this.  There may be an icons folder somewhere in the KDE suite, a quick perusal of which would turn up the file.  I'm just assuming there's a standard icon extension and I'd be looking for kgpg.*.

The other error is back:

==========================================
"The use of GnuPG Agent is enabled in GnuPG's configuration file (/home/anonymous/.gnupg/gpg.conf).
However, the agent does not seem to be running. This could result in problems with signing/decryption.
Please disable GnuPG Agent from KGpg settings, or fix the agent."
==========================================

So...I did indeed disable GnuPG Agent in the Kgpg settings, as it suggested.  We'll see if that makes  any difference at the next boot.

There's also been one saying that sound [!] has a problem when I invoke Kgpg, but as I don't have the speakers hooked up to this yet, I don't know what that's about:

===========================================
Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)
The sound server will continue, using the null output device.
===========================================

Of course, it works, and ultimately that's what matters, but it's a slovenly sort of thing to let this stuff keep popping up all the time.

---

### Post by polo_step on 2005-06-23
[QUOTE=polo_step]
So...I did indeed disable GnuPG Agent in the Kgpg settings, as it suggested.  We'll see if that makes  any difference at the next boot.
[/QUOTE]
Well, rebooting after all that finds that the error messages are all gone.

Progress!

Funniest thing, though:  The little taskbar "lock" icon (not the main Kgpg one that's still missing) has moved over to the extreme left, next to "Applications."

Now, *that's* mysterious!

Well, at least to *me.* :neutral:

---

### Post by polo_step on 2005-06-23
Well, the sound error (above) is back...but the little lock goes over where it is supposed to be.

Funny business, no lie...

---

### Post by intangible on 2005-06-24
The sound error is probably okay, KDE and Gnome use different sound servers so they don't work 100% off the bat every time, but you don't need sound effects in KGPG do you?  It would kindof be a waste of effort to get that error message to go away when the program itself doesn't actually play sound (it's probably just the toolkit, QT, connecting to the server).

Anyway, let me know if you need more help.

---

### Post by polo_step on 2005-06-24
[QUOTE=intangible]but you don't need sound effects in KGPG do you?  It would kindof be a waste of effort to get that error message to go away when the program itself doesn't actually play sound (it's probably just the toolkit, QT, connecting to the server).[/QUOTE]
No, I don't want sound, I just don't want to have to look at that error message...but today it isn't showing up.

Weird, no kidding!

---

