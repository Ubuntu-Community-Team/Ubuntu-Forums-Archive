---
title: "G4 iBook, 1.33ghz, 768MB RAM, help needed"
date: 2008-02-16
forum: Apple PPC Users
---

### Post by AuburnTiger on 2008-02-16
Ok, here's my story. I've had my iBook for around 3 years now, and the HD finally crashed on me. I've ordered a new one, and plan to have it installed (with the help of the Digital Resource Lab here) on Wednesday or Thursday. 

I'd really like to give Ubuntu a shot before I decide to put OS X back on. First of all, my question is: what version do I need to download? On the website, I see options for X86 and other versions, but no PPC versions.

Secondly, how difficult will it be to install? I've never installed anything on a blank HD before, and though I don't forsee it being too difficult, I am a bit apprehensive. 

All of your suggestions and comments are welcome. Thanks so much.

---

### Post by AuburnTiger on 2008-02-16
Hmm, I don't know how I missed the giant sticky at the top of this forum. Perhaps my questions can be answered there, I'll go have a look.

---

### Post by stream303 on 2008-02-16
Welcome aboard!

The nice thing is that you don't have to give up OSX.  Setting up for a dual boot is easy when you first install a new hard drive.  You could partition the drive in half, and install OSX on the first partition, and leave the other half as free space.

Then when installing Ubuntu, you allow guided partitioning to use the free space it finds, and it will set up a boot prompt allowing you to choose between OSX and Ubuntu.

Going with the LTS 6.06x version is fine, although many of us run 7.04 Feisty or even 7.10 Gutsy.  Typically the "alternate" install images have more success than the live-cd's, but nothing is written in stone.

You can navigate through these directories and download an iso if you like:

[http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/)

---

### Post by AuburnTiger on 2008-02-16
Would it be possible to install Ubuntu BEFORE OS X, and still have a dual boot? I ask this because my install discs are at my parents house, whereas I could just download 7.04 Feisty.

And I'm ashamed to say that I don't know what an "alternate install image" is. :confused:

I was just under the impression I could download the software, put it on a disc, then boot it with the disc.

---

### Post by stream303 on 2008-02-16
I've never done it this way, and I'm not sure how OSX reacts to seeing Ubuntu on the first partition.  Anyone?  I'm sure that a quick edit of /etc/yaboot.conf can fix that up.

Thing is, I don't know your experience level, so I'm hesitant to recommend anything that might put you off as soon as you boot, and am sticking to the easiest scenario.

You can do a full install of Ubuntu in the meantime to try it out, and when the OSX disks are available, maybe you'll have a better idea of which version of Ubuntu you'd like to run, how much space  you'd like to give over to partitioning, etc.  Kind of get your feet wet knowing that you'll be reinstalling later anyway.  Might be good practice, I dunno. :)

The "alternate" images are not live like the Desktop images, that is, the alternates go straight into installing on your disk in a text-based format, rather than letting you bring up a full gui version that runs temporarily from the cd drive - although the live Desktop cd's will also install to the HD if you like.  The alternates will install a full gui, it is just the initial installation that is text-based.

---

