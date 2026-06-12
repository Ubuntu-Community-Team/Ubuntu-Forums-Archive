---
title: "overall impessions and Media issues w/ ibook G3 600"
date: 2005-01-25
forum: Apple PPC Users
---

### Post by Darksev on 2005-01-25
Wanting to get familar with linux/macOS after this last year in the PC world (I'm an PC tech for a US Retailer) I purchased an iBook g3 off a mac buddy of mine. The hardware is fantastic, responsive even under panther, and damn slick looking. My first linux experience was Yellow Dog 4.0, and the install was reletivly painless overall. I ran into, of course, one of the main YDL bugs. lack of sound. After a week or so of playing around, I decided that I needed something with audio, so I tried a few other distirbutions. Mandrake PPC (10.1) has some severe issue with my bootstrap partition, and this trend continued even after a complete wipe of all partitions, and recreation with drakdisk or whatever they call it. 

Gentoo was definately not designed for utter noobs like me. about halfway (i think? it made my head spin) through what I think was the install, one of the packages on my disc failed install (corruption during DL). Not wanting another headache, I started looking around again, and found Ubuntu.

I had never seen an installation go so smoothly. I didn't have to really do anything. All said and done it booted right up, into Gnome (which I have come to love more than KDE) WITH SOUND and Airport working! YAY! Firefox was already installed, thunderbird (with a bit of clicking) was installed, with none of the hassle they gave me in YDL. 

now we get to the problem.

Playing any kind of media crashes the application I attempt to play it in. Audio CD's dont play (no supprise, I had read here that there are issues), MPG and WMV will cause this: 
*This Window ________ is not responding, forcing this application to quit will cause you to lose any unsaved changes* 
in Mplayer, opening the radio streams (or any streams I add) will cause the same error

I looked at installing something like XMMS, but, as I said earlier, I'm a complete noob when it comes to these things. 

browsing around here I saw a few threads about fixing issues with Mplayer, so I followed the steps [here](http://www.ubuntuforums.org/showthread.php?t=94) to no avail. the very first option, the terminal update commands generate this:

Reading Package Lists... Done
Building Dependency Tree... Done
Package autoconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package autoconf has no installation candidate

as does every other command. I saw somewhere here that I can sudo apt-get install XMMS and I get the same text as above. 

any ideas as to how I can get some from of multimedia playback working? Mplayer, audio streams, XMMS installed, anything. thanks in advance.

EDIT
-----------------------------------
Figured out my issues. needed to add some extra sources to my synaptics manager, everything worked after that. MP3 playback, everything!

---
Sev

---

### Post by dubdubdub on 2005-02-10
Can someone direct me to a media-how-to thread. When I put ubuntu on my x86 getting media to work was for the most part effortless. I can't get this iBook to play flash movies, quicktime, mpegs, anything.

I would run OS X on this but for some crazy reason this machine will not run a mac os whatsoever. I have never seen a mac that can't run a single mac os...it isn't even a mac anymore. I won't get into the weeks of repair attempts on this thing...

---

### Post by funkyade on 2006-04-04
[QUOTE=dubdubdub]Can someone direct me to a media-how-to thread. When I put ubuntu on my x86 getting media to work was for the most part effortless. I can't get this iBook to play flash movies, quicktime, mpegs, anything.

I would run OS X on this but for some crazy reason this machine will not run a mac os whatsoever. I have never seen a mac that can't run a single mac os...it isn't even a mac anymore. I won't get into the weeks of repair attempts on this thing...[/QUOTE]

I run ubuntu ppc on a similar machine. I advise searching the forums here for advice as it has helped me greatly in the past.

I have flash (with the free flash player), and you can get mpegs and quicktime by installing the appropriate packages. Just make sure you have enabled all the different kinds of repositries in your /etc/apt/sources.list file or do the same using synaptic or adept.

You may want to download and burn the latest dapper ppc install CD, this fixes the majority of the most annoying bugs with mac hardware. [http://cdimage.ubuntu.com/releases/dapper/flight-6/](http://cdimage.ubuntu.com/releases/dapper/flight-6/)

hth

---

