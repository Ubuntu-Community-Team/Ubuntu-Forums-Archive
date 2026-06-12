---
title: "netbook worthy distros"
date: 2013-02-16
forum: Any Other OS
---

### Post by kabukiM0n0 on 2013-02-16
Hey there!

I run Kubuntu on an Acer Aspire One netbook and it feels as if the more time that passes, the distro get's slower and slower. 
With a fresh install it runs like lighting - now it doesn't even play video properly without the image completely lagging out, windows take forever to open ... 

So here's the thing, I'm tried of this happening. Of course with a netbook and 1gb ram - I can't really be asking for much right? 
I looked into possible options of other distros that are supposed to be worthy, solid and efficient on netbooks, but I don't really know much - other than the standard - Ubuntu - Kubuntu ... 
So I would like your opinion on something that will continuously run efficiently, not loose it's 'umpfh' after time. Then try myself what you guys recommend. 

The recommendations are listed as follows. 
Eeebuntu
OpenGeeeU
Mandriva
Puppy Linux
OpenSuSE 11
gOS Cloud
CrunchEee
Slax
Debian
Fedora

I got them all from [this (]("http://www.techrepublic.com/blog/10things/10-solid-linux-distributions-for-your-netbook/729")site, where they have a small explanation - but it could take forever to try each one as this netbook is my only system. Any other distro that work well on netbooks are more than welcome of course. 

What I use my comp for.
Mainly writing, reading, browsing, small bit of downloading, music (Guayadeque), videos. Nothing too overly complex. 
Something that looks nice, is editable (to certain extent) has different program options and mainly and most importantly runs when I tell it to run and does what it has been told, so endless hours are not spend trying to find out what the problem is - if there even is one to start with. 

Thank you for all and any help.

---

### Post by snowpine on 2013-02-16
First of all, that list is terrible, it's a few years out of date and some of those distros are obsolete.

Second, there is no need to necessarily switch distros---you can simply install a lightweight desktop such as Xfce or LXDE as described here:

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

Personall I run Fuduntu (Gnome 2 desktop) on my netbook (Asus EEE 900ha with 1.6ghz Atom, 1gb RAM, and 160gb HDD). It's fine for a one-thing at a time, non-multitasking, non-multimedia machine. I have a more powerful desktop and laptop that I use for most tasks.

Hope that is helpful. :)

---

### Post by cwsnyder on 2013-02-16
Do you have a swap partition installed?  With 1G RAM, you should have a 1G swap partition installed unless you have a flash drive as your main drive.

Also, what is your drive free space?  Have you run the terminal command: ```
sudo apt-get autoclean
```

The main reason for netbook specific distros in the first case was the limited hard drive space available on the first netbooks.  If you have Ubuntu (unity) or Kubuntu (KDE) installed on an 8G or smaller drive, you were asking for problems in the beginning.  In that case, **read the hardware requirements for the specific distro before you install it.**  If you have 40G or more hard drive space, you probably have too many programs running at once, too many tabs open in your browser, or too much loading at startup for your 1G RAM.

---

### Post by snowpine on 2013-02-16
I'm not a KDE user but I've heard rumors one of the reasons it can be slow on sluggish hardware is due to services such as "nepomuk."

[http://nepomuk.kde.org/](http://nepomuk.kde.org/)

If you are attached to KDE then explore whether you can turn off some of these services. The system monitor or terminal commands such as 'top' are invaluable for figuring out what is gobbling up your resources. :)

---

### Post by kabukiM0n0 on 2013-02-16
> **cwsnyder said:**
> Do you have a swap partition installed?  With 1G RAM, you should have a 1G swap partition installed unless you have a flash drive as your main drive.

Also, what is your drive free space?  Have you run the terminal command: ```
sudo apt-get autoclean
```

The main reason for netbook specific distros in the first case was the limited hard drive space available on the first netbooks.  If you have Ubuntu (unity) or Kubuntu (KDE) installed on an 8G or smaller drive, you were asking for problems in the beginning.  In that case, **read the hardware requirements for the specific distro before you install it.**  If you have 40G or more hard drive space, you probably have too many programs running at once, too many tabs open in your browser, or too much loading at startup for your 1G RAM.

Yup, 1gb swap partition. 
180GB free out of a 240GB drive - From past experience it **does** start running slow once the 100GB mark is dropped. 
36GB partition specifically for system files.
Start-up programs are set to load just the basics - so exactly that doesn't happen. 
And neither are there too many programs, or tabs open - as I do the same with a fresh install and runs just as smoothly. So why should it be any different after time?  

Also, I'm starting to notice many people say very similar things about KDE - that slowly after time, the distro becomes slow. 

Oh, and yes, I've run the command.

---

### Post by kabukiM0n0 on 2013-02-16
> **snowpine said:**
> I'm not a KDE user but I've heard rumors one of the reasons it can be slow on sluggish hardware is due to services such as "nepomuk."

[http://nepomuk.kde.org/](http://nepomuk.kde.org/)

If you are attached to KDE then explore whether you can turn off some of these services. The system monitor or terminal commands such as 'top' are invaluable for figuring out what is gobbling up your resources. :)

It's on my system, but I've never used it before - thanks I'll look into it.

---

### Post by Frogs Hair on 2013-02-16
I would consider Peppermint.  
[http://peppermintos.com/](http://peppermintos.com/)

---

### Post by kabukiM0n0 on 2013-02-16
> **Frogs Hair said:**
> I would consider Peppermint.  
[http://peppermintos.com/](http://peppermintos.com/)

Very nice, thank you. Looking into it.

---

### Post by Zill on 2013-02-16
kabukiM0n0:  I have been running CrunchBang (statler) on a Acer Aspire One D260A netbook for a while now without any problems.  Very quick and reliable considering the mediocre spec of these netbooks!

I have just upgraded the netbook to the latest [CrunchBang]("http://crunchbang.org/about/") (waldorf) and, so far, it's looking good. :-)

You need to appreciate that CrunchBang may seem slightly more "techie" than some other distros, and it helps if you know how to use a few terminal commands.  However, on the plus side, it is a very lean and efficient OS but still with lots of goodies included by default, such as multimedia etc.

---

### Post by oldos2er on 2013-02-16
Moved to Other OS/Distro Talk.

---

### Post by KBD47 on 2013-02-16
KUbuntu can run OK on a netbook if you turn off effects and under appearance setting set for low CPU. I would recommend Xubuntu  or Mint Xfce if you want something a bit snappier. You could just add the Xubuntu desktop to your Kubuntu install. Gnome Fallback is also quick on a net book and can be added from the software center. Just log out and log into the installed desktop.

---

### Post by offgridguy on 2013-02-16
Just wondering, is it possible to add more ram, on the acer netbook?

---

### Post by VinDSL on 2013-02-16
> **Frogs Hair said:**
> I would consider Peppermint.  
[http://peppermintos.com/](http://peppermintos.com/)
+1

That's what I use on my Eee PC netbook, and USB thumb drives.

Flies like the wind!


[INDENT]**[COLOR="Sienna"]ASUS Eee PC 1000HD (circa 2009) / Peppermint Two OS (Lubuntu Fork) / Conky 1.8.0 / ConkyWX 0.7.9[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-eeepc-17-feb-2013-1(650x381).png[/IMG]]("http://vindsl.com/images/vindsl-eeepc-17-feb-2013-1.png")[/INDENT]


I was listening to Dubstep on Guayadeque when I took this screenie.

Please note the RAM usage...  ;)

---

### Post by drawkcab on 2013-02-17
I like Ubuntu but with the unity 2d in 12.04.  Here are some others worth trying on that hardware:

xubuntu
lubuntu
linux mint debian edition (xfce)
bodhi

---

### Post by kabukiM0n0 on 2013-02-17
> **offgridguy said:**
> Just wondering, is it possible to add more ram, on the acer netbook?

No, at least there is no easy way to do it. It has no hatch for memory. Maybe if you took it apart there *might* be an extra slot. My old netbook didn't have a memory hatch but once taken apart (once it died) there was an extra RAM slot. 

But taking it apart is not recommended, unless of course you know what you're doing.

---

### Post by kabukiM0n0 on 2013-02-17
> **VinDSL said:**
> +1

That's what I use on my Eee PC netbook, and USB thumb drives.

Flies like the wind!


Please note the RAM usage...  ;)


Just installed this - and my oh my,  does it fly like the wind!! 

-

Even though I must say. Snowpine mentioned nepomuk earlier in the thread. Well, after installing peppermint - as said; lighting fast speed - I installed kajongg - failed to read what it installed along side it, nepomuk was one of them and that speed instantly fell out the window. 

> **KBD47 said:**
> KUbuntu can run OK on a netbook if you turn off effects and under appearance setting set for low CPU. I would recommend Xubuntu  or Mint Xfce if you want something a bit snappier. You could just add the Xubuntu desktop to your Kubuntu install. Gnome Fallback is also quick on a net book and can be added from the software center. Just log out and log into the installed desktop.

I had the effects turned off - yet there was still unknown processes killing my CPU. Xubuntu I haven't really given a chance, tried it long time ago when I was an uber linux noob. Might give it another chance. 
Gnome fallback was what I used before moving onto KDE, it does run a fraction quicker than KDE but all the bugs and problems with customization, personally I prefer KDE, even with it being that fraction of a second slower.

---

### Post by tartalo on 2013-02-17
Upgrading to KDE 4.10 is worthy of considertation too, since it comes with a lot of performance improvements (For example, Nepomuk was completely redesigned)

[http://www.muktware.com/5194/kde-410-review-time-switch-kde](http://www.muktware.com/5194/kde-410-review-time-switch-kde)

---

### Post by kabukiM0n0 on 2013-02-17
> **tartalo said:**
> Upgrading to KDE 4.10 is worthy of considertation too, since it comes with a lot of performance improvements (For example, Nepomuk was completely redesigned)

[http://www.muktware.com/5194/kde-410-review-time-switch-kde](http://www.muktware.com/5194/kde-410-review-time-switch-kde)

Is that what comes with Kubuntu 12.10? because I recall installing 12.10 the first time and wouldn't run properly on the netbook - so I fell back to 12.04 and think I was running KDE 4.9 - can the KDE version be upgraded without moving to 12.10?


On another note - I've been seeing a lot of favorable comments about OpenSUSE with KDE or Gnome desktops. 
What is the difference between running Gnome/KDE on Ubuntu/Kubuntu and running it on OpenSUSE?

---

### Post by tartalo on 2013-02-17
> **kabukiM0n0 said:**
> Is that what comes with Kubuntu 12.10?
No, it's even newer.

> I fell back to 12.04 (...) can the KDE version be upgraded without moving to 12.10?

Yes, using backports PPA:
```
sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by PryGuy on 2013-02-17
Give [Point Linux]("http://pointlinux.org") a try ;)

---

### Post by kabukiM0n0 on 2013-02-17
> **Zill said:**
> kabukiM0n0:  I have been running CrunchBang (statler) on a Acer Aspire One D260A netbook for a while now without any problems.  Very quick and reliable considering the mediocre spec of these netbooks!

I have just upgraded the netbook to the latest [CrunchBang]("http://crunchbang.org/about/") (waldorf) and, so far, it's looking good. :-)

You need to appreciate that CrunchBang may seem slightly more "techie" than some other distros, and it helps if you know how to use a few terminal commands.  However, on the plus side, it is a very lean and efficient OS but still with lots of goodies included by default, such as multimedia etc.

It looks good, minor issue though - I've used openbox once before and found it extremely hard to understand. 



> **PryGuy said:**
> Give [Point Linux]("http://pointlinux.org") a try ;)
The .iso doesn't download. Apart from that looks pretty sweet.

---

### Post by PryGuy on 2013-02-17
> **kabukiM0n0 said:**
> The .iso doesn't download. Apart from that looks pretty sweet.
What do you mean? You get a broken download or you can't start download at all? I recommend using direct links and a third party app in first case.

---

### Post by kabukiM0n0 on 2013-02-17
> **PryGuy said:**
> What do you mean? You get a broken download or you can't start download at all? I recommend using direct links and a third party app in first case.

No, the download starts - 0MB/1GB and the time goes up to how long it will take to download, then after a few moments it auto-cancel's itself. 

I've tried from the download page and also the direct download links - they all do the same thing.
Absolutely no idea why, nothing else does that when downloaded.

---

### Post by PryGuy on 2013-02-17
> **kabukiM0n0 said:**
> I've tried from the download page and also the direct download links - they all do the same thing.
Absolutely no idea why, nothing else does that when downloaded.
Well, it can be a server problem, I'll dig logs to see what happens.
I can recommend you one thing, copy a direct link you're going to download, then open a terminal and type there:
```
wget -c file.iso
```
Paste the link instead of 'file.iso'. The -c switch will continue download if the connection breaks.

---

### Post by Hylas de Niall on 2013-02-17
> **Zill said:**
> kabukiM0n0:  I have been running CrunchBang (statler) on a Acer Aspire One D260A netbook for a while now without any problems.  Very quick and reliable considering the mediocre spec of these netbooks!

I have just upgraded the netbook to the latest [CrunchBang]("http://crunchbang.org/about/") (waldorf) and, so far, it's looking good. :-)

You need to appreciate that CrunchBang may seem slightly more "techie" than some other distros, and it helps if you know how to use a few terminal commands.  However, on the plus side, it is a very lean and efficient OS but still with lots of goodies included by default, such as multimedia etc.

+1 for Crunchbang. I've been using Waldorf on my old MSI Wind since November, and before that it was Statler.
I've tried MANY others on this little netbook, but i keep coming back to #!.
It really does fly! ...and really isn't all that hard for a 'noob' to configure (I managed it, and i'm about as tech-savvy as a tot!).

;)

---

### Post by kabukiM0n0 on 2013-02-17
> **Hylas de Niall said:**
> +1 for Crunchbang. I've been using Waldorf on my old MSI Wind since November, and before that it was Statler.
I've tried MANY others on this little netbook, but i keep coming back to #!.
It really does fly! ...and really isn't all that hard for a 'noob' to configure (I managed it, and i'm about as tech-savvy as a tot!).

;)

Okay, go on then. I've read up a bit about Waldorf and to be honest with you - it does sound pretty dam appealing. 
One thing I did read said this: ```
Nothing breaks if the user sticks primarily to debian squeeze (stable)
``` I'm assuming this means sticking to things that are 'debian squeeze' - so not installing programs from other distros. 

Think I'm ready to give it a try.

---

### Post by snowpine on 2013-02-17
Debian Stable Squeeze = CrunchBang 10 "Statler"
Debian Testing Wheezy = CrunchBang 11 "Waldorf"

However, Statler is no longer being supported by the #! developer, so you might as well start with the slightly-unstable Waldorf and track it to Stable sometime over the next few weeks/months (no action on your part required to do so).

---

### Post by PryGuy on 2013-02-17
kabukiM0n0, I've added torrent downloads to [the site]("http://pointlinux.org"), hope this helps.

---

### Post by PhilGil on 2013-02-17
I had an EEE PC netbook for a few years, with a single-core Atom processor and 1GB of RAM. The reality is that Atom processors were built for efficiency and long battery life, and there isn't much you can do to turn them into powerhouses.
 

 During the time I had my netbook I tried a lot of different distros: Peppermint, Crunchbang, LMDE and Debian (with Gnome 2, XFCE and LXDE desktops). In my experience, the differences in speed were marginal. What made a lot more difference was the programs I chose to run – lighter weight programs (think AbiWord instead of LibreOffice writer) improved my experience immeasurably. I kept coming back to a plain vanilla Debian Squeeze install, with a Gnome2 desktop. Squeeze XFCE was fine, too, but more fiddly to set up and not noticeably faster or lighter on resources on my machine.
 

 PryGuy's new distro actually sounds like a good choice (even though his self-promotion is a bit annoying). Debian Wheezy (which should go stable very soon) plus the Mate desktop  will give you an experience much like my favorite Debian Squeeze + Gnome2 setup. Wheezy + XFCE or Gnome fallback would also be worth a try.

---

### Post by Megaptera on 2013-02-17
> **Hylas de Niall said:**
> +1 for Crunchbang. I've been using Waldorf on my old MSI Wind since November, and before that it was Statler.
I've tried MANY others on this little netbook, but i keep coming back to #!.
It really does fly! ...and really isn't all that hard for a 'noob' to configure (I managed it, and i'm about as tech-savvy as a tot!).

;)
Me too also as well - really pleased with it & learning from it too :P

---

### Post by kabukiM0n0 on 2013-02-17
> **Megaptera said:**
> Me too also as well - really pleased with it & learning from it too :P
  
It is fantastic!! Ive been wandering around the Live CD for a few hours now. 
One minor issue - maybe someone can help me here. 
When I install everything goes fine - until the system is installing, half way through I get an error apt configure failed, followed by grub-pc failed to install into /target/

Ive looked around but can only find workarounds for Statler and 64bit. Nothing for Waldorf 32 bit

---

### Post by mamamia88 on 2013-02-17
Distro is irrelevant it comes down more to Desktop Environment and App Selection more than anything really.   Use a lighter weight desktop environment like xfce or lxde and use lighter alternatives to what you would normally use.

---

### Post by snowpine on 2013-02-17
> **mamamia88 said:**
> Distro is irrelevant it comes down more to Desktop Environment and App Selection more than anything really.   Use a lighter weight desktop environment like xfce or lxde and use lighter alternatives to what you would normally use.

mamamia88 and I are in agreement for once. ;) You can get the "best of both worlds" by simply:

```
sudo apt-get openbox
```

or

```
sudo apt-get lxde
```

and so forth

on your existing Ubuntu install. :)

---

### Post by Zill on 2013-02-17
> **kabukiM0n0 said:**
> ...When I install everything goes fine - until the system is installing, half way through I get an error apt configure failed, followed by grub-pc failed to install into /target/...
This is possibly due to a bad download.  Did you check that the md5sum for your downloaded file exactly matches the md5sum on the appropriate [download page]("http://crunchbang.org/download/")?
```
md5sum xxx.iso
```

If the md5sum is correct then it may be worth preparing your USB stick again [as per the #! instructions]("http://crunchbang.org/forums/viewtopic.php?id=23267").

This *may* not be relevant in this case but I always connect up a computer to my router with an ethernet cable while installing a new system.  At some stage during an installation the installer often wants to connect to the internet and having an ethernet connection that "just works" avoids any problems!

---

### Post by KBD47 on 2013-02-17
Peppermint looks impressive, installing now :-)

---

### Post by kevdog on 2013-02-18
To kind of rehash what everyone else said -- you just need a lightweight DE.

Hell I'd just install a basic Arch setup and roll with xcfe or openbox.  That's pretty light weight -- however if your wed to the apt packaging system, it aint going to cut it.

---

### Post by mamamia88 on 2013-02-18
> **kevdog said:**
> To kind of rehash what everyone else said -- you just need a lightweight DE.

Hell I'd just install a basic Arch setup and roll with xcfe or openbox.  That's pretty light weight -- however if your wed to the apt packaging system, it aint going to cut it.

+1 what he said  if you are willing to take the time to set it and are able to read instructions and not just skim you'll have a system perfectly tailored to your desires.

---

### Post by kabukiM0n0 on 2013-02-18
> **kevdog said:**
> To kind of rehash what everyone else said -- you just need a lightweight DE.

Hell I'd just install a basic Arch setup and roll with xcfe or openbox.  That's pretty light weight -- however if your wed to the apt packaging system, it aint going to cut it.

Arch does sound cool - but I can't figure my way around CrunchBang (all the manual installations that are needed) from the little I know about Arch - the understanding needs are much superior.

---

### Post by kabukiM0n0 on 2013-02-18
For now though - I am going to stick with Peppermint 3, it fits for what I need my system for, is fast and efficient. And as such, will label this as solved. 


Thank you all for your great input and advice!

---

### Post by Zill on 2013-02-19
> **kabukiM0n0 said:**
> Arch does sound cool - but I can't figure my way around CrunchBang (all the manual installations that are needed)...
I am pleased that you are happy with Peppermint 3 but I am puzzled by your comment about CrunchBang.
> **kabukiM0n0 said:**
> ...What I use my comp for.
Mainly writing, reading, browsing, small bit of downloading, music (Guayadeque), videos. Nothing too overly complex...
Everything you mentioned here is installed in a standard default installation of CrunchBang - no "manual installation" required. ;-)

What do you need to manually install that isn't a simple "sudo apt-get install" away?

---

### Post by kabukiM0n0 on 2013-02-19
> **Zill said:**
> 
Everything you mentioned here is installed in a standard default installation of CrunchBang - no "manual installation" required. ;-)

What do you need to manually install that isn't a simple "sudo apt-get install" away?

Well - I attempted to install Waldorf but for some unknown reason it wasn't installing apt compiler and then grub-pc failed to install somewhere (I cannot remember the exact location it said) so the installation wasn't complete. 
After hours of help on the forums we basically gave up. 
Where I proceeded to install Statler - which installed perfectly fine. But there was no wireless, sound, SD cards (and maybe a few other things) which after reading around a bit - they have to be 'manually installed' i.e through the terminal. And this is no walk in the park. 

I have heard that this is known, in older versions of CrunchBang, but seeing as Waldorf refuses to install on my system - I'll stick with Peppermint for now. 
One extra note; Even though it proved a huge headache, what I did get to see of #! was amazing!!

---

### Post by Zill on 2013-02-19
> **kabukiM0n0 said:**
> ..Where I proceeded to install Statler - which installed perfectly fine. But there was no wireless, sound, SD cards (and maybe a few other things) which after reading around a bit - they have to be 'manually installed' i.e through the terminal. And this is no walk in the park...
Sound worked out-of-the-box when I installed Statler on my Acer Aspire One D260-A.  Maybe your volume control was set at minimum.

Enabling wifi [(BCM4313)]("http://wiki.debian.org/brcm80211") required just three terminal commands...
```
sudo -i
apt-get install firmware-brcm80211
modprobe -r brcm80211 ; modprobe brcm80211
```

The built-in SD card reader (ENE UB6250 - 0cf2:6250) did not work with Statler due to no kernel support.  However, I understand that this has been introduced with some later kernels but I have not yet checked this with Waldorf.

If you do get Waldorf working then enabling wifi requires slightly different commands:
```
sudo -i
aptitude install firmware-brcm80211 wireless-tools
modprobe -r brcmsmac ; modprobe brcmsmac
```
Not *particularly* arduous IMHO ;-)

---

### Post by shiv1499 on 2013-02-19
> **kabukiM0n0 said:**
> Hey there!

I run Kubuntu on an Acer Aspire One netbook and it feels as if the more time that passes, the distro get's slower and slower. 
With a fresh install it runs like lighting - now it doesn't even play video properly without the image completely lagging out, windows take forever to open ... 

So here's the thing, I'm tried of this happening. Of course with a netbook and 1gb ram - I can't really be asking for much right? 
I looked into possible options of other distros that are supposed to be worthy, solid and efficient on netbooks, but I don't really know much - other than the standard - Ubuntu - Kubuntu ... 
So I would like your opinion on something that will continuously run efficiently, not loose it's 'umpfh' after time. Then try myself what you guys recommend. 

The recommendations are listed as follows. 
Eeebuntu
OpenGeeeU
Mandriva
Puppy Linux
OpenSuSE 11
gOS Cloud
CrunchEee
Slax
Debian
Fedora

I got them all from [this (]("http://www.techrepublic.com/blog/10things/10-solid-linux-distributions-for-your-netbook/729")site, where they have a small explanation - but it could take forever to try each one as this netbook is my only system. Any other distro that work well on netbooks are more than welcome of course. 

What I use my comp for.
Mainly writing, reading, browsing, small bit of downloading, music (Guayadeque), videos. Nothing too overly complex. 
Something that looks nice, is editable (to certain extent) has different program options and mainly and most importantly runs when I tell it to run and does what it has been told, so endless hours are not spend trying to find out what the problem is - if there even is one to start with. 

Thank you for all and any help.

Currently I have one netbook which runs Ubuntu 12.04(desktop version) just fine. This has been observed by me as well that the system goes slow in about 3-4 months after a number of updates have been installed but still its not as slow as windows. Also uninstalling applications(not in use) may help. Try installing 64 bit ubuntu which is much faster as almost all the netbook harware supports 64 bit.

---

### Post by kabukiM0n0 on 2013-02-19
> **Zill said:**
> Sound worked out-of-the-box when I installed Statler on my Acer Aspire One D260-A.  Maybe your volume control was set at minimum.

Enabling wifi [(BCM4313)]("http://wiki.debian.org/brcm80211") required just three terminal commands...
```
sudo -i
apt-get install firmware-brcm80211
modprobe -r brcm80211 ; modprobe brcm80211
```

The built-in SD card reader (ENE UB6250 - 0cf2:6250) did not work with Statler due to no kernel support.  However, I understand that this has been introduced with some later kernels but I have not yet checked this with Waldorf.

If you do get Waldorf working then enabling wifi requires slightly different commands:
```
sudo -i
aptitude install firmware-brcm80211 wireless-tools
modprobe -r brcmsmac ; modprobe brcmsmac
```
Not *particularly* arduous IMHO ;-)


Dam! well .. it's not really *that* complex when you put it like that. 
Does it matter that the netbooks are different versions?, or does the same codes apply for all Acer Aspire One?
I'll save that for when I do give #! another try.

---

### Post by Zill on 2013-02-20
> **kabukiM0n0 said:**
> ...Does it matter that the netbooks are different versions?, or does the same codes apply for all Acer Aspire One?...

My netbook is an Acer Aspire One D260-A and I understand that their are several different models of the Acer Aspire One series.  In order to get the wifi working, you need to establish the installed network controller.  The following code should show exactly which controller is installed:
```
lspci
```
My D260A shows the following:
> 02:00.0 Network controller: Broadcom Corporation [COLOR="Red"]**BCM4313**[/COLOR] 802.11b/g/n Wireless LAN Controller (rev 01)
If your netbook has the same BCM4313 controller then the commands given in post [#42]("http://ubuntuforums.org/showpost.php?p=12518904&postcount=42") should work fine for you.

If you have a different controller listed with lspci then I suggest you do a quick search for the appropriate Debian documentation.

If you have any problems just post back here with the exact Acer Aspire One model number *and* the output from the lspci command.

---

### Post by Zill on 2013-02-20
> **Zill said:**
> ...The built-in SD card reader (ENE UB6250 - 0cf2:6250) did not work with Statler due to no kernel support.  However, I understand that this has been introduced with some later kernels but I have not yet checked this with Waldorf...
I have just tested the SD card reader on the Acer Aspire One D260-A running CrunchBang Waldorf and can confirm that SD cards now work perfectly, automounting when plugged in and can be easily unmounted graphically via Thunar. :-)

---

### Post by kabukiM0n0 on 2013-02-20
> **Zill said:**
> 

If you do get Waldorf working then enabling wifi requires slightly different commands:
```
sudo -i
aptitude install firmware-brcm80211 wireless-tools
modprobe -r brcmsmac ; modprobe brcmsmac
```

Managed to get Waldorf up and running, probably using dd helped.
I ran your commands to start with and they failed. Yet I tried something that was on a debian page and then ran them again and it worked. Also the SD card wasn't worked and now it does. 

Cheers man!!

---

### Post by Zill on 2013-02-20
> **kabukiM0n0 said:**
> Managed to get Waldorf up and running, probably using dd helped.
I ran your commands as wireless isn't being recognized

This is the response I recieved...
Crunchbang includes a post-install script that installs many useful extras after installing the main system.  This script starts automatically after installing and, if you run the script, it starts by updating all the packages.  If you did *not* run the script then you really should update all installed packages in the usual way:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
The error you have shown *could* be due to the system not being fully updated so I suggest you run these two commands asap.

I note that you now have wireless working - but without these packages I really do not know how!

If you open the Synaptic Package Manager you can easily see what is (and is not!) installed.

ps. I would also recommend *not* mixing aptitude and apt-get as this has caused problems in the past (possibly now fixed!).  IMHO it is best just to choose one and stick to it to avoid any potential problems.

---

### Post by kabukiM0n0 on 2013-02-20
> **Zill said:**
>  I would also recommend *not* mixing aptitude and apt-get as this has caused problems in the past (possibly now fixed!).  IMHO it is best just to choose one and stick to it to avoid any potential problems.

I've pretty familiar with apt-get but aptitude is still a hit and miss. One thing I have noticed is that on most debian sites they use aptitude instead of apt-get. Is it as simple as changing aptitude for apt-get and the following command or is there more too it?

Also - I see there is no equivalant on debian of Ubuntu-restricted-extras and most debians tend to do this themselves - How do I find out what unofficial sources I need and how to get them?

Is it as simple as using debgen and adding what it recommends into /etc/apt/sources.list?

---

### Post by Zill on 2013-02-20
> **kabukiM0n0 said:**
> I've pretty familiar with apt-get but aptitude is still a hit and miss. One thing I have noticed is that on most debian sites they use aptitude instead of apt-get. Is it as simple as changing aptitude for apt-get and the following command or is there more too it?...
Personally, I just stick with apt-get but my understanding is that if you would rather use aptitude then the syntax, particularly for installing packages, is very similar.  Check the man pages for further info:
```
man apt-get
man aptitude
```
> **kabukiM0n0 said:**
> ...Also - I see there is no equivalant on debian of Ubuntu-restricted-extras and most debians tend to do this themselves - How do I find out what unofficial sources I need and how to get them?...
One reason I like CrunchBang and Linux Mint is that both these distros include all this "extra" functionality as standard.  I can't think of any "unofficial sources" I would need!

---

### Post by kabukiM0n0 on 2013-02-20
Okay found it all, was just a thing of becoming a little familiar with where I was walking. 
Thank you very much for the help - seriously!

---

### Post by Zill on 2013-02-21
You're welcome. :-)

---

### Post by mamamia88 on 2013-02-21
> **kabukiM0n0 said:**
> I've pretty familiar with apt-get but aptitude is still a hit and miss. One thing I have noticed is that on most debian sites they use aptitude instead of apt-get. Is it as simple as changing aptitude for apt-get and the following command or is there more too it?

Also - I see there is no equivalant on debian of Ubuntu-restricted-extras and most debians tend to do this themselves - How do I find out what unofficial sources I need and how to get them?

Is it as simple as using debgen and adding what it recommends into /etc/apt/sources.list?

the only real difference i've noticed is that aptitude allows you to search packages via the command line ala synaptic. where as apt-get is strictly for adding/removing stuff.

---

### Post by kabukiM0n0 on 2013-02-21
> **mamamia88 said:**
> the only real difference i've noticed is that aptitude allows you to search packages via the command line ala synaptic. where as apt-get is strictly for adding/removing stuff.
Oh, that sounds like a handy command, and definitely worth taking a look into then.

---

### Post by CDR Services on 2013-02-23
> **kabukiM0n0 said:**
> No, at least there is no easy way to do it. It has no hatch for memory. Maybe if you took it apart there *might* be an extra slot. My old netbook didn't have a memory hatch but once taken apart (once it died) there was an extra RAM slot. 

But taking it apart is not recommended, unless of course you know what you're doing.
I have the older 8.9 inch acer aspire one and according to the specs it has 512 megs on the motherboard and 1 ram slot that will accept 1 gig maxing it out at 1.5 gig!  but I have a 2 gig stick waiting in the wings to give it a try when i have occasion to tear it apart again!

---

### Post by cwsnyder on 2013-02-23
Debian is one of the oldest distros and one which takes the software freedoms most seriously, not including by default or making easy to use binary blobs or proprietary software.  The information on the sources is there on the Internet, but some codecs are restricted in some countries, so I will not be responsible for spreading the information here.

---

### Post by chronos0 on 2013-05-17
My favorite: easypeasy 1.6, it doesn´t matter it´s out of date

---

### Post by yeswetran on 2013-05-19
A great article that answers all:
[https://www.linux.com/news/software/applications/708977-the-2013-top-7-best-linux-distributions-for-you](https://www.linux.com/news/software/applications/708977-the-2013-top-7-best-linux-distributions-for-you)
And an even greater one:
[http://www.techradar.com/us/news/software/operating-systems/best-linux-distro-five-we-recommend-1090058](http://www.techradar.com/us/news/software/operating-systems/best-linux-distro-five-we-recommend-1090058)
And if you're into security stuff (like this rookie/noob):
[http://www.serverwatch.com/server-trends/10-secure-linux-distributions-you-need-know-about.html](http://www.serverwatch.com/server-trends/10-secure-linux-distributions-you-need-know-about.html)

---

### Post by VinDSL on 2013-05-19
> **yeswetran said:**
> A great article that answers all:
[https://www.linux.com/news/software/applications/708977-the-2013-top-7-best-linux-distributions-for-you](https://www.linux.com/news/software/applications/708977-the-2013-top-7-best-linux-distributions-for-you)
Er...

Their #1 Laptop pick has been orphaned:  [http://www.fuduntu.org/blog/2013/04/28/project-ends/](http://www.fuduntu.org/blog/2013/04/28/project-ends/)  ;)

---

### Post by mips on 2013-05-20
> **drawkcab said:**
> 
bodhi

I read this and downloaded bodhi, installed it on my laptop and I don;'t see how people can call it lightweight, On a clean boot it ate about 160MB of ram and it was not fast. More show than go.
If you want something lightweight try a openbox distro, plenty of them around, crunchbang, archbang, manjaro etc all all good distros.

---

### Post by binaryhermit on 2013-05-21
I don't see why a lubuntu installaton wouldn't be another option.

---

### Post by jediboaz on 2013-05-24
my wife is using an acer aspire one d270 and have ubuntu ultimate ed 3.5 ([http://ultimateedition.info/](http://ultimateedition.info/)) installed. she
is very happy with it, and is very quick. she played around with the desktop environments, and i see she settled for
xfce.

---

