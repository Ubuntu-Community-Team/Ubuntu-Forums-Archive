---
title: "Bit Torrent download speed too slow"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by chuugokujin on 2007-06-10
I am using Azureus to download BT files. I do not have any speed problem in Windows, but the speed in Ubuntu is just like a few KB/s. I have a router and I already forward almost all ports to my local ip. Still the speed is soooo low. 
Could anyone help me?

---

### Post by dhruva023 on 2007-06-10
i don't know the answer,

however, i use utorrent under wine.

it works perfectly.  fast!!

bit torrent has never worked for me.

try utorrent.

---

### Post by NinerSevenTango on 2007-06-10
I read all kinds of conflicting and confusing stuff about this.  It might be that you need to open the port you use with some IPtables command line stuff.  I tried it and it didn't help.  I adjusted all the settings according to the Wiki.  I physically took the router out of the circuit to make sure it's not a NAT problem.  It would go for a few minutes, then stall, then dribble a few bytes, then stall, and the speed would never stabilize.  Under 1KB, when it decided to run at all.

What I ended up doing to fix the problem was to uninstall the dang thing.  Then I started downloading torrents using the built-in client.  It works somewhere between 50 and 100 times faster.  Only one at a time, and no settings or eye candy.  But it downloads, nicely.

Sorry if that wasn't much help.  I'm new to Linux (enjoying it for the most part).

I never did like Java.  Maybe it sensed that, and bit me again for it.

--97T--

Edit:  Next week I'll play with Wine for the first time.
Edit2:  If you like your uTorrent client, stick with it.  The company has been sold, new versions might not be privacy-friendly.

---

### Post by sloggerkhan on 2007-11-09
I'm having the same problem. Don't know why, but I've never had it before.
The built in client can't be throttled and does only one torrent at a time. I typically get downloads of about 200 kb/s second on decent torrents with it.

Never had a single problem with deluge, but recently,
even leaving it unthrottled, I start a torrent, it goes up and peaks at about the same speed as the built in client, and then it starts slowing down and within half an hour, it's stuck at like 0 - 1kb upload and download speeds. 

I don't have this problem with the built in client, and it's driving me nuts because I want something with a few features that works. What I especially don't get it that I never had a single problem with  deluge until this one seemingly showed up out of the blue...

---

### Post by dkruidhof on 2007-11-09
I never got Azureus to work very well on my computer either. I recently switched to Deluge and it's been working quite nicely so far. No problem with it slowing down to 0 like slogger mentioned, but I don't use it all that much.

---

### Post by sloggerkhan on 2007-11-09
Yeah, I don't know what's up with. Never had it happen until about a week ago, but it's doing it with pretty much every torrent. The same torrents are getting up to 200 kb/s sustained download in standard bit torrent client and transmissions, but stall out to pretty much zero after about 20 in deluge. I wouldn't care much if transmission had a blocklist importer (Of course, then it'd be pretty much the same as deluge anyway), but it's still irksome.

---

