---
title: "New life for PowerBook G3?"
date: 2008-11-14
forum: Apple Hardware Users
---

### Post by snoble on 2008-11-14
I must love pain!

I have a really OLD PowerBook G3, 64 MB ram (yes -just 64MB) and a 4MB drive.
What on earth can I load on here to make it work? I do NOT have an OS on it and YES, I'd like a Linu version.

What variant (if any) of Ubuntu, Xubuntu etc might I consider? What limitations do I face regarding internet use? Should I just leave it on the sidewalk for someone to find? (ROFL)

What a challenge! BTW - I'm a noob too!

---

### Post by bryonak on 2008-11-14
EDIT:
Whoops, I completely ignored that we're talking about PowerPC processors here...
You will have to use the [alternate install CD]("http://cdimage.ubuntu.com/ports/releases/intrepid/release/") anyway with these...




Newer GNOME and KDE releases are out of question with such a machine.
You can choose between Xubuntu and Fluxbuntu.

XFCE is more lightweight than GNOME/KDE while offering almost all the features. You can download Xubuntu 8.10 at xubuntu.org
Still it might be too heavy for your system.

Fluxbox is definitely very lightweight, but you might miss features you have grown accustomed to, since it has quite a different feel from XFCE/GNOME/KDE. Best try the liveCD from fluxbuntu.org in order to find out if you like it.
A drawback may be that the last Fluxbuntu release is 7.10, which is a year old by now. I personally prefer the improvements that the newer kernels (especially 8.10) provide for laptops.


Still Fluxbuntu will be more responsive than Xubuntu on your system, while both Fluxbox and XFCE are available in the Ubuntu 8.10 repositories.
So what I would do is install 8.10 from an alternate install CD and install the latest stable Fluxbox. Then again, the drawback of this is that it requires some work.


These are the three options I can offer you, each with its own drawback.
Of course the sidewalk is a fourth possible solution... but could you please make sure it's the sidewalk outside of my house, let's say tomorrow at 6pm? ;)

---

### Post by stream303 on 2008-11-14
My all-time favorite docs for exactly what you are doing:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Even though the introductory paragraphs talk about Intel, the docs work just fine for ppc.

Essentially, what you do is install a command-line system first.

Then you add your software repos and do an update.

Then you choose to add the X server.  If you like, you can also add something like GDM for automatic login, or you can continue to bring up X from the commandline with startx.  Your choice.

Pick a window manager.  You can keep it light with say Fluxbox, or maybe a little heavier with XFCE4.

Now toss in some apps like the epiphany browser, abiword, etc.

If you can, try and use commandline apps, like vorbis-tools etc for a little audio playback / streaming bling if the gui apps slow you down.

A text editor will be your friend, so you'll probably start out with nano as the editor.

The frustration level may be high at times, but the rewards are great!  That link above has helped me create 64mb macs that are actually useful, and NOT doorstops!

Have fun!

---

### Post by bryonak on 2008-11-15
If you don't want to fiddle much, I can recommend [DamnSmallLinux]("http://www.damnsmalllinux.org/"), which is based on Debian (like Ubuntu) and is tailored to systems with around 16MB RAM.

Apart from that, the only way to get a modern, fast, stable system on such an old machine is doing something like what stream303 wrote.

There is a huge variety of window managers, here's my personal notes.. it's far from complete (there's about twice as many managers/environments), but that's what I've tried out.
Note that they are all installable via Synaptic/aptitude

```

[heavy and newbie-friendly]

GNOME			popular standard environment
KDE			a bit heavier, more eye candy



[medium weight, average functionality]

XFCE			similar functionality as winxp, quite popular
Enlightenment		extremely customizable and innovative, but in eternal development



[light and fast, but fiddly]

Fluxbox			popular, good looks, quite own "*box" look&feel
Openbox			very lightweight, rather hard to use, "*box" look&feel
WindowMaker		very lightweight, popular in the 90s, very own look&feel
FVWM (-Crystal)		nice eye candy, crystal is friendly (fvwm alone is not)
IceWM			windows look-alike (can be made look like xp and vista)
PekWM			rather young project, looks nice
StumpWM			Ratpoison successor, mouseless, most lightweight!, strange to use


```

---

### Post by mikjp on 2008-11-29
> **bryonak said:**
> If you don't want to fiddle much, I can recommend [DamnSmallLinux]("http://www.damnsmalllinux.org/"), which is based on Debian (like Ubuntu) and is tailored to systems with around 16MB RAM.
But it does not have a version for PowerPC architecture.

I myself use Debian with my iBook that has a 600 MHz CPU and 384 Mb RAM. Works great!

Also Slackintosh might be a good choice.

Or NetBSD's port for PPC architecture.

Mikko

---

