---
title: "Ubuntu or Mint as a Server OS?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Rotting on 2008-03-11
I noticed a list at some site (I think it was distrowatch.com) that gave a rundown of a lot of linux distributions, and it caused me to wonder about a few things. It lists ubuntu and mint as “desktop” distributions, and other distributions as “server” or “workstation” etc. 

So, what about Mint makes it NOT ideal to say, run a mailserver on, or a file server, etc? I can see if some distributions don’t default install with X11 or something along those lines making it not ideal for desktop home users, but what, intrinsically, would make it more difficult to run servers with Ubuntu or Mint? 

Thanks,

Rotting

---

### Post by Arkenzor on 2008-03-11
I'd definitely not advise you to try and run a server with Linux Mint. Not that you can't do it - in the end, when you know how to configure things you can do anything with any distro. It'll simply be a huge waste of your time because you'll need to install and configure all required software on your own. As for the GUI on a server, you may like if you want, it's probably even a good thing if you install it on a home computer with a screen, keyboard and mouse. The only issue is that you many people start feeling sick when they realize they have 1GB of useless software on their server.

As for Ubuntu, the server edition can certainly be used for a server, that's what it's for, actually ^^'.

---

### Post by PriceChild on 2008-03-11
Linux Mint is not Ubuntu. There are various changes which split it apart, and mean it may be different in its support.

I'm wondering why on earth you want Mint for a server? I was of the opinion that the whole idea was to install codecs and other shiny desktop things by default?

---

### Post by twright on 2008-03-11
linux mint has some things automatically configured that ubuntu doesn't

while automatic is good for the desktop you usually want to do stuff more manually on the server

also it would be unsuited for the same reasons that ubuntu desktop isn't, it's not designed for servers

there's no reason that you couldn't run a small samba, cups or ftp server on it but if a machines primary use is as a server it is best to go for something else

---

### Post by justleen on 2008-03-11
as a quick note on X on a server: most computers nowaday are perfectly capable to run X and do other stuff. Just close X when you dont use it though..

---

### Post by Oldsoldier2003 on 2008-03-11
> **Arkenzor said:**
> I'd definitely not advise you to try and run a server with Linux Mint. Not that you can't do it - in the end, when you know how to configure things you can do anything with any distro. It'll simply be a huge waste of your time because you'll need to install and configure all required software on your own. As for the GUI on a server, you may like if you want, it's probably even a good thing if you install it on a home computer with a screen, keyboard and mouse. The only issue is that you many people start feeling sick when they realize they have 1GB of useless software on their server.

As for Ubuntu, the server edition can certainly be used for a server, that's what it's for, actually ^^'.
Agreed!

Regardless of whether you install the gui on a server box, you WILL need to use the command line. The tools are just not there for GUI administration of an Ubuntu Server. Sure you can add web based control panels... * but ultimately the terminal is your best friend and most powerful tool.*

---

### Post by Rotting on 2008-03-11
Thanks for all the replies.

I guess I'm still in the dark about the core of my question. I understand from all the replies that it's NOT a good idea to user Mint to run a server, but the question is still WHY? Is it just that Mint installs too much "crap" by default? From what I understand, people are saying that Mint has too much "stuff" but not that it lacks any particular thing. So, maybe a better question would be: Other than having stuff you don't need, can Mint or a similar distribution run a server just as readily or does it LACK anything that a server-centric distro has?

Don't get me wrong, I'm not dead set on using Mint to run a mail server, I'm simply interested in the whys and whats and hows of linux as a beginner.

---

### Post by jken146 on 2008-03-11
Ubuntu Server has a kernel that is optimised for server use (don't ask me how).  I don't think that there is a version of Mint like this.

---

### Post by ByteJuggler on 2008-03-11
> **Rotting said:**
> Thanks for all the replies.

I guess I'm still in the dark about the core of my question. I understand from all the replies that it's NOT a good idea to user Mint to run a server, but the question is still WHY? Is it just that Mint installs too much "crap" by default? From what I understand, people are saying that Mint has too much "stuff" but not that it lacks any particular thing. So, maybe a better question would be: Other than having stuff you don't need, can Mint or a similar distribution run a server just as readily or does it LACK anything that a server-centric distro has?

Don't get me wrong, I'm not dead set on using Mint to run a mail server, I'm simply interested in the whys and whats and hows of linux as a beginner.

My $0.02 worth

"can Mint or a similar distribution run a server just as readily" Yes, in principle.

"does it LACK anything that a server-centric distro has?" Possibly (not having checked as such), but probably not, and in any case if it does it's likely no big deal to install.

There's in reality no highly compelling single reason to say you *must* use the server distro services, but rather, a collection of debateable smaller reasons which collectively becomes convincing in some scenarios.  Probably the biggest one in my book is one of security.  The less running and installed on a box, the fewer potential and actual attack vectors there are.  But, even that, is more preventative paranoia in reality - in practice you're likely not really any more vulnerable with a desktop distribution than with a desktop one. 

Personally, I run a game server with attendant MySQL, Apache etc. on (what is still currently) a Feisty desktop install, 24/7.  Zero problems.  Rebooted the other day with like 37 days uptime to upgrade the kernel.  (The minimalist in me is however currently considering reinstalling the box with 64bit Ubuntu server, with the intent to keep it nice and minimalistically lean.  64-bit, because I've recently added RAM which the box now can't fully use, and because I run virtual machines on it.  Anyway we'll see. :))

---

### Post by Oldsoldier2003 on 2008-03-11
> **Rotting said:**
> Thanks for all the replies.

I guess I'm still in the dark about the core of my question. I understand from all the replies that it's NOT a good idea to user Mint to run a server, but the question is still WHY? Is it just that Mint installs too much "crap" by default? From what I understand, people are saying that Mint has too much "stuff" but not that it lacks any particular thing. So, maybe a better question would be: Other than having stuff you don't need, can Mint or a similar distribution run a server just as readily or does it LACK anything that a server-centric distro has?

Don't get me wrong, I'm not dead set on using Mint to run a mail server, I'm simply interested in the whys and whats and hows of linux as a beginner.

Its a not so great idea because: the support is not going to be there. If you want to set up an Ubuntu server there is a lot better support available than if you were to try to build a mint Linux server.  Not that it can't be done....    If you are good with linux and have an understanding of what needs to be done you can do it, it just won't be as easy.

---

### Post by SunnyRabbiera on 2008-03-11
Mint is more for desktops then servers, in theory yes you can probably use Mint on a server but it is not really meant for it.
Debian or even BSD are more suitable for servers.

---

### Post by HermanAB on 2008-03-11
As for why:
Server distros (Eg. RedHat, Mandriva, Suse) have many server related configuration wizards making setting up server functions a snap.
Desktop distros (Eg. Mandriva, Suse, Ubuntu) have many desktop related confguration wizards making setting up desktop features a snap.

Further, server distros include precompiled packages for all server functions and desktop distros include packages for all desktop functions.

For example, if you wish to use Redhat as a desktop system, then you'll have a very hard time getting multi-media features to work and you'll likely end up spending weeks compiling MP4 codecs, Mplayer and VLC.  While if you wish to use Ubuntu as a server, then you may have to compile RADIUS or some other special server from source code.

If you cannot make up your mind as to what exactly you wish to do on a machine, then you may be better served by a 'fat' distribution such as Mandriva or Suse, which include wizards and packages for practically everything, instead of trying to force a 'lean' distro into the wrong usage mode.  

Many questions on these forums are from people trying to set up FTP, Samba, DNS or Mail servers and spending many hours (even days) doing it manually, while with Suse or Mandriva it can be accomplished with a few clicks of a mouse.

Cheers,

Herman

---

### Post by forrestcupp on 2008-03-11
HermanAB had some good thoughts.

Distros are just basically a kernel with a bunch of software added.  Any distro *can* be used as a server.  Some distros come already with all of the software and settings needed to run a server but not a desktop and others focus on packaging a lot of software to run a desktop instead.  It's easiest to pick the package that works for you, but you can modify any distro to do the job if you really want to put extra work into it.

Using Linux Mint for a server is kind of like buying a 2 seater Porche and a station wagon, and modifying the Porche's body to work for a family, then modifying the station wagon to be a race car.

---

