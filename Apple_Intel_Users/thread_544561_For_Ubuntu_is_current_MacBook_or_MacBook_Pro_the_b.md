---
title: "For Ubuntu is current MacBook or MacBook Pro the better purchase?"
date: 2007-09-06
forum: Apple Intel Users
---

### Post by offthewall on 2007-09-06
Hi all,

I am about to purchase either the current generation MacBook or MacBook Pro.

One of the main things I want to do is to be able to dual boot Ubuntu and OS X.

In this regard, which hardware choice would be better?

Any advice would be greatly appreciated.

Thank you.

-offthewall

P.S. I am an experienced OS X user, but a complete novice at Ubuntu.

---

### Post by undead-monkey on 2007-09-06
Well, simply put, do you want a bigger screen and graphics card, or a smaller more stylish form factor (though slightly slower)?

---

### Post by themacmonk on 2007-09-06
I would agree with the previous post and it depends on what you want from the MAC.  If you plan on doing a lot of audio, video or graphics editing then the go for the Pro as it has a dedicated graphics card to handle the screen "redraws" when editing in such programs.

I'm using a MacBook 2.0Ghz and installation was a breeze and I'm much like yourself, an experienced Mac user and a novice to Ubuntu.  Just about everything worked right off the bat and other things I learned to eventually tweak through the forums.  The nice thing about Ubuntu and Macs are that Macs are pretty much the same across the board so it makes troubleshooting and updating that much easier as opposed to  PC's where each manufacturer and sometimes each model has it's own dedicated user groups because the system architecture can vary.

Good luck!

---

### Post by offthewall on 2007-09-06
> **undead-monkey said:**
> Well, simply put, do you want a bigger screen and graphics card, or a smaller more stylish form factor (though slightly slower)?

> **themacmonk said:**
> I would agree with the previous post and it depends on what you want from the MAC.  If you plan on doing a lot of audio, video or graphics editing then the go for the Pro as it has a dedicated graphics card to handle the screen "redraws" when editing in such programs.

Yes, those are valid points, and I had pretty much decided on the MacBook Pro because I would like a 15 inch screen and firewire 800. 

However when I realized that I will want to run Ubuntu, and began some introductory reading, I discovered there are a lot of differences between internal components between MacBook and MacBook Pro and even between the different revisions of each model. Some of the internal components (e.g. sound card, graphics card, wifi card, touchpad, etc) allowing functionality with Ubuntu off the bat and some needing quite a bit of tweaking, or even impeding full functionality with Ubuntu.

So to clarify, the reason for my post here at ubuntuforums is to discover whether the specific hardware component innards of the 2.16GHz Intel Core 2 Duo MacBook versus the Santa Rosa MacBook Pro will make installing and running Ubuntu significantly easier on one versus the other.

To partially answer my own question, it seems that the older models need less tweaking of the software to get full functionality. However, I had hoped to get the latest model (its been 3 years since I upgraded to my current PowerBook 12 inch, so I crave the latest and greatest)

So, any thoughts as to which of the current models will be easier to get up and running with Ubuntu? Or would I be wise to choose an earlier revision?

> **themacmonk said:**
> I'm using a MacBook 2.0Ghz and installation was a breeze and I'm much like yourself, an experienced Mac user and a novice to Ubuntu.  Just about everything worked right off the bat and other things I learned to eventually tweak through the forums.  The nice thing about Ubuntu and Macs are that Macs are pretty much the same across the board so it makes troubleshooting and updating that much easier as opposed to  PC's where each manufacturer and sometimes each model has it's own dedicated user groups because the system architecture can vary.

Yes, it seems that the earlier MacBooks (and especially the core duos) need a whole lot less tweaking.

I would welcome any perspectives on the MacBook vs MacBook Pro buying decision specifically from the point of view of ease of getting Ubuntu up and running.

Thanks for your input and suggestions.

-offthewall

---

### Post by cyberdork33 on 2007-09-07
As far as hardware compatibility, I would say the Macbook is easier. There are still issues with WiFi on the newer models though.

Unfortunately there is a lag in linux support of new hardware since it has to actually be released to the public before developers can even get their hands on it to develop drivers and whatnot. In addition, Apple tends to use the latest and greatest hardware they can find when they release a new machine. This causes problems in the linux world because this hardware is untested. On top of that, much of Apple hardware that is generally the same across the board (Take the ATI cards for instance) and working in linux, always seem to be just a little bit different than the PC versions, causing some issues. These are usually a quicker fix though. All this is fine under OSX since Apple has access to the information needed to make it compatible. For this reason, generally, older hardware will be more compatible. The Santa Rosa machines are still a bit difficult to get working 100%, although lots of solutions have been posted in this forum. Hopefully, many fixes will be integrated into Gutsy.

The Intel Video devices in the Macbooks are very compatible with linux because Intel has open drivers.

---

### Post by tehkain on 2007-09-07
My macbook is new as of monday. I cleaned out OS X(tho leaving it around with refit is easy enough) and had to do almost no mandatory tinkering. 

What I have done thus far is typical:
I loaded gutsy since I am a tester and I find it wonderful*. Once in I modded my Xorg with the touchpad config found on the macbook ubuntu wiki. I used xmodmaps to make my right apple and right small enter button function as right click and delete. After that I tried the madwifi drivers, I found that they do not work for me due to a dhcp issue, then instead I used ndiswrapper which only required one command. So it really only took me five minutes to get the pc up and running fully**. The PC runs like a dream. It is the 2.16ghz super drive model.

All in all I am happy that I am running almost fully open source on a macbook and once I get my madwifi driver working I will rejoice.

* It requires a usb keyboard to install since the macbooks keyboard is not detected during livecd boot
** Oh and my webcam works(thanks to this forum) but gstreamer has a bug that should be getting fixed.

---

