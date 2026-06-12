---
title: "A few notes on trying Fedora 14"
date: 2011-05-01
forum: Any Other OS
---

### Post by decoherence on 2011-05-01
Hi all! First off, sorry if this is not the correct place for this. I justified to myself putting this here as I think that most of the people who would find this post interesting will be reading this particular section of the forum.

Here are a few notes on my recent experience trying Fedora. For the record, I've been using Ubuntu since Warty and before that, Debian since Potato. I have historically steered clear of RPM-based systems, preferring Arch or FreeBSD for an occasional alternative to Deb-based systems.

Just to be clear, my intent is not to proselytize or present either Fedora or Ubuntu as superior. You won't find any opinion in these few notes and as little as possible in the summary at the end.

By the same token, I'm aware that there are a few people complaining about Unity and who may be interested in hearing a few notes about an alternative. Personally, I don't even have 11.04 and my preferred user interface is xmonad/dmenu, anyway.

Finally a reminder that F15 which features GNOME 3 will be released Real Soon Now. As with both Ubuntu and Fedora, things are subject to change and YMMV.

OK on to the notes, which may well seem anti-climactic now due to all my kowtowing.

------

Immediately recognized dual screen setup on desktop computer and automatically created an extended desktop. (nvidia card and, presumably, nouveau drivers)

No obvious way to install nVidia proprietary drivers -- contrast with Ubuntu's Hardware Drivers program.

3D acceleration disabled in Nouveau -- no obvious way to enable and may not be supported.

Tried to open an MPEG4 encoded AVI with Totem. It searched for a suitable codec but was not able to find one. Error dialogue contained a link to a Fedora Project wiki page.

"Unfortunately, the codec you were searching for is not available in Fedora."

The page also contained a link to fedorasolved.org which in turn sent me to rpmfusion.org.

The process for installing RPM Fusion's repositories is to click on the appropriate link on their web page and click OK when the package installer asks for confirmation. The installation of the free repository seemed to finish however the installer program appears to have crashed at that stage. The close button is non-responsive and the close box in the title bar graphically responds but does not function.

The program does not grey out as it might in Ubuntu (tho i'm not able to test whether this program would) nor is a Force Quit dialogue displayed after a period of inactivity. Is this an Ubuntu-specific enhancement to GNOME?

Unsure of which process to terminate, I simply logged out and logged back in. Upon logging back in, the free repository still did not appear to be installed.

Successfully installed both free and non-free repos using the command line instructions on RPM Fusion's page.

Re-opened the MPEG 4 program in Totem and it offered once again to search for a suitable codec. This time it found them immediately and one auth dialogue, a few clicks and a download later and... uhh it still didn't play. But when I closed and re-opened Totem it did.

------

To summarize my experience so far, Ubuntu seems a bit more user friendly but at no point did I feel like I was 'up the creek' with Fedora. The only thing I had to do differently is read through a couple of web pages which Fedora itself pointed me at when it was unable to accomplish what I had asked. Ubuntu seems to do a better job of handling this automatically which is a good thing as Ubuntu documentation doesn't seem to be as cohesive as Fedora's.

This appears to be mostly an idealogical difference. It seems the Fedora project will not do anything to help you install non-free software but it will point you in the right direction. With this in mind, Ubuntu may seem to be a better system for new users who want things to 'just work.' That said, Fedora's excellent docs and the fact that it points you to them means getting non-free stuff running is quite easy. The largest problem, in terms of user experience, is that the RPM Fusion web links to add repositories didn't seem to work, requiring me to resort to the command line (which, granted, was a simple copy/paste. But still... command line! oooOOOoooOOOoooh!) The Fedora Project has no direct control over RPM Fusion.

Anyway, I hope this was useful or at least interesting to someone! Thanks for reading.

---

### Post by ventrical on 2011-05-01
Great read. Have had Fedora for over 6 months now. Rock solid. I did my update to F14 via the Update Manager. Took a while but was seamless. I'll wait until the release of F15 and use the Update Manager to upgrade.

 I had always thought that Fedora had smoother edges while working with compiz and that Flash was overall a lot more lucid and clear than Maveric but now even Unity Interface on Natty Narwhal seems to have corrected the mini 'sawtooths' that were presenting themselves from time to time.

  I haven't had any real problems with Fedora 13 or 14 at all. I do not use it as much as I use Ubuntu but it is always ready to go..  My only complaint was that it seems to have problems with keeping persisitve pendrives working correctly after updates or after switching a pendrive from one PC to another. of course I'll keep trying to get that ironed out,:)

I am trying to teach my ladyfriend how to use Ubuntu 10.10 Netbook and she catches on really fast. One day she came over and I had Fedora desktop up and running and she exclaimed, ' wow .. a brand new computer'.

:)



regards..

---

### Post by overdrank on 2011-05-01
Moved to Other OS/Distro Talk :)

---

### Post by decoherence on 2011-05-01
> **overdrank said:**
> Moved to Other OS/Distro Talk :)

I swear I was looking for a section like that before I convinced myself to post it in Testimonials. I somehow missed it (though there ARE a lot of sections ;) )

Thanks for the catch,

---

### Post by coffee412 on 2011-05-01
I have been using Fedora ever since it came out. I can tell you that its going to be alot different than Ubuntu.  You see, Fedora is a "Bleeding Edge" version of linux. Its the testing ground for Redhat. 

Fedora is also more "Nuts and Bolts" in installing and configuring. But to me there is nothing wrong with that as its usually a very stable system. Infact, Its my prefered right now. 

Ubuntu is probably the first flavor of linux to go after the crowd. Both have their strengths and weaknesses. 

So, You really cant draw a good comparison between the two. Both are great.

Bottom line, Dont expect the click and go with Fedora so much. Sometimes you get down and dirty. 

Enjoy them both!

---

### Post by screaminj3sus on 2011-05-02
My biggest pet peeve with fedora is the font rendering. Still the ugliest font rendering out of the many distro's I've used. I always wanted to like it, I liked that it was bleeding edge and fast, but even with the freetype-freeworld package installed the fonts look horrible to me.

The other thing is even with rpm fusion enabled I found it lacking package-wise, compared to ubuntu/debian/arch it just didn't cut it for me.

At lest they have made huge improvements to the package manager in recent versions. In the fedora 15 beta it was much faster and more stable. I always had issues with yum in previous versions of fedora. And the boot time in fedora 15 beta is incredibly fast.

---

### Post by decoherence on 2011-05-02
I recently tried to install Kdenlive from RPM Fusion. I had to enable the test-updates to actually get the dependencies to resolve. Bummer! Presumably they'll be finished 'testing' them soon, tho.

---

