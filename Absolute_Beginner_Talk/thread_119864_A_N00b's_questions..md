---
title: "A N00b's questions."
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by LinuX Nova on 2006-01-20
Hey.

I tried Ubuntu breezy live yesterday, and instantly fell in love with it. However, before I install it, I have some questions.

1) Is installing, half windows/ half linux difficult?(Dual boot) Are there any guides availible to do it? And, does this slow the computer down any?

2) I recently bought a Sony walkman NW-A3000 mp3 player. To put music onto it, one must use special sonicstage software. Would this be compatible with Ubuntu linux?

3) Can i use torrents?

4) I use a wireless usb adapter to recieve internet on the computer I'm installing Ubuntu/Windows on. Will it work with Ubuntu? (It's netgear if that helps)


Thanks all in advance.

Paul. :)

---

### Post by carlosqueso on 2006-01-20
1) No, it's not difficult, it's what many of us do.  There's a guide at [https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28dual%29%7C%28boot%29](https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28dual%29%7C%28boot%29) and lots of people are willing to help you. As for performance, as long as you leave some disk space for your windows partition to use as swap, it shouldn't slow down your computer.  Only one operating system will be working at a time.

2) That software is probably not compatible.  However, there may be something else that will work, or there may be a way to get ubuntu to see your mp3 player as an external hard drive.

3) Yup, there's a bittorrent program in Ubuntu.

4) The answer to that is maybe....look here: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29%7C%28card%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29%7C%28card%29) If that doesn't work, you may need the windows drivers and ndiswrapper instructions about which can be found here: [https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

Welcome to ubuntu!

---

### Post by christhemonkey on 2006-01-20
1) Dual booting i have found fairly easy!  Just about sets itself up...

2) Hmm not sure about that one, but my mp3 player worked fine putting music on.

3) Yes.

4) Possibly, dont know much about wireless.

And
5) Have fun with Ubuntu :D

Edit:
Seems i cant type fast enough!

---

### Post by public_void on 2006-01-20
> 1) Is installing, half windows/ half linux difficult?(Dual boot) Are there any guides availible to do it? And, does this slow the computer down any?
Ubuntu will install a boot loader called grub that will allow you to choose your OS when your computer boots. It isn't difficult as this is all done in the Ubuntu install. Your computer won't be slow because only one OS will be running.

> 2) I recently bought a Sony walkman NW-A3000 mp3 player. To put music onto it, one must use special sonicstage software. Would this be compatible with Ubuntu linux?
Hmmmm, I'm not sure, someone else should help you with that.

> 3) Can i use torrents?
Yes, I think bit torrent comes installed.

> 4) I use a wireless usb adapter to recieve internet on the computer I'm installing Ubuntu/Windows on. Will it work with Ubuntu? (It's netgear if that helps)
From what I've heard it can be hit or miss. You'll need ndiswrapper, that can be easily got when Ubuntu is setup. It will allow Ubuntu to use Windows drivers for the usb adapter. Your'll probably have to post back to get some help on it.

EDIT:This happens all the time. I knew someone whould beat me. At least the questions are answered.

---

### Post by christhemonkey on 2006-01-20
OOooh, just a thought:
If your mp3 player thing only works in windoze, then you can use wine or other such emulation software!
(or if your dual booting, just go back into windows!)

---

### Post by LinuX Nova on 2006-01-20
Yeah, I can always use my windows boot for the Mp3 player.

I really need the USB adapter to work as it is my main connection, and i wanna keep the host computer on windows as it's not mine.

---

### Post by carlosqueso on 2006-01-20
I'd reccomend trying it, and we'll help if it gives you any problems.  That's the beauty of Ubuntu.  It's not necessarily the software itself (although it's a very nice system), but the community that makes Ubuntu special.

---

### Post by christhemonkey on 2006-01-20
Yeah, there nearly always is a way to get things working.
Its just how to do it thats the problem!

---

### Post by LinuX Nova on 2006-01-20
Right. I'm gonna do it. Install Breezy I mean. Last question. How much is a sensible amount of space to partition for Ubuntu?

---

### Post by Kimm on 2006-01-20
I doubt sonicstage would work in wine, but try searching freashmeat.net or sourceforge.net to see if someone wrote a Sony mp3-player compatable program for Linux 

[http://sourceforge.net/projects/himdhack](http://sourceforge.net/projects/himdhack) could turn into something, has very low activity though and hasnt released anything.

---

