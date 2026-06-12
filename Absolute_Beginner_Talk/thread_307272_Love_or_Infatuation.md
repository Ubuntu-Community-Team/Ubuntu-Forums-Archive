---
title: "Love or Infatuation?"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by CtrlAltDelete on 2006-11-26
After testing the Live Cd, I went all out in being commited to linux (I didn't even leave the possibilty of Windows to be reinstalled) Two days later the decision seems to be ok. Just like I expected I will need more time browsing through forums to get everything rolling. (ex. wireless card, stability of beryl, tv card)

I have read the minumum requirements to run Ubuntu.. but what are the practical requirements to have it running reasonably smooth.

My Dinosaurus-
E-Machines-Intel Celeron Processor 2.93 Ghz
533 mhz fb
256 kb l2 cache

Memory- 256mb ddr sdram
dual channel capable

video- intel xtreme graphics2 3d

HD- 80 gb ata

Right now its a bit laggy because of the ram... i think. What steps would you take (limited budget) to improve the quality of the linux enviroment.

Another option is to take a break.. and save up for a more capable computer in the future. (dell)

---

### Post by Perfect Storm on 2006-11-26
and extra 256mb ram will do wonder. Or perhaps using Xubuntu instead. It can run great on low end computers.

---

### Post by Stew2 on 2006-11-26
Your system should run Ubuntu just fine. Definitely wouldn't hurt to up the ram to at least 512 though :) . If it still seems slow to you, try the Xubuntu desktop in the repos. Hope this helps.

Regards,
Stew2

Edit: Doh! Artificial Intelligence beat me to it! :)

---

### Post by meng on 2006-11-26
Another vote for RAM.

---

### Post by hydrox on 2006-11-26
Hey,

I don't mean to be rude, but buying a new computer seems a bit drastic. Up until 2weeks ago I was running a 700mhz Intel Celeron, 10GB harddrive, 256MB/ram, computer as my main desktop, using Debian as the operating system, and I found it quite usable.

I really don't think it's the computer's problem, or even the lack of RAM that's making it sluggish. I'd very rarely surpass the 256mbs of RAM I used on my old computer, and the CPU never seemed that much of a problem.

I don't know what the problem with it acting sluggish is, but I highly recomend against buying an entire new system, with your specs I can't imagine how you'd have a problem with the speed. Make sure everything's working fine, it could be a piece of hardware acting strangely, or the software/hardware compatibility.

Mike.

---

### Post by CtrlAltDelete on 2006-11-26
Adding Ram:
Does the:
The ram I add has to be ddr sdram?
Have to also be 256 or can I put a 512,1gb,2gb

---

### Post by bulldog on 2006-11-26
> **CtrlAltDelete said:**
> Adding Ram:
Does the:
The ram I add has to be ddr sdram?
Have to also be 256 or can I put a 512,1gb,2gb

Well you stated you motherboard can run with dual channel,and you should take two identical peaces of RAM and place them in the right slots of your motherboard.
If you take two times 256MB or two times 512MB is depending on your budget.
But definitely go for the dual channel option.

---

### Post by CtrlAltDelete on 2006-11-26
Choppy Dvd Playback is a Hardware or Software Problem? Maybe both?

Do I also need to upgrade my video card?

---

### Post by IYY on 2006-11-26
Choppy DVD playback can be a video card issue. It's possible that you just do not have the correct drivers installed, though.

---

### Post by Perfect Storm on 2006-11-26
> **CtrlAltDelete said:**
> Choppy Dvd Playback is a Hardware or Software Problem? Maybe both?

Do I also need to upgrade my video card?

Do you have installed libdvdcss2?

---

### Post by happy-and-lost on 2006-11-26
RAM or Xubuntu
AFAIK, Intel Extreme 2 graphics are cheap integrated graphics chips. A good nVidia PCI card should do the trick.

---

### Post by CtrlAltDelete on 2006-11-26
> **Artificial Intelligence said:**
> Do you have installed libdvdcss2?

I installed automatix2 codecs and drivers. The dvd was playing well before i installed beryl using this technique:

[http://www.ubuntuforums.org/showthre...t=beryl+dapper](http://www.ubuntuforums.org/showthre...t=beryl+dapper)

Since then the whole system has been pretty choppy and slow. I have  had help on this issue in an earlier thread:

[http://www.ubuntuforums.org/showthread.php?t=306960](http://www.ubuntuforums.org/showthread.php?t=306960)
Everytime I restart my computer i must type :
> 
xmodmap -e "keycode 22 = BackSpace"
beryl-manager


in order to get Beryl working.


I love Beryl I think I am just a few tweaks away from making it work. Again I would love thank this community for helping make Ubunto possible.

---

