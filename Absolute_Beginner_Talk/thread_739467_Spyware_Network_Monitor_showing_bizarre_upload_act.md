---
title: "Spyware? Network Monitor showing bizarre upload activity"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by John Costella on 2008-03-29
Hi folks,

I'm relatively new to Ubuntu (but an old hand in DOS/Windows). Please be gentle. Please redirect me if I am asking in the wrong place.

I run the Network Monitor graph in the top toolbar, and look at it often when downloading. 

This morning I noticed it was maxed out even though I wasn't pulling anything down. I went into it and it thinks that I am **up**loading at 180 kB/s. 

My Windozed brain immediately thought of Spyware for a millisecond, until I realised that the return path of my 256 kbps ADSL is only around 5 kB/s. I checked the modem (I don't look at it often) and the Wireless and Ethernet lights are blinking at a regular rate. (The ubuntu machine connects to it through wireless.) I then thought that perhaps some sort of communication (or worse) was occurring with the other two (Windows) machines on the modem, one of which is directly connected. But I've shut down those two machines, and Network History still thinks it is uploading at 180 kB/s.

The upload must be a bogus reading, because I can still surf the net and pull down a YouTube video at 27 kB/s (the normal maximum rate of download through the ADSL). (But I notice that the results of my nightmare attempt yesterday to try to get the microphone to work on Ubuntu has now killed the sound on YouTube videos ... sigh.)

I'd almost kicked my Windows addiction by getting Ubuntu to a reasonably usable state (following a lot of command-line hacks that really shouldn't be necessary), but, in the words of Scotty, "She's breakin' up, Cap'n."

Anyone out there help me save the Enterprise?

Thanks
John

---

### Post by Joeb454 on 2008-03-29
Could be a bug in Network Manager...although you should know that if there's no reported spyware app's around for Linux :)

---

### Post by saj0577 on 2008-03-29
You should make regular back ups specially if you have great trouble getting your system to work..

Saj

y only input into this sorry.

---

### Post by The Cog on 2008-03-29
It might be interesting to install iftop and then run it with:
**sudo iftop -i eth0**
to see what's talking to what.

---

### Post by John Costella on 2008-03-29
Thanks Cog -- fascinating tool.

There are some bizarre entries popping up, but it is dominated by an apparent uploading to 224.0.0.56 at 1.38 Mb ...

Aha ... Pulse Audio. That damn thing I installed yesterday to try to solve this microphone nightmare!

Yes, I found the answer here:

[http://taint.org/2008/03/21/142716a.html](http://taint.org/2008/03/21/142716a.html)

which solved the problem.

I suspect that, in my case, the RTP was not actually being broadcast, because it wasn't affecting my download speeds.

It was intriguing that, when I originally installed Pulse yesterday and rebooted, it took several minutes on login (the ubuntu  and thermometer) when it was talking to the wireless. I thought the machine had frozen. It eventually finished booting, but I was a tad suspicious about what it was doing all that time,

Whatever Pulse's benefits are (and it provided none, with regard to the microphone; and indeed has killed some of my sound system now), it's malware in my books, and I'll try to remove it using the reverse of the wiki article that told me how to install it.

Many thanks, people! (esp The Cog) :)

John

---

