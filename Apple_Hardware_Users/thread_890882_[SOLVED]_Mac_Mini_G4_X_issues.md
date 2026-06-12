---
title: "[SOLVED] Mac Mini G4 X issues"
date: 2008-08-15
forum: Apple Hardware Users
---

### Post by unugmax on 2008-08-15
Hi,

[SIZE="4"]Whats my goal?[/SIZE]
[SIZE="2"]*(no technical value, you can skip that if you like)*[/SIZE]

I´d like to turn a Mac Mini into a Linux Machine for Web Development. It shall provide a full featured LAMP Environment and a Desktop wich I use to code and work with the browsers. No runtime IDE required for now. The main task will be the work with Typo3.

[SIZE="4"]Why not Mac OS X?[/SIZE]
[SIZE="2"]*(no technical value, you can skip that if you like)*[/SIZE]

First, I never managed to build a suitable LAMP interface with the portage on Mac OS X which covers all my needs. I´m sure I could but it´s not worth the time fiddling arround with it. Second, Firefox on Mac OS is damn slow compared to what I´ve seen with Linux. Apple seems to have forgotten about the PPC users. I´m not willing to buy a new Intel Mac just for a new browser. My PPC´s need to last for a few more years ;)
[SIZE="4"]
Hardware involved?[/SIZE]

[LIST]
[*]Mac Mini G4 (PPC) first generation, radeon 9200 GPU
[*]iiyama AU4831D 19" TFT. max resolution 1600x1200, connected via DVI
[/LIST]

[SIZE="4"]Whats the problem?[/SIZE]

Gentoo is always my first choice so i´ve installed it. Worked great until I tried to get X running. The machine crashed every time I´ve killed the X server. Couldn´t get a solution so far.

Tried Ubuntu 8. Same here, didn´t even boot from CD. Ubuntu 7.04 works fine. X comes up and it can be installed. Big problem: The X server delivers a 1600x1200 desktop (not virtual) while the tft screen only runs at 1024x768.  The same problem appears on SuSE 11.

[SIZE="4"]What did I try?[/SIZE]

I found out that is could be a problem with the screen itself. Since I don´t have another one available, I can´t try another one. 

So I tried:
> 
Option         "ModeValidation" "NoDFPNativeResolutionCheck"

in the screen section of the [xorg.conf]("http://max.unug.net/ppc-suse/xorg.conf").

Doesn´t work. It´s one of these damn ATI cards, not a good linux compatible Nvidia chip. 

So I read the radeon manpage and finally played around wiht this:

> Option "PanelSize" "1600x1200"
Option "DDCMode" "true"
Option "IgnoreEDID" "true"
Option "NoDDC" "false"
Option "LVDSProbePLL" "false"

No effect at all. So I ask for your help in this matter.

Here are links to a few resources which might be valuable.

- LINK: [My xorg.conf]("http://max.unug.net/ppc-suse/xorg.conf") (SuSE, but doesn´t make much difference, it´s all the same X)
- LINK: [the X.org Log]("http://max.unug.net/ppc-suse/Xorg.0.log") (SuSE too, looks about the same on Ubuntu, which is still my preferred solution)

- LINK: [A topic about gpu problems on a Mac Mini in this forum]("http://ubuntuforums.org/showthread.php?p=4762956")
- LINK: [A topic which confirms that the monitor could be the problem]("http://osdir.com/ml/linux.ubuntu.user.kubuntu/2005-08/msg00035.html") (No I don´t have a VGA Adapter)

Thank you very very much for any help in advance. I start getting desperate about this topic.

cu
max

---

### Post by unugmax on 2008-08-15
GOT IT!!! :)

Well after three days of fighting I could expect to find some solution. The Mini now runs on Ubuntu 8.04. It´s fast and easy to use. Nice Release. Much better then 7.10.

Ok, what did I do? I found [THIS in the Ubuntu Wiki]("https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu%208.04%20PowerPC%20LiveCd%20will%20not%20boot%20on%20iBookG4"). Very usefull, thanks!

The line:
> live-nosplash-powerpc modprobe ide-core video=radeonfb:1600x1200-24@60 used with the yaboot of the live CD did the trick to boot.

It booted into a 1024x768 mode. From here it was no problem at all to set 1600x1200. After the unproblematic installation I was afraid it would not boot properly. Ok, it shows a totally fu**ed spash screen which is alright. I´d like to turn it off anyway. Don´t like the idea of not seeing whats going on under the hood. X comes up correctly and works. I had to set 1600x1200 again, but now it really works :)

I hope this post is usefull to ANYONE who has similar problems in recyling an old G4 Mac Mini. Working with the G4 is much nicer now since a lot of deleys do not happen any more. It´s a bit annoying if you have to wait for a simple browser output more than half a second on a DSL connection.

cu
max

---

### Post by stream303 on 2008-08-16
Wow - glad you got it work and thanks for the great feedback!

You might be able to get away with not using modprobe ide-core with 8.04, as that was a real pain mostly for Gutsy 7.10.  I know I didn't need it on my G5 running Hardy 8.04, but maybe yours still needs it?  A quick test will tell.

Is the screwed up screen a bungled dmesg, or does it still look like the graphical splash screen with the sweeping gas-gauge?  That splash has never really worked well in most instances, and I'm surprised that live-nosplash-powerpc didn't take care of that for you.

At any rate, you could also try editing *nosplash* into your /etc/yaboot.conf file in the append= line.  then follow up with a ybin -v -C /etc/yaboot.conf and see if you now have a clean dmesg at boot.

Even though you aren't running Feisty 7.04 - it makes for a great diagnostic tool just to get some xorg.conf values and yaboot.conf values out of it that may aid one later on with later versions.  If you are doing installs frequently, I think having the "alternate" Feisty 7.04 ready to go in your toolbox a good thing, even if the first thing you might do after grabbing some values is to blow the whole install away.  I'd grab it before it goes away from the repos before too long.

Congrats again!

---

### Post by youfudoij on 2008-08-17
it is an unearthly world. There are all kinds of character. Some of them like promenade. Obtain delight in this far-flung course. Others like assault .fight the enemy. You could find interesting in slow journey.  Step by step. You also could leap in a short time by use safety powerleveling.
[www.8thgame.com](www.8thgame.com) provide safety pl. their gold is cheapeast also.
:popcorn:

---

### Post by unugmax on 2008-08-18
Hi thanks for the welcome. I'll try turning off the splash in the yaboot as you described. Right now I don't mind. I usualy don't restart computers very often. Thats for windows users :)

Well now that I had the chance to try this latest release of ubuntu I'm quite happy with it, even if it doesn't offer the extreme flexibility of gentoo. I had serious trouble with 7.10 and banned ubuntu from my list of friendly distributions.

It runs great in the live CD mode on my Powerbook G4 12". Yet I can't risk to change it into a dual boot system. It's to important at the moment. When I'm back home I'll may try it on my mighty G5. I was so surprised by the speed boost on the G4, I really wonder what wonders Linux could do on a G5. It's a shame that there are no nvidia drivers for the PPC. The 6800 Ultra in my G5 would show very nice framerates :D

cu
max

---

### Post by stream303 on 2008-08-18
> **unugmax said:**
> I had serious trouble with 7.10 and banned ubuntu from my list of friendly distributions.

There are certainly peaks and valleys with any distro.  One day Debian rocks, then Ubuntu, then Fedora, and then back down the chain. :)

> The 6800 Ultra in my G5 would show very nice framerates :D

Be sure to do some quick research on that card to see if it might present some problems in ppc land.  I think it has been covered here, or in the archives.

---

