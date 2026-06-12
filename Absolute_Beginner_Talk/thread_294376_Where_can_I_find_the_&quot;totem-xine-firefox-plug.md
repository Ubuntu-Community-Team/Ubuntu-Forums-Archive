---
title: "Where can I find the &quot;totem-xine-firefox-plugin&quot;?"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-11-06
Hello!

I have an Ubuntu v6.10 Operating System (Edgy Eft).

I am trying to locate the package called: "totem-xine-firefox-plugin".

I have not been able to locate it inside the Synaptic.

Can somebody tell me what line to add inside my "sources.list", to be able to locate it?

I think that the above package, enables playing VCDs inside Totem, gxine & Mplayer...

I am able to play DVDs in Totem (by installing "totem-xine"), but not VCDs.
I am able to play VCDs in gxine (by installing "totem-xine"), but with NO audio.

I think installing the package "totem-xine-firefox-plugin" will help me solve this problem.

I have tried installing zillions of other packages with NO success!!!

Unless you have something else to propose, this is my last guess/chance to solve my problem...

Thanks.

P.S.1> Do not suggest me to install "automatix". I do not want to go this way...

P.S.2> Do not tell me that "automatix" was the easiest way for you...
I just want to do it my way...!!! Thanks.

P.S.3> Please respond only if you really know the answer or if you have suggestions other than "automatix". Thanks.

---

### Post by bollix47 on 2006-11-06
There's no sign of that plugin in synaptic on my system either.

Have you tried the totem-mozilla plugin?

---

### Post by dvarsam on 2006-11-06
> **bollix47 said:**
> There's no sign of that plugin in synaptic on my system either.

Have you tried the totem-mozilla plugin?

Thanks for your reply!

Yes, the package "totem-mozilla" is already installed.

But still, I can not play VCDs on my Ubuntu...

Is there any other solution for this, excluding "automatix"?

Thanks.

---

### Post by bollix47 on 2006-11-06
Have you tried [here]("http://packages.ubuntu.com/dapper/web/totem-xine-firefox-plugin").

Just realized your opening post says edgy 6.10 even though your profile still says 6.06.  Sorry.

---

### Post by dvarsam on 2006-11-07
> **bollix47 said:**
> Have you tried [here]("http://packages.ubuntu.com/dapper/web/totem-xine-firefox-plugin").

Just realized your opening post says edgy 6.10 even though your profile still says 6.06.  Sorry.

Thanks for pointing that out!

My actual OS is Ubuntu 6.10!

It seems to me that I forgot to update my profile with my latest Ubuntu Flavor...

Thanks for pointing out...

---

### Post by dvarsam on 2006-11-07
What a big IRONY...!!!

For the first time, I have installed Automatix...

... and it still hasn't done anything to make VCDs play on my Ubuntu...


So, why the heck is Automatix so important/useful, if it can not even make my Ubuntu Edgy Eft play VCDs?

> If Automatix can't do it...

... if no other package can do it...

...The how can I play VCDs on my Ubuntu Edgy?

Any ideas?

Thanks.

P.S.> It seems to me that Ubuntu Dapper was performing much better than Edgy...

---

### Post by localuser on 2006-11-07
Are you trying to play vcd's in Firefox or a stand-alone application?

Perhaps I'm missing something, in which case it would be nice to learn something new, but isn't the totem-xine-firefox-plugin used for playing movies in firefox?

---

### Post by JayTee on 2006-11-07
I'm gonna ask a question which you may have already checked and tried but have you gone into System | Administration | Software Properties and enabled the Universe and Multiverse repositories? They aren't by default and that is probably why you aren't finding the package for Totem-xine-plugin in Synaptic. Once you do this if you go into Add / Remove Programs from the Applications menu you need to click on the Advanced button and after you type the admin password just click on search and type in totem-xine and it should list the player plus the plugins for Firefox. I'm still running Dapper and I noticed just now when I checked that I have Totem-xine 1.4.3 and I don't have the totem-xine-firefox-plugin installed but then I've never tried to play VCDs, only DVDs. The version of the plugin that shows up in the Dapper repositories is only for Totem-xine 1.4.1 so maybe they haven't come out with a new one yet. I noticed a libvcdinfo0 module that xine and vlc use to read VideoCDs. Do you have that installed also? And there is a gxineplugin and the description is here: 

the xine video player, GTK+/Gnome; launcher plugin for Mozilla
This is a GTK+ based GUI for the libxine video player library.
It provides gxine, a  media player that can play all the audio/video formats
that libxine supports. Currently, this includes MPEG1/2, some AVI and
Quicktime files, some network streaming methods and disc based media (VCD,
SVCD, DVD).
A more complete list can be found on [http://xinehq.de/](http://xinehq.de/).   <maybe this site has some info you can use.

This package contains the Mozilla plugin, which is a launcher for gxine.

I'm still too much of a noob to suggest how to find and install an earlier version of the player that might work for you. Sorry if this wasn't much help.

---

### Post by dvarsam on 2006-11-09
> **localuser said:**
> Are you trying to play vcd's in Firefox or a stand-alone application?

Perhaps I'm missing something, in which case it would be nice to learn something new, but isn't the totem-xine-firefox-plugin used for playing movies in firefox?

Dear "localuser",

Thanks for your reply!

I am trying to play VCDs with either of the following programs:

1. gxine

2. KMPlayer

3. Totem Movie Player

4. MPlayer Movie Player


I am NOT trying to play a VCD through Firefox.

From the past (in Dapper), I noticed that I was able to play VCDs with gxine, just by installing the package "totem-xine-firefox-plugin"...
I believe that the above package helps both gxine & firefox.
I do NOT think it is just designed for firefox only...

Thanks.

---

### Post by dvarsam on 2006-11-09
Dear "JayTee",

Thanks for your reply!

> **JayTee]
I'm gonna ask a question which you may have already checked and tried but have you gone into System | Administration | Software Properties and enabled the Universe and Multiverse repositories?
They aren't by default and that is probably why you aren't finding the package for Totem-xine-plugin in Synaptic.[/quote]

From the Menu:

1. I select "System\Administration\Software Sources"


2. I click on the Tab named "Ubuntu 6.10"

And find that I have the following Internet Sources active (checked):

a. Community maintained Open Source Software (universe)

b. Canonical Supported Open Source Software (main

c. Software Restricted by copyright or legal issues (multiverse)

d. Proprietary drivers for devices (restricted)


3. I click on the Tab named "Third Party"

And find that I have the following Sources listed:

a. [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable (main)

b. [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy-plf (free non-free)

c. [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy-plf (free non-free Source Code)

d. [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy (main)

So, from the above info, it seems to me that universe & multiverse are activated...

Am I right?

> 
Once you do this if you go into Add / Remove Programs from the Applications menu you need to click on the Advanced button and after you type the admin password just click on search and type in totem-xine and it should list the player plus the plugins for Firefox.
I'm still running Dapper and I noticed just now when I checked that I have Totem-xine 1.4.3 and I don't have the totem-xine-firefox-plugin installed but then I've never tried to play VCDs, only DVDs.

First of all, _you_ & _me_ are talking of 2 different packages!!!

_You_ are talking about the package named "totem-xine", which is already installed on my Unbuntu Edgy Eft...

...while I am talking for the package named "totem-xine-firefox-plugin", a different package from the one _you_ are talking about!

> 
The version of the plugin that shows up in the Dapper repositories is only for Totem-xine 1.4.1 so maybe they haven't come out with a new one yet.

Well, the package, that is installed on my Ubuntu Edgy Eft machine, is NOT "totem-xine 1.4.1", but "totem-xine 2.16.2-0ubuntu1" (according to the info Synaptic is providing)...

> 
I noticed a libvcdinfo0 module that xine and vlc use to read VideoCDs.
Do you have that installed also?

I noticed that it was not installed on my Ubuntu Edgy Eft.
I went & installed it, only to find out that _none_ of the VCD players I have installed, can really play VCD's on my System...

> 
And there is a gxineplugin and the description is here: 

the xine video player, GTK+/Gnome said:**
> http://xinehq.de/[/url].   <maybe this site has some info you can use.

This package contains the Mozilla plugin, which is a launcher for gxine.

I'm still too much of a noob to suggest how to find and install an earlier version of the player that might work for you. Sorry if this wasn't much help.

I have already installed the package you mentioned, gxineplugin version 0.5.7-1ubuntu6 (according to the info Synaptic provided)...

Still, nothing works...

"Totem Movie Player" prints the following Error:

[quote]Totem could not play this media (Video CD) although a plugin is present to handle it.
You might want to check that a disc is present in the drive and that it is correctly configured.

"Gxine 0.5.7" can play the VCD, but with NO sound!!!

"KMPlayer" can play the VCD, but with NO sound also!!!

"MPlayer Movie Player" prints the following Error"

> Error opening/initializing the selected video_out (-vo) device.

What do I do?

Any ideas?

Thanks.

---

### Post by localuser on 2006-11-09
What's your hardware?  And which version of 6.10 are you running (ppc, 64-bit)?

By the way, have you tried VDR which has a VCD plug-in.  I've never tried it myself so I may be way off-base but the VCD plug-in caught my eye.

---

### Post by JayTee on 2006-11-09
Dvarsam, sorry none of the info helped. Like I said I'm still a bit of a noob at this and while I'd installed Edgy on another machine I'd mostly messed with it on video issues to do with my widescreen and pretty much given up on it for awhile. I'd forgotten that the Package manager has a slightly different look to it than Dapper has. I've been doing some digging around for your particular problem but haven't found anything so far that looks applicable. If I do I'll post another response here in the next few days. Sorry I couldn't be more help. Maybe someone else here on the forums could step in and contribute some ideas?

---

### Post by cvmostert on 2006-11-11
I have the same problem with edgy and VCD,

BUT... I have managed to play n VCD with mplayer (not my first choice) 

what i had to do is put the disk into my other drive to make it work..

I still get some audio error, but at least the vcd plays fine after just clicking ok.

strongs.

---

