---
title: "Newish user: Would like a little help if possible"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by DarkGashX on 2007-05-09
The reason I used the title I did for my topic is because I have a few questions to ask if the great Ubuntu community doesn't mind. If you don't want to read why I am considering Ubuntu yet again, please start at [COLOR="Red"]**[!]**[/COLOR] below.

I have tried Ubuntu before, a good few times in fact and loved how stable it was and the fact that it is free and I won't have to fork out a whole load of money for a new OS/hardware every 3-5 years. I used it for a couple of months and decided to go back to Windows. The decision was simple at the time, my NTFS hard drives wasn't safe to be written too and a lot of drivers were missing for my peripherals.

I have now been using Windows for about 10 years and I have been testing Vista and have been using the RTM (final) version of Vista for a good month or two now and I am very disappointed with it. My computer that once was a super beast is now a slow snail running it and I hate the constant UAC (User Access Control) bugging it does. My computer is ready for a format and so I have the choice: Windows XP, Windows Vista or Ubuntu. Knowing Ubuntu didn't have stable NTFS support back on 6.06 when I lasted used it, I noticed 7.04 was out and did a quick Google for "Ubuntu NTFS" only to fall off of my chair backwards with a result in my face with the following "Ubuntu 7.10 has stable NTFS read/write drivers!".

I would get a Mac but I just don't have the spare cash to do it right now and seeing the Google result I did I just had to come to the Ubuntu forums and ask some questions.

[COLOR="#ff0000"]**[!]**[/COLOR] Enough babbling, let me get on with my questions.

**1) **Even though Ubuntu says NTFS is now stable, is there any possibility (even 0.01%) that I could loose data? I have some precious big files on one of my hard drives I wouldn't want to risk loosing.
**2) **If data loss is a possibility, is there any safe way to convert to EXT3 OR EXT4?
**3) **How do I mount an external Hard drive? Isn't there an "auto" mounter?
**4) **Is there a Linux download manager/accelerator like Flashget? All the ones I have found don't seem to do both.
**5) **Is there currently any stable working Logitech G15 drivers? I can _[see these ones](http://g15tools.sourceforge.net/)_ but have never used them before.
**6) **I understand there are working Quicktime and Windows Media Player alternatives. Is there any that will work in the Opera browser with Ubuntu so I can watch streaming video?

That's all I can think of for now. Thank you everyone :).

---

### Post by Acglaphotis on 2007-05-09
1: There is always the posibily of a bug.
2: I think the only to way to do that is transferring files to external disk, then re-format partition as ext3. (there is an ext4? didnt know that ! :) )
3: My external drive automounts whenever i plug it in.
4: Eh... i think there are some of those in the firefox extension library.
5: Sorry, i have no idea.
6: Opera has an official port for linux! 

Hope i helped.

-Acgla

---

### Post by viciouslime on 2007-05-09
I'm afraid I don't know about 5&6 but basically the ntfs driver is stable. It has been tested to absolute extremes over very long periods of time now and no data corruption has occurred, however, there is always a chance of corruption, not just in linux, but also in windows! I've actually had xp corrupt two separate ntfs drives, but that's another story. Basically, the chance of anything being corrupted on linux is the same as on xp now, i.e. extremely small. However, it would still be better to use ext just because it is much more mature in the linux world, everything can read and write to it. You can' convert directly, however, if you can move all your data elsewhere then copy it back that will work.

External hard drives are just a case of plugging them in in my experience. Once you plug it in, ubuntu will mount it automatically and show you it's contents.

As for flashget, it works on linux, it is just a firefox plug-in, it works on os x, linux and windows.

It needs something to send downloads too though, try gwget or freeloader, both are pretty good :)

---

### Post by DarkGashX on 2007-05-09
I will be using Opera though, not Firefox. I prefer it over the Fox ;). And it wasn't Opera I wanted to run on Linux. It is streaming Quicktime and Windows Media Files I wanted to know if they worked or not in Opera.

---

### Post by Cypher on 2007-05-09
> 1) Even though Ubuntu says NTFS is now stable, is there any possibility (even 0.01%) that I could loose data? I have some precious big files on one of my hard drives I wouldn't want to risk loosing.

I've tried the NTFS driver in Ubuntu 7.04 Feisty Fawn and it has worked out fine. I don't think you'll have any trouble here.
> 2) If data loss is a possibility, is there any safe way to convert to EXT3 OR EXT4?

I don't believe you can convert to a different filesystem from NTFS without actually formatting and losing the data. So you'd only want to do this once you've gotten all your important files into your Ubuntu system.
> 3) How do I mount an external Hard drive? Isn't there an "auto" mounter?

The Kernel/Ubuntu will recognize most external devices and automatically mount it for you. So far I've tried a  WD MyBook external HD(Firewire), iPod(USB), Fuji Film Digicam(USB), Panasonic DV Camcorder(Firewire) and all have been properly recognized and usable without any extra work on my part.
> 4) Is there a Linux download manager/accelerator like Flashget? All the ones I have found don't seem to do both.

Get a faster Internet connection. :) I've never bothered with download accelerators..
> 5) Is there currently any stable working Logitech G15 drivers? I can see these ones but have never used them before.

No clue on this one..
> 6) I understand there are working Quicktime and Windows Media Player alternatives. Is there any that will work in the Opera browser with Ubuntu so I can watch streaming video?
There are indeed alternatives and they should work for streaming. But you might want to do a specific search related to that in this forum..

---

### Post by DarkGashX on 2007-05-09
> **Cypher said:**
> I've tried the NTFS driver in Ubuntu 7.04 Feisty Fawn and it has worked out fine. I don't think you'll have any trouble here.

I don't believe you can convert to a different filesystem from NTFS without actually formatting and losing the data. So you'd only want to do this once you've gotten all your important files into your Ubuntu system.

The Kernel/Ubuntu will recognize most external devices and automatically mount it for you. So far I've tried a  WD MyBook external HD(Firewire), iPod(USB), Fuji Film Digicam(USB), Panasonic DV Camcorder(Firewire) and all have been properly recognized and usable without any extra work on my part.

Get a faster Internet connection. :) I've never bothered with download accelerators..

No clue on this one..

There are indeed alternatives and they should work for streaming. But you might want to do a specific search related to that in this forum..

I am on 20Mbit connection. It is just that servers far away can be very slow so spliting the files up with a download accelerator makes them faster :).

Maybe I should Re-Fraze what I mean about Opera. Is there any Linux media players that play WMV/MOV and can also be used in Opera to view the same content streamed?

---

### Post by Cypher on 2007-05-09
20MBit, wow..that's fast..what exactly are you downloading from far away servers, huh?? :p

There are indeed players for WMV/MOV/ASF/MPG, check out MPlayer, XINE, Totem, VLC and others I'm probably not thinking of.

---

### Post by DarkGashX on 2007-05-09
> **Cypher said:**
> 20MBit, wow..that's fast..what exactly are you downloading from far away servers, huh?? :p

There are indeed players for WMV/MOV/ASF/MPG, check out MPlayer, XINE, Totem, VLC and others I'm probably not thinking of.

Gametrailers.com HD videos at peak times mostly. I read Opera works with MPlayer to play streaming content, _[see here](http://www.opera.com/linux/docs/plugins/install/#mplayer)_.

Does MPlayer/Can MPlayer play Quicktime content?

---

### Post by DarkGashX on 2007-05-11
Ok, I have been playing with Ubuntu again :)

NTFS seems very stable and more "responsive" then windows even! I am very impressed.
I have also been looking at web browsers. Opera + Flash in Ubuntu seems to have an issue now for some reason, it seems to make flash content "grey" until I move the window.

The cube and wobble effects are really nice! I like the fact you can "one click" install the required driver as well, very good move and thanks to the Ubuntu team for doing that.

So now all I need to know is information on the Logitech G15 drivers and for someone to recommend a download accelerator. I may switch back to Firefox at a later date but for now I need a stand alone one.

:guitar: Thank you to everyone who has replied so far, the Ubuntu team and Linux devs/community.

---

