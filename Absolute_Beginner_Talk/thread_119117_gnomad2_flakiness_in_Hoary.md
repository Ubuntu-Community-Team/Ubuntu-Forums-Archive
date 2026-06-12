---
title: "gnomad2 flakiness in Hoary"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by extraspecialbitter on 2006-01-18
I've been Hoary since May 2005, but I'm still booting XP at least part of the time.  It seems that I've been able to find adequate Micro$oft replacements on most - but not all - fronts.  While I find that Gimp and Bluefish meet my needs on the graphics editing front, I've yet to figure out how to get my Creative Zen Touch to work reliably with my Hedgehog. There's also the matter of synching my Blackberry to something other than Outhouse, although I'm thinking of switching to another smart phone to get around this.

As a workaround I've been synching my old Handspring Visor to my XP desktop using Outlook and then to my Ubuntu desktop using JPilot.  I found it at least equal to the Palm Desktop application on Windows, and look forward to retiring my Blackberry in favor of a Treo, which I hope to be able to sync directly to both XP and Ubuntu without a kludge.

As for audio, Rhythmbox seems adequate as an MP3 (once I installed the proper codex) and streaming audio player, but gnomad2 seems hit or miss when it comes to transferring files to my Creative Zen Touch. Some files make it without incident, and others seem to copy but then give me a Playback error when I attempt to play them.  Since it seems to be the lower quality MP3s that copy cleanly, I'm wondering if there's a bit rate threshold for the application.  Strange.

I'm not far from tossing Windoze for good, but I'm an audiofile at heart, and I need more a consistent interface before making the switch...

---

### Post by extraspecialbitter on 2006-01-25
Here's what I did to resolve this issue: I started from scratch.

First, I upgraded to Breezy, just to be sure that I would have access to the latest and greatest software.  Next, I ripped and encoded my CDs using grip and lame, and then sync'ed to my Zen Touch using gnomad2 2.8.0 (libnjb5 2.2.1-2).  Not one of nearly 1,000 tracks failed with a "Playback error".  Two tracks seemed corrupted (resulting in a loud hissing sound), but worked perfectly after decoding (lame --decode) and re-encoding (lame -h).

At this point I'm not entirely sure what caused the initial problem, but I'm more than satisfied with the results...

---

