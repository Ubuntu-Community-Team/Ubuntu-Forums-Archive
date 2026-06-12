---
title: "Basic torrent questions"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-09-26
I've only just started looking at torrents - I'm thinking about when I need to get large(ish) ISOs such as a new LiveCd or release of Ubuntu.

I understand that I should leave my torrent program running for a while, but how does the software know how to find any files on my PC to share? Is it searching my drive? Are there any security implications? (Sorry, I've only switched from XP recently, and I see spies behind every pixel!)

Should I leave downloaded ISOs on my PC for a while for sharing?  I've got plenty of space on my drive at the moment, but I usually delete that sort of stuff fairly soon.

TIA - I know I'll understand it all one day. :)

---

### Post by darc on 2007-09-26
> **freesitebuilder said:**
> I've only just started looking at torrents - I'm thinking about when I need to get large(ish) ISOs such as a new LiveCd or release of Ubuntu.

I understand that I should leave my torrent program running for a while, but how does the software know how to find any files on my PC to share? Is it searching my drive? Are there any security implications? (Sorry, I've only switched from XP recently, and I see spies behind every pixel!)

Should I leave downloaded ISOs on my PC for a while for sharing?  I've got plenty of space on my drive at the moment, but I usually delete that sort of stuff fairly soon.

TIA - I know I'll understand it all one day. :)


1)  Torrent software doesn't search your drive or share any of your files unless you specifically create a torrent of files to share, and upload that torrent to a tracker.  It will share (seed) files that you've downloaded via torrent until you tell it to stop (some software automatically stops at 150% upload, torrentflux for example, unless you set it higher).

2)  There's no specific security implications other than what can occasionally occur due to a bug in your torrent program (I use Azureus) or downloading a malicious file and executing it.

3)  If you download an ISO via torrent it is common courtesy to let it seed (upload to others) until you've uploaded 100% to 150% as much as you downloaded.  Of course, the longer you leave it seeding, the more you're helping others if you can spare the disk space and upload rates.

If you have other questions, shoot.
-darc

---

### Post by P235 on 2007-09-26
Hi, the user typically selects the files he wants to share with his torrent program.  The torrent program is not like a P2P community sharing program like Kazaa or the like because it won't scan your hard drive to find fies to share and it won't open up a file or location on your computer to the public either.  Some torrent programs, like Azureus, have features and add-ons to give users the ability to create blacklists that block specific IPs.  

When you download a file through a torrent, you are generally expected to reach at least a 1:1 share ratio to maintain the 'life' of the torrent.

---

### Post by glotz on 2007-09-26
It is regarded courteous to leave the torrent active for awhile after downloading it. However, it is quite ok if you don't. The BT protocol is designed to upload while it downloads (the file you're downloading). Diskspace is seldom the limiting thing. Usually it is the bandwidth, cpu time and memory the client uses. (Don't know about security implications)

Welcome to the land of Ubuntu by the way! :)

---

### Post by JBAlaska on 2007-09-26
When you load a torrent file into your client it asks you for a "save location", this is the place your download will be stored in, after the download is complete, your client will continue to upload or "seed" the flie to others in the "swarm" (people on the same torrent).
Torrents unlike some other peer 2 peer protocol's does not share from a common directory, you have to load a torrent file containing info about the file and a tracker url, the tracker controls the file sharing for everyone on that file.

When your download completes, you should allow it to seed to at least 1:1 in other words, upload the same amount as you have downloaded, this will allow others to get the file and keep the torrent alive.

The best torrent clients are;
uTorrent (run under WINE in linux)
Azureus (full featured but may be somewhat confusing to beginners)
Deluge (I have not tried it as it's not allowed on many private trackers, but it may be the best one for you to get started on)

There are many other good torrent clients, but when your starting out it's best to stick with the above.

If your going to share open source material, that's all you need to know to get started. If your planning to share copywrited material, there's alot more you need to know to do it safely, in this case I advise you to pick a semi-private tracker (open signups) and visit the forums to get some basic advice.

If you try to use public trackers, you will probably  end up with a nasty letter from your ISP...or worse..Not worth the risk IMHO

Good luck and happy torrenting

[color=#3333FF]Edit: Guess I'm a slow typist LOL[/color]

---

### Post by freesitebuilder on 2007-09-26
Aha - so I can run Azureus when I'm online to share stuff, even if I'm not downloading? Then it won't matter if I download some other time and can't leave it running afterwards for a while?

---

### Post by anemptygun on 2007-09-26
> **darc said:**
> 1)  Torrent software doesn't search your drive or share any of your files unless you specifically create a torrent of files to share, and upload that torrent to a tracker.  It will share (seed) files that you've downloaded via torrent until you tell it to stop (some software automatically stops at 150% upload, torrentflux for example, unless you set it higher).

2)  There's no specific security implications other than what can occasionally occur due to a bug in your torrent program (I use Azureus) or downloading a malicious file and executing it.

3)  If you download an ISO via torrent it is common courtesy to let it seed (upload to others) until you've uploaded 100% to 150% as much as you downloaded.  Of course, the longer you leave it seeding, the more you're helping others if you can spare the disk space and upload rates.
-darc
 Well said.

---

### Post by JBAlaska on 2007-09-26
Its good practice to keep a overall ratio of 1:1 + and try to seed back as much as you take on each file, if you download then drop off this is called "hit and running" and is not appreciated in the torrent community (And will get you banned from private sites) you are expected to do the best you can to "pay Back" what you take, sometimes this is not possible, in this case it's acceptable to simply leave the torrent running until someone gets on it or 4 or 5 days pass. 

In order to share your own stuff, you will have to make a torrent file (with your client) and register it on a tracker, then post it where others can start downloading.

If your interested in trying a exceptional private site, PM me and i'll get you started, Please only do this if you intend to try your best to keep a 1:1 + ratio.

---

### Post by P235 on 2007-09-26
Yes, you can run Azureus while you are online to share files even when you are not downloading.  When you have the complete file on your hard drive and are no longer downloading, you become a 'seeder' a.k.a. an uploader.  You can configure Azureus to stop torrents when they reach a specified share ratio and leave the program running without worrying about overuse of bandwidth.  

If you stop a torrent you are leeching (downloading) from that is not yet completed, you can resume your download at a later date or time so long as the torrent is still active.

---

