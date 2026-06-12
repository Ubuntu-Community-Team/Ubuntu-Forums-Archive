---
title: "Anyone tried KDEMod 4.2?"
date: 2009-01-15
forum: Arch and derivatives
---

### Post by SomeGuyDude on 2009-01-15
Still mega curious about this. Supposedly 4.2 is this giant improvement. Might be enough to make me do the ol' switcharoony, but I'm not sure.

---

### Post by mips on 2009-01-15
I have kdemod 4.2. It's way better than 4.1. Less bugs, faster etc

---

### Post by benerivo on 2009-01-15
I'm on KDE 4.2 RC1, and it is faster, especially konqueror. Dragonplayer seems smoother. Some things still crash for me as they have always done (on any kde4 installation), notably plasma, konqueror, juk, shaman (arch only), and rarely, dolphin. Not any real changes to the design/interface. For me, there were no problems or drawbacks in upgrading from 4.1.

---

### Post by LuisAugusto on 2009-01-15
Those crash are packaging related.

---

### Post by benerivo on 2009-01-15
> **LuisAugusto said:**
> Those crash are packaging related.
What do you mean by 'packaging related'?

---

### Post by LuisAugusto on 2009-01-15
That KDEMod repositories suck. And most problems are caused by their mistakes. If you truly want to test KDE 4.2 as it is, use OpenSUSE 11.1 Build Service (Fedora packages are better too).

---

### Post by SomeGuyDude on 2009-01-15
Well I ain't getting rid of Arch no way no how, so OpenSUSE 11.1 is out, so's Fedora. Heavily tempted to give 'er a go. If things go tits up I'll just reformat, since I've been wanting to switch filesystems for a while now.

---

### Post by LuisAugusto on 2009-01-15
There's an Arch KDE 4 live CD, if you want to give it a shot before installing it:

[http://chakra-project.org/download.html](http://chakra-project.org/download.html)

Tough, if you truly think about using KDE 4 as your main desktop, OpenSUSE is still the best option.

---

### Post by SomeGuyDude on 2009-01-15
Yeah, thing is, I've used OpenSUSE before. I don't like YAST, I don't like RPM-based distros, and I'm not going to install something that comes on a 4 gig DVD. SUSE's another distro with the theory of "throw everything in there to make sure the user has what they need". I just want the DE, not the OS.

---

### Post by LuisAugusto on 2009-01-16
> **SomeGuyDude said:**
> Yeah, thing is, I've used OpenSUSE before. I don't like YAST, I don't like RPM-based distros, and I'm not going to install something that comes on a 4 gig DVD. SUSE's another distro with the theory of "throw everything in there to make sure the user has what they need". I just want the DE, not the OS.

Then, your best shot (even tough I don't agree with anything you said) is to compile KDE 4 from sources (or wait for 4.2 final).

---

### Post by Open-SuSe-A-Me on 2009-01-16
@LuisAugusto

I'm Mexican. If you find any mistakes please let me know, you'll help me improve my English. Thanks in advance. >>>>

"even tough I don't agree at anything you said" 

should be

"even though i don't agree ***with*** anything you said"

---

### Post by ghindo on 2009-01-16
What version of KDE is in the Arch repositories, again?

---

### Post by mips on 2009-01-16
> **LuisAugusto said:**
> That KDEMod repositories suck. And most problems are caused by their mistakes. If you truly want to test KDE 4.2 as it is, use OpenSUSE 11.1 Build Service (Fedora packages are better too).

KDEmod 4 no longer customises packages, You get them as they are from upstream. If there are bugs the fixes are expected to come from upstream. This makes me suspect that OpenSuse does not use vanilla packages.

Have you tried normal KDE4 on Arch, I have not and am just wondering if there is any difference besides the modular packages.

Keep up you nice reviews on your blog, I really enjoy reading them. You seem to have a natural ability to write nice readable reviews.

---

### Post by mips on 2009-01-16
> **ghindo said:**
> What version of KDE is in the Arch repositories, again?

KDE or KDEmod? Anyway you can get both 4.1 & 4.2 depending on which repos you use for both kde & kdemod.

---

### Post by SomeGuyDude on 2009-01-16
> **mips said:**
> KDEmod 4 no longer customises packages, You get them as they are from upstream. If there are bugs the fixes are expected to come from upstream. 

Wait. What do you mean here? If KDEmod doesn't customize anything, what's the difference between it and regular old KDE?

---

### Post by Ptero-4 on 2009-01-16
> **SomeGuyDude said:**
> Wait. What do you mean here? If KDEmod doesn't customize anything, what's the difference between it and regular old KDE?

The difference is that KDEmod makes KDE more modular (for example you get a kate package and a kwrite package instead of having both editors be part of kdebase which is the way vanilla KDE haves it, it applies to all the apps in all the packages, like kopete, kontact, keep, juk, etc).

---

### Post by gjoellee on 2009-01-16
Here is the kdemod-unstable (4.2) repo:

[kdemod-unstable]
Server = http://kdemod.ath.cx/repo/kdemod-unstable/$ARCH

---

### Post by LuisAugusto on 2009-01-16
> **Open-SuSe-A-Me said:**
> @LuisAugusto

I'm Mexican. If you find any mistakes please let me know, you'll help me improve my English. Thanks in advance. >>>>

"even tough I don't agree at anything you said" 

should be

"even though i don't agree ***with*** anything you said"

Thank you very much :-)

---

### Post by mips on 2009-01-17
> **SomeGuyDude said:**
> Wait. What do you mean here? If KDEmod doesn't customize anything, what's the difference between it and regular old KDE?

KDEmod 3.x use to be heavily modded and patched but they stopped that in 4.x.

**The main focus of KDEmod is to be modular, that's it.** KDEmod 4.x has a few customisations but they are minimal and only involve a few logos & names they modified in the original kde to identify it as kdemod. They also backport some things from their unstable to their testing repository at times but not the core repo.

---

### Post by SomeGuyDude on 2009-01-17
> **Ptero-4 said:**
> The difference is that KDEmod makes KDE more modular (for example you get a kate package and a kwrite package instead of having both editors be part of kdebase which is the way vanilla KDE haves it, it applies to all the apps in all the packages, like kopete, kontact, keep, juk, etc).

Oh I see. So it's **KDEmod**ular, not **KDEmod**ified. Hm. Well, if it's all the same, I might as well just install me some KDE and see how she flies.

---

### Post by vishzilla on 2009-01-17
Since KDE 4.2 is releasing on Jan 27th, when will it hit the kdemod core repo?

---

### Post by OutOfReach on 2009-01-17
It's all good here. :)

The only thing that really annoys me right now is a crackling sound from my speakers when the startup sound plays.

EDIT: And I just fixed that bug, turns out KDE was trying to play system sounds from my Internal PC speaker. So everything NOW is flawless.

---

### Post by mips on 2009-01-18
> **vishzilla said:**
> Since KDE 4.2 is releasing on Jan 27th, when will it hit the kdemod core repo?

They are usually on the ball and the repackaged kdemod usually follows quickly. Say a day or two but I'm not speaking on the devs behalve here.

---

### Post by mips on 2009-01-18
> **gjoellee said:**
> Here is the kdemod-unstable (4.2) repo:

[kdemod-unstable]
Server = http://kdemod.ath.cx/repo/kdemod-unstable/$ARCH

[COLOR=Red]Do **NOT** use the kdemod-unstable repository![/COLOR][COLOR=Black]

Kdemod-unstable is out of date. The machine they use to build kdemod-unstable (kde trunk) packages died and nothing has been pulled in from kde trunk to to the unstable repos. Nothing is going to happen here until after 4.2 is released.

The KDEmod-testing repo is the one to use as it is more up to date 4.1.96-3 as of today.

Follow these instructions to install kdemod 4.2 or upgrade your existing unstable install,

[/COLOR] [http://chakra-project.org/news/index.php?/archives/5-KDE-4.2-RC-Packages-available!.html]("http://chakra-project.org/news/index.php?/archives/5-KDE-4.2-RC-Packages-available%21.html")
> **[KDE 4.2 RC Packages available!]("http://chakra-project.org/news/index.php?/archives/5-KDE-4.2-RC-Packages-available%21.html")**

      
Maybe someone already noticed the 4.2 RC packages for i686 in our [[kdemod-testing]]("http://chakra-project.org/repo/testing/") repo, which were available just after the KDE people tagged the release... Well, now that the first set of x86_64 packages has been uploaded too, we think its time to announce them [IMG]http://chakra-project.org/news/templates/default/img/emoticons/smile.png[/IMG]

We encourage everyone to try these packages to find and [report]("http://chakra-project.org/bugs/") any outstanding bugs for them and KDE of course. The RC is quite stable and usable and we will do regular updates from the stable KDE 4.2 branch to include the latest bugfixes until the final is out.

To activate the testing repo and install the packages, just follow these steps:


[LIST=1]
[*]uncomment all other kdemod repos in pacman.conf (yes, [COLOR=Red]**all** [/COLOR]of them)
[*]Add the testing repo [COLOR=Red]**above**[/COLOR] all other repo entries in pacman.conf:

**for i686:**
[kdemod-testing]
Server = [http://chakra-project.org/repo/testing/i686/](http://chakra-project.org/repo/testing/i686/)

**for x86_64:**
[kdemod-testing]
Server = [http://chakra-project.org/repo/testing/x86_64/](http://chakra-project.org/repo/testing/x86_64/)
[*][COLOR=Red]remove all installed[/COLOR] kdemod-extragear and kdemod-playgound packages
[*]*pacman -Sy*
[*]*pacman -Su*
[/LIST]

Extragear and Playground will be available again for 4.2 after the final release. Oh, and you can expect alpha2 (with a **lot** of fixed bugs and improvements) of our LiveCD some days after KDE 4.2 is out [IMG]http://chakra-project.org/news/templates/default/img/emoticons/smile.png[/IMG]

Thats it for now, have fun! 

Jan

Ps: You may have noticed that i am not really a pro when it comes to announcements and such things. If someone would like to help us out with community stuff like writing these announcements or doing some moderating at our forums, just leave us a line - either by mail or just visit our [IRC channels]("http://chakra-project.org/irc.html"). Thanks!

Text in red is my doing!

---

### Post by vishzilla on 2009-01-20
nice. i am looking forward to kdemod 4.2. never felt this confortable with kde before

---

