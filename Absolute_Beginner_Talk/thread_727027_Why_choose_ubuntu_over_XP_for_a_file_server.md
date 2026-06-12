---
title: "Why choose ubuntu over XP for a file server?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Landsharkk on 2008-03-17
Hey all,

First of all I'm not a complete advocate of linux or windows, I'm on the fence, but most of my experience (a good 95%) is with windows.  I'd like to consider using a version of linux for my next project.

Basically, I'm going to be needing a file server to host both media and backup files and will need to be able to remotely monitor/access this box as it will not have a monitor once it's setup. 

What I need answered is: why should I install ubuntu rather than xp or vista for this file server/media share computer?  

One stipulation will be that it needs to be able to serve media through windows media center or something that works with (and will be recognized by) other media devices such as my xbox 360.

Can anyone shed some light on the subject?  Thanks!

---

### Post by Anzan on 2008-03-17
Windows needs a video card even if the server is headless. The design is fundamentally busted. I wouldn't trust it enough to put a coffe cup on top of the box.

Ha ha ha.

Have you considered Mythbuntu?

---

### Post by Wobedraggled on 2008-03-17
Windows:

 + Will be an easier way to connect to XB360 for streaming
 - More Overhead (hardware req's)


Linux:

 +Can use a headless setup, even leave out a user interface all together
 -Not sure of streaming to 360 there are options but I have not explored them.

---

### Post by Calash on 2008-03-17
Linux is going to give you superior remote control capabilities, almost out of the box.  SSH and VNC are both great utilities to control a system with no display.  I use SSH -X myself, but that is from another Ubuntu box.

I also find that my Ubuntu system is more stable over long periods of activity, like weeks or months online.  Reboots are mostly due to upgrades than actual need.

For the same level of configuration and custom ability, you would have to look at Windows Server 2003, not XP.  With Ubuntu you get Server and Workstation capabilities on the same disk.

---

### Post by Oldsoldier2003 on 2008-03-17
Licensing costs. Xp isnt a real server but if you run a real server you need to consider licensing costs. Ubuntu has none, Windows does.

Windows does have a plus in that its easier to administer because of the Gui.. it's also a lot easier to run a windows server in a mixed windows/linux environment. Its also inherently less secure than linux

Ubuntu on the other hand is harder to set up and configure, but is inherently more secure out of the box than a fully tweaked windows server. Sad but true...  The tools for Ubuntu are mostly command line based and the gui tools that have been developed are not complete.

The bottom line is that if your organization has deep pockets and is heavily invested in windows, a windows server is probably what you want, unless you are willing to learn linux and spend some time integrating an Ubuntu server with your existing network. EIther solution is viable, its just a matter of choice.

For a home user, I'd say use Ubuntu, you'd be crazy to spend money for the licenses on a windows server. And if you weren't... well thats not a topic of legal discussion in these forums  :lolflag:

---

### Post by Nythain on 2008-03-17
why not choose ubuntu over xp for a file server...
do you really need the bloat of xp just to serve files... seems a bit extreme...
xp slows down the longer it runs (at least in my and many other users experience) while linux will keep on chugging, only using what it needs when it needs it.

it really is all going to boil down to what you prefer... if you want to get some linux experience under your belt then set up ubuntu

if you want to stick with the familiar, then for the love of god, at least consider windows server 2003...

i can tell you windows will more than likely be easier, but with ease comes unecessity... ubuntu will be a bit more complicated, especially seeming so to anyone unfamiliar with linux to begin with... there will be difficulties, errors, problems, etc... but all of them can be overcome with the help of these forums and google

i've set up a few file/media servers using ubuntu (though i've never streamed to an xbox360, could be an issue but im sure its a possibility, specially if its modded at all *note, i do not condone modding, nor am i recomending modding in any way shape or form, please dont give me another freaking warning about this behavior, im just stating facts here*)

once you get past the samba hurdle, its all downhill :)

---

### Post by Landsharkk on 2008-03-17
Thanks for the replies so far, much appreciated!

I should mention that the cost of XP is irrelevant, as I already have a copy installed on the box and it will be needing to be rebuilt when I get this home project going.

I will have other windows pc's on the same network that will be interacting with the file server/media share.  I don't now much about Ubuntu or how well it integrates with other windows systems on the same network, but it appears that it wouldn't be a big issue.

I'm ok with using a command line based system.  My goal is to 'set it and forget it' once this thing is all installed.  I suppose I put a higher value on uptime than on ease of use.

Thanks again for the comments and please keep 'em coming!

---

### Post by Oldsoldier2003 on 2008-03-17
> **Landsharkk said:**
> 

I'm ok with using a command line based system.  My goal is to 'set it and forget it' once this thing is all installed.[COLOR="Red"]  I suppose I put a higher value on uptime than on ease of use.[/COLOR]

Thanks again for the comments and please keep 'em coming!

then thats your answer. Ubuntu Server

---

### Post by dca on 2008-03-17
...hmmm, you need to call MS and find out if using WinXP outside it's design warrants the purchase of a CAL or puts you in non-compliance.  I always thought the MC vers of XP allows you to run a complete media center but if you're using a Windows product on a client/server basis (where the Win box hosts files) a CAL is req'd.  I know it's being anal but, hey, how do you think they make all that money...

---

