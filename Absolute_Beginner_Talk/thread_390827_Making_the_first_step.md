---
title: "Making the first step"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by StandardsDT on 2007-03-22
Many times before I've tried Linux. I've tried Linspire (yuck!), Mandriva/drake, and Knoppix to name a few. I've heard about Ubuntu but for whatever reason never made the move to try it. After countless times of being discouraged from Linux do to the above listed OS's I believe thats what held me back. So I finally decided to make the decision of trying out Ubuntu in VMware Server. After a night of trying it out and everything I love it! I would like to install it as my primary OS on my  laptop but then I remembered that there's one other thing holding me back. The Zune I had purchased a few months back. After doing some searching I found no solutions of being able to use the Zune natively on Linux. Most options required installing Windows as a Virtual OS and using it that way. Personally I would like to be rid of Windows on my laptop. Anyone have suggestions of what I could do to make the move besides tossing out the Zune? Is there any possible way to run the Zune marketplace using Wine or will it not install because it doesn't detect a Windows OS installation? And my final question why has no one been able to get the Zune to run on Linux successfully? I would have imagined by now this would have been accomplished.

---

### Post by karthikp on 2007-03-22
Right off the bat, I don't have a Zune. I do have an iPod, though. It works beautifully with Amarok.

The reason why the Zune doesn't work (it doesn't? Did you check?) could probably be because of two reasons - it's new and there probably aren't enough Zune users yet (Must...resist...making...jokes....). So, in all probability, someone will get that thing working if it becomes more (try...harder...)ubiquitous.

But if you're willing to sacrifice the Marketplace functionality, you should be able to use one of the media players to manage music on it...Any other Zune users around?

---

### Post by jimbren on 2007-03-22
There's a new project in the works called [Zune-Linux]("http://www.zune-linux.com/"), though it looks like they are looking to port linux to the Zune, not write a program that will allow you to add songs and such.  

I'd consider doing a small VMware installation of windows and talking to it that way for now.  Not the most elegant solution, but it is probably one of the only options out there right now. Remember that the Zune is very new to the marketplace.

jimbo

---

### Post by StandardsDT on 2007-03-22
Hmm this is true that it still is new. I've seen plenty of information about getting Linux to run on the Zune but hardly a thing about transfering songs to the Zune. Looks like I'll have to do a VMWare virtualization temporarily. And one more question I have a ton of songs that I originally purchased on iTunes back in August. What would be the best way to convert them over so I can listen to them?

Also feel free to make any jokes about the Zune you want. I'm not a fanboy so I won't take offense or anything to it.

---

### Post by dracomordag on 2007-03-22
Zune uses MTP, so check out [http://www.ubuntuforums.org/showthread.php?t=199250](http://www.ubuntuforums.org/showthread.php?t=199250) to see how to get MTP devices working in Ubuntu.

Zune, however, uses an updated version of MTP, so it may not work... but i'd try it anyway.

---

### Post by karthikp on 2007-03-22
> **StandardsDT said:**
> And one more question I have a ton of songs that I originally purchased on iTunes back in August. What would be the best way to convert them over so I can listen to them?

Ah, sweet DRM hell! I'm afraid the only legal way out of this is to burn the iTMS songs to an audio CD and rip it back into mp3's. And that takes time, especially if your DRM'd collection is big...

---

### Post by Zune-Online.com on 2007-03-22
Zune uses MTP. This means you can use libmtp open source library (amaroK supports it but you may have to compile it from source to enable it). The problem is Zune Software uses a login system, so the tasks you can do with amaroK are very limited (no read/write tracks).

If you use VMware v5 it works fine with a small adjustement: you have to use a v1.1 USB port, or unload the USB 2.0 driver module from kernel. If you don't do this Windows hung. 

VMware 6 will support USB 2.0, but the last beta I tried a month ago was very unstable and I can't verify it.

You can find more details here:
[http://www.zune-online.com/mac-and-linux.html](http://www.zune-online.com/mac-and-linux.html)
[http://www.zune-online.com/forum/linux-support/current-status-of-amarok-with-libmtp-t253.0.html](http://www.zune-online.com/forum/linux-support/current-status-of-amarok-with-libmtp-t253.0.html)

For stripping DRM off iTunes tracks there are better solutions than burning them on CDs, but you won't learn them from me :)

---

### Post by StandardsDT on 2007-03-22
Thanks for responce zune-online.com I shall give your suggestions a shot. I  have ran in to one problem with display resolution. My display can support 1980x1200 and I've done so in Windows. Is there anyway to enable this on my video card? I have a Nvidia Geforce Go 6800.

---

### Post by StandardsDT on 2007-03-23
i made an error i meant 1920x1200. sorry about that! anyways i found some tutorials here on the forum and else where and nothing works. i restart and it still does not show 1920x1200. i know for a fact my computer can display at that resolution. any ideas?

---

### Post by StandardsDT on 2007-03-23
Well this is my last post in this topic. I finally got Ubuntu properly configured to my liking with Beryl. Printer, Networking it's all set up. I would like to thank those of you who helped me make this as painless as possible and I thank all of you who gave me advice in this topic. Unfortunately I have to install Windows in a Virtualization for my Zune but once the Zune is cracked to run on Linux Good Bye Windows for Good. I Hope.

---

