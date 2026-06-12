---
title: "Hardware config questions? (general)"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Blue_Horseshoe on 2007-12-12
Hi guys, I've been playing with ubuntu 7.10 on my laptop (hp dv8309us) for about a month. I've tinkered around with getting things like my ati and broadcom cards to work, pretty good learning experience! Anyways, to the heart of my questions. 

Is there some systematic way for me to detect all my hardware and check to see if it is functioning properly? (is this what i'm doing when i do a "lspci -n", how can i use the data from lspci to achieve my goal?)

Is there a way that once I have some piece of hardware locked in and working to save/store the settings/drivers so **when** (not if) I break my install I can revert to my last good settings, something like a custom install cd with what i've done so far?? i dunno?? ideas.

I've installed ubuntu countless times and have a notebook with how to make some of the hardware work but having to do it all manually time and time again is getting a bit old. (perhapses someone has a link to a script writing tutorial and I could script the process of reconfiguring my working settings)

I know some people are going to come on here and say "Well heck, if it's functional and you major issues wifi and gfx work leave it alone" and I can totally understand why you would say somthing like that but i rather enjoy the tweaking hacking and LEARNING i get by messing things up. Thats why I dumped XP,I want to get in there and get my hands dirty, understand whats going on inside the box!

sorry about the windy post, but it's my 1st one, so give me a break :guitar:



I would also like to thank all you crazy smart fools who have solved so many issues for others on this forum, this place was my safety blanket / cornucopia of knowledge that got me this far.

---

### Post by p_quarles on 2007-12-13
The easiest way to see all your hardware is to use:
```
sudo lshw
```
This will give you a full rundown on every piece of hardware recognized by the kernel, whether it's currently working or not. Pieces of hardware that are not functioning will be designated as "unclaimed."

The biggest shortcuts for restoring your ATI card functionality would be to save a copy of /etc/X11/xorg.conf to a CD/Flash card, as well as saving whatever tools you used to install the driver (whether it was Envy, the driver itself, etc.). If you installed it without help from a script, I would also write down a step-by-step list of instructions for my future self. 

I have no experience with NDISwrapper/fwcutter, but I'm guessing that it too has a configuration file which would be useful to store externally. Again, any scripts you used, and any step-by-steps that might be helpful. 

If you'd like to write a script to automate these processes, you should be able to do that pretty easily as well. I'd recommend taking a look at chapter 2 of the [Bash Guide for Beginners]("http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html"). 

Again, I do think the most important thing here is to save copies of the relevant configuration files. That'll allow you to plop in your old settings instantaneously.

---

