---
title: "Installing/ upgrading xubuntu on 400Mhz iMac?????"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by shgadwa on 2008-04-26
I have a few questions....Xubuntu 6.06 works great on my 400Mhz imac, 512MB ram computer. It also works decently well on a 333Mhz imac, 96MB ram (which I sold for $30.00). 

However, EVERY SINGLE TIME I try to upgrade the os, something happens, like it deletes the kernel and cannot reload it properly...usually something is messed up with the xserver-xorg (GUI). If I restart, an error pops up and I then have to restart my computer. Because it does not upgrade it all right for some reason. It also, is not that all the apps are not upgraded, they are.

I cannot install xubuntu 8.04 or even 7.10 as with 7.10, I get the loading screen (where it says xubuntu) and it says there, doing nothing for 5 minutes then goes to a command line. Xubuntu 8.04 does not work because after installing, I get a blank screen shortly after booting

Another question I had it, I have installed java using synaptic, however it still does not work in firefox for some reason. I also need adobe flash but it does not support ppc for linux. I heard of gnash but does that work as well as adobe?? I tried to install that but there were way too many things missing to do the installation.

Any help would be appreciated.

---

### Post by stream303 on 2008-04-26
> **shgadwa said:**
> However, EVERY SINGLE TIME I try to upgrade the os, something happens, like it deletes the kernel and cannot reload it properly

That's why I generically advocate using the "alternate" images which are non-live and just pure installers, especially on low-mem machines.  Although maybe they have improved the live-cd images for those with a lot of ram - I'm just so used to the "alternates" that I like to reduce the possibilities for errors.  Something to try...

> If I restart, an error pops up and I then have to restart my computer.

What is the error?  If it is related to being dropped down into a busybox shell like it was on Gutsy, there's a cool tip here:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

> Xubuntu 8.04 does not work because after installing, I get a blank screen shortly after booting

I got mine to work by stopping the boot at the second stage boot: prompt, and using

```
Linux nosplash
```

Although yours might need more parameters.  We're in some new territory here, and it still appears that our Apple hardware isn't "hardy-savvy", rather than the other way around. :)

> I also need adobe flash but it does not support ppc for linux. I heard of gnash but does that work as well as adobe??

That's right.  I'm amazed that it works as well as it does.

We're all pioneers at this stage. :)

---

### Post by shgadwa on 2008-04-26
Thank you for your reply. I used the aternate Cds as the live cds never worked...I'd get this kernel panic...not syncing attempted to kil te idle task warning.

After I tried to upgrade 6.06 using either a CD or the internet, it does not do the whole thing completely for some reason and usually either the kernal and/ or the xserver-xorg gets messed up. The warning was something like xserver-xorg not configured properly. I tried to configure it...with no luck.

I would really like to get this upgraded though...But I find too that it seems as if I run kubuntu more than xubuntu. Maybe the newer xubuntu is better.

On ubuntu, how do I get to a command line before the blank screen so I can type that in???

Thanks!

Shawn

---

### Post by shgadwa on 2008-04-26
I need to know how to get to the command ine when it has not booted up yet???

---

### Post by shgadwa on 2008-04-27
I found out how to get to the command line. Now it says command not found. the linux nosplash command does not work....?

---

### Post by CREEPING DEATH on 2008-04-27
Unfortunately, Ubuntu hasn't worked well on PPC machines since 6.06.  I tried it and ended up installing Debian on a similar machine.

CD

---

### Post by stream303 on 2008-04-27
> **CREEPING DEATH said:**
> Unfortunately, Ubuntu hasn't worked well on PPC machines since 6.06.  I tried it and ended up installing Debian on a similar machine.

I beg to differ. :)  On a G5 iMac, with 6.06 you are met with screaming fans, and it was only until Feisty 7.04 that it got fixed without requiring manual intervention.

Everything is relative, so I don't want to turn this into a pointless debian-vs-Ubuntu thread.  There's no need for that as I also run Debian Lenny testing here and both coexist peacefully - as should the users of both distros...

---

### Post by stream303 on 2008-04-27
> **shgadwa said:**
> I need to know how to get to the command ine when it has not booted up yet???

When you first power up, do you get the yaboot prompt in the upper left - which eventually times out and moves on to the second-stage prompt with

**boot:**

If you do nothing here, it will time out and begin to load the kernel.  However, if you hit -tab- here, it will stop the countdown, and allow you to type in special boot parameters.

If you can get yaboot to stop here with a -tab- , try typing 
```
Linux nosplash
```

Or do you not even get any yaboot prompts at the very beginning?

---

### Post by shgadwa on 2008-04-27
Ok......Did that, but linux loaded jsut like it always loaded before....the screen goes black. I can get to a command line like in a computer without a gui, by pressing Control+alt+F1. Then I sign in...It says no resume image..doing normal boot?????

---

### Post by crapple on 2008-04-27
I am having the same problem with ubuntu on an emac powerpc g4 800mhz prosser and about 800mb of ram.

---

### Post by shgadwa on 2008-04-27
I really need to get these computers working....... Is there something else I can try?? Any ideas or should I just load 6.06 and forget upgrading??

---

### Post by CREEPING DEATH on 2008-04-27
> **stream303 said:**
> I beg to differ. :)  On a G5 iMac, with 6.06 you are met with screaming fans, and it was only until Feisty 7.04 that it got fixed without requiring manual intervention.

Everything is relative, so I don't want to turn this into a pointless debian-vs-Ubuntu thread.  There's no need for that as I also run Debian Lenny testing here and both coexist peacefully - as should the users of both distros...
Try it on a G4 with an IDE drive and you get busybox.  It doesn't work without CLI usage every boot or a lot of configuration, and even then it might break upon upgrade.  I know, I did it, and it sucked!  PPC is an unsupported port in Ubuntu, it still has full official support in Debian, which is why I suggest it.  I use Ubuntu, I like Ubuntu, but Ubuntu doesn't support PPCs well and Debian does.
> **shgadwa said:**
> I really need to get these computers working....... Is there something else I can try?? Any ideas or should I just load 6.06 and forget upgrading??
I'd start [here]("http://www.debian.org/ports/powerpc/") and use either Etch (stable) or Lenny (testing).  Lenny currently stays very current, and with 512 MB RAM you could easily run the full Gnome desktop.  It looks very similar to Ubuntu because Ubuntu is based on Debian, and can be set up to use Sudo like Ubuntu does.  And upgrading is fairly easy as well.
Gnash is improving but still lacking, I'm not sure about Java.

CD

---

### Post by stream303 on 2008-04-27
> **CREEPING DEATH said:**
> PPC is an unsupported port in Ubuntu, it still has full official support in Debian, which is why I suggest it.

By all means try it.  I run Lenny-Testing here as well.  Just remember that stable, Debian Etch, may not have as much up-to-date software as you'd like, and is roughly analogous to Dapper.

Debian Lenny-testing is roughly analogous to running Gutsy, so go ahead, since Lenny is still dependent upon the older xorg 7.2 and older xrandr.  Unless you run Debian Sid, you won't be trying out the newer xorg 7.3 like Hardy is.

When Debian goes stable much later this year - maybe - you might be faced with exactly the same situation you are in now as they adopt the newer xorg 7.3, xrandr, etc.  

So go ahead and try it - get whatever works on your box.

> I use Ubuntu, I like Ubuntu, but Ubuntu doesn't support PPCs well and Debian does.

You mean dropping corporate-support and instead being community-supported by devs and developers exactly as what we are trying to achieve here?  The last time I spoke to an Ubuntu dev, they were actively involved with trying to fix an installation issue with the fans - all on their free time, which is exactly what a Debian dev does.

So no, Debian and Ubuntu have exactly the same amount of support, and in fact, I have yet to see a Debian web-based-forum of the caliber of what you'll find right here.

When/if Ubuntu drops the ability to pull down a ppc build from the repos, and shuts down this forum, would be the only time to hint that it isn't fully supported.

It just lacks corporate backing, and is depending on users like you and me to provide support.

---

### Post by shgadwa on 2008-04-27
Well, what I want to do with Linux, is take older computers, mainly these older iMacs as well as G3s and 6500s and put linux on them so that it is current and fast, and sell the computers for a profit, rather than throwing the computers in a landfill........WHAT OS would do great for that???

As fare as other OSes, I have ubuntu on by 400imac currently with the KDE desktop wich works great but lots of things is not upgrded...liek firefox and such. I might jsut reinstall a brand new version of kubuntu then.

Also, Gentoo seems REALLY NEAT but when I tried to install it, it seems like a huge deal and you have to guess at what to type. they have a handbook but its very long and they expect you to know what they do not tell you....has anyone used Gentoo and how do you isntall it?? Is it great or good for slower computers??

Also, I tried setting the date right, as it was set wrong adn I fixed it...I used linux nosplash and also linux nosplash video=ofonly...the ofonly one worked...at least it booted in text but I still get a blank screen. Updating it does not work...furthermore, its 8.04, WHY does it need an update?

Thanks,

Shawn

---

### Post by stream303 on 2008-04-28
> **shgadwa said:**
> has anyone used Gentoo and how do you isntall it?? Is it great or good for slower computers??

Gentoo is great for PPC.  You definitely become a bit more intimate with the install process, and with a low-spec machine, you'll be waiting around for compilations to finish - but time is something you willingly sacrifice since you will know your system down to the last nut and bolt.  Some might say that compiler optimization may not net you that big of a speed improvement, but then again, using Gentoo is not just about speed - like Ubuntu, you have a great community, and it has it's own unique focus.

Things seem a little rough right now for some ati card machines, but hang in there.  We'll find the right kernel parameters at some point, look back at these threads and laugh. :)

---

