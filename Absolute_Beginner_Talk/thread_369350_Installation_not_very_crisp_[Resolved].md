---
title: "Installation not very crisp [Resolved]"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Meson on 2007-02-24
I've been playing around with a few distributions over the past few days and I'm liking Ubuntu the most, however it still isn't as clean as WinXP.  I gather from the reading I've been doing that most of this is do to Gnome (and KDE on other distros) being slow, however even boot time is much longer.  The hard drive seems to be clicking a lot more (MAJOR DIFFERENCE).

I feel some of this is do to poor system organization.  On my windows machine I know exactly what is installed, executed at startup, and running at all times.   The directory structure is not redundant like the standard linux style.

Granted my Windows installation is refined from years of use (and reformats), however it can still be tweaked with ease (I don't do anything complicated, just insure the right software is installed and running, with nothing extra running in the background).

Any general tips for improving the performance of the system (the things I do to Windows can all be described as general - I do not like making extremely specific changes).  Maybe this isn't the right distribution for me?  Or in some sense am I just out of luck until Linux support becomes more refined?

---

### Post by shareMenaPeace on 2007-02-24
> **Meson said:**
> I feel some of this is do to poor system organization.  On my windows machine I know exactly what is installed, executed at startup, and running at all times.   The directory structure is not redundant like the standard linux style.
Hi, 
for a start checkout your /home/username (Your "username" when you login),
hit CTRL + H to see "hidden files + folders".

Much is installed here, but basicly when you install things it will be spread in diffrent locations.
First this is irritating but if you need something do a search from the terminal with 

```
locate filename
```

or addd a wildcard to just search parts of a filename with

```
locate filena*
```

or

```
whereis *ilen*
```

And when you manualy install use 

```
sudo aptitude install name
```

Automatic install can be done from

System -> Administration -> Synaptic Package Manager

Here in synaptic is also a good start to search for stuff (Use search function).


> **Meson said:**
> Granted my Windows installation is refined from years of use (and reformats), however it can still be tweaked with ease (I don't do anything complicated, just insure the right software is installed and running, with nothing extra running in the background).
Ok to know what you personal needs are be more specific?
Well there is a TOOL which let you automatic install the most needed stuff like CODECS (mp3 etc), Players most needed tools and all this.

Its accessable from here

[http://getautomatix.com](http://getautomatix.com)

Note it might be down but will be back in around 5 hours.


> **Meson said:**
> 
Any general tips for improving the performance of the system (the things I do to Windows can all be described as general - I do not like making extremely specific changes).  Maybe this isn't the right distribution for me?  Or in some sense am I just out of luck until Linux support becomes more refined?
Well to help you with this you might want to post your system specs.
MAybe you are low on RAM which is essential for performance, and if your ubuntu experience lack if you eg have just 192 RAM than you could try XUBUNTU.com a ubuntu version designed for low performance systems.

But i guess you fine and well maybe start special topics for each problem you encounter, after you searched the forum as the most common things are answered allready.
When you search type the device name and model number.
```

ATI RADEON XYZ23.w
```

Cheers

---

### Post by aysiu on 2007-02-24
There are some ways to tweak performance. You may also want to try [a lighter desktop environment like XFCE](http://www.psychocats.net/ubuntu/xfce) or even just [a window manager like IceWM.](http://ubuntuforums.org/showthread.php?t=263710)

Here's one thing you can do--turn off some unnecessary services. This may decrease your boot time *and* better your performance by installing BUM and using it.

From the terminal (the easy way): ```
sudo apt-get update
sudo apt-get install bum gksu
gksudo bum
``` Wait a minute or two for it to load up, then uncheck any boxes you don't want.

If you prefer to install things the point-and-click way, read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by irish_flu on 2007-02-24
Hey buddy,

For starters (and don't take this the wrong way) it seems like one of your biggest complaints about Ubuntu is that you're more familiar with Windows.  Don't fret, use it awhile and I think you'll quickly become accustomed to the way Linux works.

What (specifically) seems slow to you in Gnome?  In my personal experience, it runs a lot faster than Windows XP does on similar hardware.

There are a WHOLE LOT of tweaks you can do for performance, I'm not even sure how to tell you where to start.

There are also a lot of tweaks to speed up boot-time, namely turning off services you don't need (and it sounds like you're familiar with doing that in Windows).  If you search around these forums and elsewhere, you'll find a lot of advice on that.

One easy performance tweak you can check out is turning off system-wide IPv6 support.  This should improve the speed of doing network and internet-related stuff (assuming you don't need IPv6, most of us don't).

There are instructions for that here:
[http://ubuntuforums.org/showpost.php?p=1942241&postcount=6](http://ubuntuforums.org/showpost.php?p=1942241&postcount=6)

One other question, what do you mean when you say the filesystem is "redundant"?  I'm just not sure what you're talking about (specifically).

Also, if you tell us the specs of the hardware you're using we might be able to help you make performance tweaks in more specific ways.

---

### Post by SeanTater on 2007-02-24
You are a newbie to Linux, it seems. We appreciate your comments, but such general statements to help linux continue to change and improve, please be more specific so that constructive changes can be made in the appropriate places.

In relation to the most specific examples you gave, what do you find the most redundant about the file structure, and are you /sure/ it's really slower to start up? Many comments have been made both ways..

---

### Post by Meson on 2007-02-24
Thanks Everyone.

I'm running a Dell Latitude D800 with a Pentium M 1.7 GHz and 2 gigs of ram.  Video is a geforce go5650.

Yes, I said I was a newbie to linux as a desktop environment but I do have quite a bit of experience with just about everything else computer related.  So I am more used to windows but I think if I set down a complete outsider in front of my computer and booted into windows and then into gnome, he would definitely say my windows xp setup feels cleaner.

My problems with the directory structure is that you have things like /bin, /usr/bin, /usr/local/bin, /sbin, et cetera (spelled out to avoid confusion =P)  And I'll admit, I'm intimidated by all the lib* files floating around everywhere.  I just think there should be a very rigid standard on where things are supposed to be located in the filesystem and where symbolic links should be (I'd like it if there was a /apps/ directory and a /bin/ directory with only symbolic links to the apps.

And I know there are tons and tons of tweaks to be done, but I think ideally that things like this are dangerous.  You lose track of obscure changes you've made and they are hard to reproduce on new systems.

In respect to my hard drive seeming more active in Ubuntu.  Would anyone recommend I try FAT so I can defrag it when I think I need to?

---

### Post by Aazn on 2007-02-24
> **Meson said:**
> My problems with the directory structure is that you have things like /bin, /usr/bin, /usr/local/bin, /sbin, et cetera

The average user should not be poking around in directories; the Package Manager and the Gnome Menu should be all that you need. If you are poking around, that is a sign thta you think or do know a bit about computers. If you do, then you should at least take the time to learn how files are organized. I will be the first in this thread to mention that [b]there are no "hidden registry" entries in Ubuntu, there aren't any "hidden services" or "phone home software" lurking under Ubuntu.

You say that GNOME boots slower. If you'll notice, a good chunk of time is spent pre-configuring network before you login, so no matter who logs in, networking is ready. You could probably disable this. The time that I've saved using Synaptec Package Manager instead of crawling the web trying to find a Windows application more than makes up for the slightly slower boot time. The fact that when I install an application I don't have to reboot anymore also saves me time. This "GNOME is slower than Explorer" argument barely plays out; it might be quicker to initialize, but it is full of holes anyway.

> **Meson said:**
>  I just think there should be a very rigid standard on where things are supposed to be located in the filesystem and where symbolic links should be (I'd like it if there was a /apps/ directory and a /bin/ directory with only symbolic links to the apps.

Why would you make an /apps directory when you already have /bin? If you took the time to learn the new filesystem organization which is standard in **all** Linux-based operating systems, not just Ubuntu, then you wouldn't be as confused. I admit, it took time to adjust to Linux's file organization, but it took time to learn Windows too?

> **Meson said:**
> In respect to my hard drive seeming more active in Ubuntu.  Would anyone recommend I try FAT so I can defrag it when I think I need to?

It's only active because you're doing more things. An operating system can only use it more because it's doing things in the background such as downloading. If you sit still with both operating systems for longer than a minute, you'll see they both rarely use the hard drive. 

I also strongly reccomend you stay with ext3, as it **automatically defrags itself** in the background so you aren't stuck defragmenting like in Windows.

---

### Post by Maestro23 on 2007-02-24
Good post Aazn and everyone for that matter.  Just want to add this link for the OP on Linux File structure.

LinuxCommand.org: [http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)

---

### Post by Meson on 2007-02-24
I am going to spend some time now going through Synaptic (is there any garuntee that have a packages installed that aren't listed here, or I have packages listed that aren't installed - is there any audit mechanism?)

Meanwhile can someone tell me how to get my scroll wheel to work.  I can click a link with it but the scrolling feature is not working.

---

### Post by aysiu on 2007-02-24
Any package you have installed will be listed in Synaptic. You can also get more packages available by enabling extra repositories. I'd advise reading this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

To understand the file structure, read this:
[http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html](http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html)

I don't know anything about getting scroll wheels to work (never had a problem with mine), but someone else may be able to help you if you post the model # and brand.

---

### Post by Meson on 2007-02-25
Ok, I have to come clean.  I was on VMWare :-# (In my defense though I had a WinXP virtual machine which seemed to run fine)

The point is however, I went to an all out dual boot (a process which took only about half an hour + the time it took to back up my data) and I'm thrilled.  Ubuntu is extremely snappy and efficient.

I'm humbled and sorry I had my doubts.

---

### Post by Maestro23 on 2007-02-25
> **Meson said:**
> Ok, I have to come clean.  I was on VMWare :-# (In my defense though I had a WinXP virtual machine which seemed to run fine)

The point is however, I went to an all out dual boot (a process which took only about half an hour + the time it took to back up my data) and I'm thrilled.  Ubuntu is extremely snappy and efficient.

I'm humbled and sorry I had my doubts.

Just be honest and up front next time.  Good people on these forums were taking their time to try and help you.  This is the best forum for any linux distro I have been a part of.  People here don't mind helping others who really want help, and who are willing to help themselves.

Glad things are working out for you.

---

### Post by rsambuca on 2007-02-25
> **Meson said:**
> Ok, I have to come clean.  I was on VMWare :-# 

[-X 

Actually, Kinda fun though.

---

### Post by Meson on 2007-02-25
> **Maestro23 said:**
> Good people on these forums were taking their time to try and help you.

Damn, I didn't even consider that.  I actually feel bad now.  As a payback I pledge to be the New Jersey Ubuntu head cheerleader for at least one month.

---

### Post by rsambuca on 2007-02-25
Meson, you may as well edit your original post and flag it as "Resolved";)

---

