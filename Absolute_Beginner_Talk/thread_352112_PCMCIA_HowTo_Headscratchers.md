---
title: "PCMCIA HowTo Headscratchers"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by .plaid on 2007-02-02
Howdy.

I'm trying to get my 2011B LAN PC Card to work, so that I can get online (like at a Starbucks or something) and start accessing the wonderful repositories I've heard so much about.

I've downloaded pcmcia-cs-3.2.8.tar.tar and both spectrum24t-1.03*.tar.gz files and (after much machination) managed to to complete the first step under Installation: unpack to /usr/src.

I understand the value of permissions, but it was a might annoying to give permissions for /usr and then have to give the same (no, different!) permissions for /src. I am the user of /usr and in the group of /src? **Is there a way to effect changes to all subfolders for something like this? Or a smarter way in general?**

But my point: I have unpacked this thing to that folder (sorry - file - like everything else in Linux) but I cannot find anything that smells of the directions in step 2: run "make config" in the new [directory]." **I see a Makefile text file, but no Makeconfig or the like.** 

Is this like my old college math class where the professor skipped a few operations between lines because everybody knew how to get from A to B? I recognize that this is like trying to eat an elephant after growing up on broccoli soup, but logic suggests there'd be some suggested logic to this.

Thanks humbly in advance for your slow-talking-detailed-with-graphs-and-arrows replies.

Best regards,
.

---

### Post by K.Mandla on 2007-02-02
A couple of things come to mind: First, the pcmcia-cs package in [Dapper]("http://packages.ubuntu.com/dapper/base/pcmcia-cs") and [Edgy]("http://packages.ubuntu.com/edgy/base/pcmcia-cs") is already v3.2.8, so judging by your signature, you're already up to date there. It should be installed by default, unless you removed it.

Second, you might want to look over these pages. ...

[http://www.ubuntuforums.org/showthread.php?t=237944](http://www.ubuntuforums.org/showthread.php?t=237944)
[http://www.ubuntuforums.org/showthread.php?t=296430](http://www.ubuntuforums.org/showthread.php?t=296430)
[http://www.ubuntuforums.org/showthread.php?t=87227](http://www.ubuntuforums.org/showthread.php?t=87227)

I've never worked with that card, so it's impossible for me to tell. But it seems like you'll need both the driver and the firmware for the chipset of that card, and there's both good news and bad news.

[http://sourceforge.net/forum/forum.php?thread_id=712833&forum_id=181499](http://sourceforge.net/forum/forum.php?thread_id=712833&forum_id=181499)

Looks like it's possible to get it working, but some of those pages are so old that they're expired. Keep your eyes peeled.

---

### Post by .plaid on 2007-02-03
Thanks, K.mandla, for the direction.

I am so accustomed to downloading, then installing, then running applications that I spent a good half hour scouring my desktop and drop-down folders for an app named ndiswrapper or the like. I eventually learned that it is simply called in a Terminal command line. Sheesh.

Today, however, my keyboard is acting goofily (both '0' and '[' keys when clicked show up as '[0'; 'y' and '7' are paired together, as are 't' and '4'...it's kinda wierd). Getting my password - let alone general commands - entered correctly forced me to install ndisgtk and load drivers that way. Neither wl50nd5.inf nor NetWlan5.inf gave me love, though I haven't yet modified the boot module to include ndsiwrapper. Point of fact, I'm not entirely sure that I blacklisted any existing drivers. One headache at a time, eh?

So, I'm not sunk yet. I'm going to fix this keyboard issue then begin anew.

Happy Superbowling, all.

.

---

