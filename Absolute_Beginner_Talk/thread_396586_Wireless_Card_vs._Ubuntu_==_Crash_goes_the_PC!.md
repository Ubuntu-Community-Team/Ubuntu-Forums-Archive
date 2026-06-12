---
title: "Wireless Card vs. Ubuntu == Crash goes the PC!"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by LadyLuna on 2007-03-29
Hi there. :3 I'm brand new to linux -- been wanting to try it for years and the comments of several people I know on the ease of Ubuntu and the glory of being free from Microsoft's opressive thumb (etc etc ) finally moved me to get it on my PC.

I am having several problems, but most are small things. There is however one problem that is proving VERY restrictive and VERY serious in today's internet dependent world.

My wireless card.

Oh, I got it working at one point -- god bless ndiswrapper, but, unfortunately it's feeling quite jury rigged because well, I'm crashing left and right.

So, here's the situation rundown:

Wireless Card is a Linksys Wireless G, 2.4 Ghz, USB network adapter. Model Number: WUSB54Gv2

When I initially installed Ubuntu card didn't work, the network menu didn't even provide a wireless option -- I got the drivers off of the CD and used ndiswrapper to get them working for me an initially the card worked splendidly. However, within a few hours it became apparent that there were problems. 

The first I noted was the Internet dropping out. It tended to do this at the beginning of downloads of any real size -- I had this problem while trying to download Amarok and Skype. A quick reboot got the card working again, did my downloads. 

Drop out didn't seem to happen if I was just using GAIM, but the moment I started doing anything of size in firefox the link would die -- light going off on the card, the works. Shortly after the link died I'd start to see graphical lag, followed by everything but my mouse and a few other things (Such as, I could push buttons and see the graphical changing of the button -- or if I moused over something that would usually change size it still changed size. However, nothing actually happened if I'd click the button, the actual program stuck (just not the GUI it seemed)).  A cold reboot seemed to fix things in these situations... But where was the famed stability of Linux? I've had too many friends tell me about it to just blame what was happening on the OS alone -- something is clearly going down between the wireless card drivers and Ubuntu.

I decided that the next time the Internet connection dropped out and died I would write down everything that happened and the results of my attempts to repair it. It went something like this:
- Internet Connection dies. Amarok running fine, Firefox running fine. But, with entire computer there is a slight graphical lag (like, when you pull a box across the screen and there is a trail of boxes behind it that vanish when you stop moving it around.). Things performed before the drop out were installing Amarok and mounting windows to get at my stuff on the other side of the partition. I was going to get a program (skype) and the Internet connection died as soon as the download started.
- I attempted to fix the problem by going to the networking menu and fiddling with the wireless settings. First I disabled wireless -- waited for the change to be applied -- then re-enabled it and waited for the change to be reapplied. No luck, connection still deader than a doornail.
- My next attempt was simply to unplug the card from the computer and then to replug it in. The moment the card was unplugged the entire computer went into complete lock up. No mouse function, no function from the other programs I had running (Firefox and Amarok), nothing. Completely stuck. Plugging the card back in didn't help.
- I performed a cold reboot by going down to my power strip and flipping everything off. After the reboot was performed and I loaded Ubuntu the internet seemed to work fine initally.

After this episode however I noticed that internet browsing went fine as long as I was browsing web pages that were not large, and B: was only browsing with 1-2 tabs open at a time. If I went to a webpage with say, imbedded flash ( I have the plugin for it going), or had many tabs open the Internet would lock itself up without completely dropping out. Rather than the link light dropping out on my wireless card (signifying a dead connection) it would stay continuously lit. Usually when I am doing anything online the light flickers to show activity.

This began happening disturbingly often, to the point where I was rebooting 2-3 times in a row.  The simple act of registering for the forums here became somewhat of a nightmare.

I left for classes and when I got back the screen saver had locked up (no idea what this was due to -- I am using the 2d braid screen saver as I haven't gotten Ubuntu to use my video card for 3d rendering yet...) and I had to perform another cold reboot. Upon reboot the computer had  taken the wireless option off of the networking menu and refused to let me online at all.  I went to the terminal and checked to see if the ndiswrapper module was loading (Or at least tried to) and from what I gathered (though I could be very wrong) it is.

So, uhm, from what I can best guess my wireless card and Ubuntu are having an EPIC battle that I am not privy to at all. Are there any known issues with my card's drivers and ndiswrapper? Are there any ways to solve what's going on with the drivers? Am I doing something terribly wrong that one should never do with Ubuntu? In short -- How can I get my card running smoothly and consistently so that I'm not rebooting 6 times a day, and well, get it working at all at this point?

---

### Post by Durito on 2007-03-29
Are you sure you need ndiswrapper? Did it load any modules for your wireless when you first installed? And if so, did you blacklist them? Otherwise your machine might be using those, ndiswrapper or no. What does **$lshw -C network **return?

---

### Post by Durito on 2007-03-29
I've also had some problem with kernel panic around the wireless card. Sometimes if it can't find the network it throws a hissy fit. Phbbt. Annoying for an OS known for its crash proofness, no? I haven't really starting fussing with it yet. Though it's next on my hitlist, and I'll let you know what (if anything) I figure out. In the meantime, trying googling "WUSB54Gv2 kernel panic" or " [W, etc] crash". It returns some hits. What sort of machine are you running on?
 
You can never find a guru when you need one, yo.

---

### Post by LadyLuna on 2007-03-30
Not sure what terminal says yet -- I'll have to check it once I finish up some stuff in Ye Olde Windows. I'll do some of the google-fuing then too.

I don't remember any modules being loaded for the wireless card -- it was completely nonfunctional before I used ndiswrapper. Is there any way I could check for them? Because if there are some I certainly didn't blacklist them.

EDIT: Machine I'm running on! Didn't see that bit before I replied, okay, machine specs are:

ATI graphics card -- not sure on specs, can look them up
1 gig ram
150ish gig harddrive all partitioned up. I gave Ubuntu 50 gig to toy with.
Dual Intel Processor 2.66 Ghz per processor.

It's a Dell prefab, I'm ashamed to admit. Still a little to chicken to attempt building my own machine.

---

### Post by Durito on 2007-03-30
No shame. I use ThinkPads myself. 

Sorry for the long delay--I dislocated my shoulder last night, and spent most of the day in the hospital.

Run **[FONT=Courier New]$lshw -C network[/FONT]**[FONT=Courier New][FONT=Palatino Linotype] and see what turns up under "driver". If it's the ndiswrapper one, you're probably good to go on that front.[/FONT][/FONT]

---

### Post by Durito on 2007-03-31
Also, do you have the same problem downloading things with **$wget [file location]**? It's a handy commandline utility. And, you can have it keep downloading in the background even after you've logged off.

---

