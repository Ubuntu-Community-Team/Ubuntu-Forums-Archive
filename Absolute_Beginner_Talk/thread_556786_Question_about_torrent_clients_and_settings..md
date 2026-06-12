---
title: "Question about torrent clients and settings."
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by c_olin on 2007-09-21
I just moved on campus and they hooked me up with a very fast connection.  They let us download as much as we want, but don't want us using torrents because of the use of upload bandwidth and the high use of pirating.  They said it was fine if I set up my torrent client to where it would not upload anything; strictly downloading...

I have tried this on multiple clients, but pretty much all of them force you to upload while you download.   Which is understandable, if nobody uploaded, then nobody could download.

I was hoping someone could help me set up a torrent client on Ubuntu with full downloading capabilities but no (or limited) uploading capabilities.

Thanks

BTW I hope this is the right forum to ask this in.

---

### Post by Mr. T on 2007-09-21
I don't know of any torrent clients which allow you to disable uploading entirely, since it goes against the idea of torrenting to begin with. You could perhaps download the source code to one and hack it yourself, but that seems to be overkill.

What is possible with most modern clients is that you can specify the maximum speed of uploading, so as to cap for whatever reason. I use utorrent via WINE, and I can lower the upload speed to as low as 1 kB/second, which would probably blend in with regular net access and would definately not raise any suspicious. Then again, your downloading speed would probably suffer as a result.

---

### Post by starcraft.man on 2007-09-21
All major torrent clients I know of can set global and individual speed limits on up and download speeds (usually not 0). You should always set limits on both to optimize your connection, saturating either (especially upload) can cripple your client (so can low upload though too). Global upload should be 80% or less of your maximum and global downloading should be 90-95%. Ktorrent should work fine for you, it's in the repositories, if you need help installing click blue link in my sig. The configure menu will list speed limits so you can set them appropriately.

On an ethical note, if you don't intend to upload I suggest you not torrent. Leaching is wrong, no matter your situation IMO. I won't even bother trying to tell ya not to pirate. Remember that those campuses are cracking down and if you do that, you have an extremely high chance (from what I seen) of receiving a notice and being cut off from the net (and worse).

[Oh and no, the right forum would be here.]("http://ubuntuforums.org/forumdisplay.php?f=73")

These two links explain well how to optimize clients for traffic, it's for windows clients and azureus but applies to all. [Link1]("http://torrentfreak.com/optimize-your-BitTorrent-download-speed/") [Link2]("http://torrentfreak.com/calculate-your-optimal-bittorrent-settings/")

That is all. Above information is provided in good faith that your not planning on pirating or leaching. Reported for move too.

---

### Post by ryno519 on 2007-09-21
You can set deluge's upload rate to 0 in the network settings and the upload rate will hover around 0.2Kb/s (just tried it). Will that work for you? That's about 17 megabytes every day, so I doubt your school would notice, seeing as you probably do more just watching a couple of youtube videos.

On a side note, prepare to be bombarded by the ethics police.

---

### Post by c_olin on 2007-09-21
Yes, I understand why it is important for everyone to upload as much as they download.  

I guess I'll have to do without bittorrent.

Thanks for the help

---

### Post by ddrichardson on 2007-09-21
Sorry that is impossible. Every time a packet is recieved, a packet has to be returned to the control server - it's part of the TCP/IP protocol. There is simply no way around this. Frankly I'd be worried about any sysadmin who didn't know this.

---

### Post by bapoumba on 2007-09-22
On my campus network, torrents and IM are not allowed. Even if it bugs me from time to time (no IRC access for meetings, no torrent ISO dl), I comply with the rules. Please try to either do the same, or convince your network admins to reconsider. I understand the admins message to you is quite... strange :)

BTW: moved your thread to ABT.

---

### Post by ddrichardson on 2007-09-22
Further to the fact you need a response packet - there was an article on Slashdot a few weeks ago about a proposed change to torrent trackers that would disconnect anyone not sharing a file after download from downloading from that tracker again. The technological theory was sound but the implementation seems dubious.

Like Bapoumba says though, it's really not worth the risk of getting reprimanded by your Uni for complying with their policy, a number of US colleges have been the subject of RIAA lawsuits where the Colleges have sided with the RIAA and banned users even expelling people.

---

