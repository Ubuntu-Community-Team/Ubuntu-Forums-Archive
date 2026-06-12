---
title: "Firefox and Video"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by bowler802 on 2007-12-23
Just installed 7.10 very new to Linux when using Firefox can't get websites that use video to work. I have installed the plug ins when prompted for example You Tube I can see the video but it's real slow and my CPU is at 100% (gnash process?) Computer is frozen until video is done.

Any ideas why so many have issues with Firefox? I run Firefox in windows with no issues? 

Running AMD 2000+
Radeon 7000
512MB ram

---

### Post by RIchard James13 on 2007-12-23
In Microsoft Windows Firefox will be using the Adobe Flash plugin. Under Ubuntu you appear to have the gnash Flash plugin installed. You need to remove that and install the Adobe Flash plugin to get video working properly. 

First go into the Synaptic Package Manager

From the top menus go System->Administration->Synaptic Package Manager
You will have to enter your password
When synaptic loads click on the search icon
In the search dialog enter 
flash plugin
This will list all the packages that match a similar description
Next to each package is a square a green square means that package is installed
To install a package right click on the square and from the pop-up menu choose "Mark for installation"
To remove a package right click on the square and from the pop-up menu choose "Mark for removal"

Remove all the gnash ones and install the flashplugin-nonfree one.

Once you have marked them for install or removal you need to click the apply button to make the system apply your changes.

When the process of installation and removal is complete close synaptic and restart firefox. Try the movies again. On the movie your should right click and a menu should come up that will include the line "About Adobe Flash Player 9..." if that is there then you have successfully installed Adobe Flash.

---

### Post by rgb1701 on 2007-12-23
> **bowler802 said:**
> Just installed 7.10 very new to Linux when using Firefox can't get websites that use video to work. I have installed the plug ins when prompted for example You Tube I can see the video but it's real slow and my CPU is at 100% (gnash process?) Computer is frozen until video is done.

Any ideas why so many have issues with Firefox? I run Firefox in windows with no issues? 

Running AMD 2000+
Radeon 7000
512MB ram

I made several posts in another thread earlier today re: the poor performance of Flash video (which 99% of embedded web page video feeds are nowadays) on Linux.

After testing gOS, Ubuntu 7.10, Xubuntu 7.10, PCLinuxOS, Linux Mint, and Puppy Linux today, I've come to the conlcusion that the Linux Flash web plugin is not optimized for Linux as well as the Windows FLash plugin for Firefox is optimized for Windows.

I did back to back comparisons on two 600Mhz P3 boxes, one with each of the Linuxes listed, and one with XP Pro SP1 with a lowly 8MB Matrox G450 card.  The XP box was butter smooth with Flash video playback at 60%-80% CPU utilization.

THe Linux OS's pegged at 95% CPU and jerky playback, though Puppy Linux was the least jerky and approached usable.

I tested many video cards on Linux- GeForce 2 32MB, Geforce 4 ti4600 128MB, Radeon 9000 64MB, and a GeFOrce FX5500 128MB- none appeared to improve the Flash video performance issue.  But seeing that an 8MB Matrox G450 card plays web video and Java at full speed on the same machine with XP, there is no excuse for Adobe and Sun on this.  A major distro and/or OEM (Dell, HP, etc) need to hammer Adobe and Sun on the FLash and Java port quality for Linux, or hammer the Linux video API projects.

Given the ubiquity and importance of Flash and Java (Java web plugins appear to have the same performance hit on <1Ghz hardware) all over the web, this is a BIG DEAL in the Linux community, and the Adobes/Suns/Linux video API's of the world need to address this performance gap with Xp on lower end hardware.  Moving forward, this kind of hardware will be more common, like the eePc's,  OLPC's, Intel Classmates, and hand held x86 PC's that will be coming soon.

Linux was once touted as breathing new life into old machines, and enabling recycling of this fine hardware, but it appears Linux has suffered from bloat creep, too. :(

But to address the OP's issue- yes, uninstall Gnash and install the official Adobe Flash plugin as described in the other post.

---

