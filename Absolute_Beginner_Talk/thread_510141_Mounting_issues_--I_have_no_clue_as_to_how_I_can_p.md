---
title: "Mounting issues --I have no clue as to how I can proceed"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by ratbagradio on 2007-07-26
I have posted before on this: [here]("http://ubuntuforums.org/showthread.php?p=3065420#post3065420") and later [here]("http://ubuntuforums.org/showthread.php?p=3071359#post3071359") and I apologize to everyone for being persistent but...

I'm on Edgy after a  fresh install of Dapper. It's a great setup and I love it except for one major hitch: I cannot mount either of my mp3 players -- iriver T30 and IFP -- nor my usb stick. I

My digital camera mounts fine....the printer installs fine. I've changed usb ports to see if that changes the interface. But when I plug in a device the device Ubuntu ignores it.
My kernal is:
2.6.17-12-386

So what procedures step by step do I need to follow to work through this problem? What do I have to vet? What apects do I need to check? What changes can I make? What tests can I run?

---

### Post by srt4play on 2007-07-26
Oohh I have bad memories of an iriver t30, at least I think it was a t30.  My girlfriend has one and boy was it fun updating the firmware in it to make it usable.  It comes formatted to only work with windows media player,  MTP is the term I think.  If yours is MTP, you need to update the firmware in it to make it usable as a regular usb storage device.

iRiver's firmware updater only works in Windows, and the fun part was when they had tons of firmware downloads who's descriptions were very confusing.  We had to pretty much go one by one through each of the firmware downloads until we found the one that worked.

---

### Post by NESFreak on 2007-07-26
libmtp is included with feisty. Synchronise using gnomad2 or amarok.

---

### Post by ratbagradio on 2007-07-26
>  	libmtp is included with feisty. Synchronise using gnomad2 or amarok.

Ah. I weas working on the issue last night and I got it to recognise the T30 ...BUT it woudl flah in and out of recognition, such that when I went to delete files from the device it locked down and insisted I had dangerously removed the item. Then it wouldl shift but into read agina and my desktop would h go highwire switching in and out of the device folder and my player -- Amarok. or Rythmnbox

I use Amarok. I think at some stage I mislabeled the mount. I have a few media files with t30 and irivert30 to get rid off but Ubuntu won;t let me delete them. 

How do I work around that?

Thn whne mounting in Amarok I need to follow a code protocol for the T30 and the ifp -- so what's the likey script? I get asked for "5" protocols...

But this won;t solve my usb stick problem I guess.

So I either have muched up the miunting protocol or my usb hardware is playing up (but I very much doubt the later because it works fro other devices/hardsware -- like printers and cameras.

How do i syncronise using gnomad2 ?

---

