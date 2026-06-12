---
title: "[SOLVED] Making a DVD9 backup copy"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by dylanologist on 2007-09-14
I ripped a few of my DVDs in their entirety using Vobcopy.  Now I have some directories with .vob .bup and .ifo files. I would like to be able to burn those DVD directories to DVD9s (ie. I don't want them compressed).

I'm just wondering, if I burn those directories as data files onto a DVD9, will that make for a video DVD playable on my standard DVD player?  Or do I need a program to convert those files and that will produce a disc image for burning?

---

### Post by Nikitas350 on 2007-09-15
Make two folders in the dvd. One called "VIDEO_TS" and one "AUDIO_TS". Put all the files in the folder "VIDEO_TS" and enjoy.... (i hope) :popcorn: (the .vob and .ifo files are files of the dvd-video format)

---

### Post by rfurman24 on 2007-09-15
I would like to know if this works. I asked this question recently with no replies.

---

### Post by Kilz on 2007-09-15
The best and easiest way to backup dvd's is with k9copy imho.

---

### Post by dylanologist on 2007-09-16
I'll test that theory tomorrow (Mon) with a dual-layer DVD.  Hope it works, because that would be very simple.  I'll post the results Monday afternoon or evening.  As for k9copy, I've tried it and I do like it, but I couldn't figure out if there was a way to copy DVDs without compressing the data to fit onto a DVD5, which is not what I was aiming to do with some of my favorite DVDs.

---

### Post by mc4man on 2007-09-16
Your certainly headed for disappointment at the moment. 1st. you can only burn from an .iso or you'll end up with a data disc not a dvd video.  2nd. dual layer disks need to have the layer break set properly or you're dvd player will play layer0 and then stop.
I use k9 for ripping only (use progs. in wine for processing, build/burning) but you can set the dvd size higher in settings to prevent it from transcoding and also couple it with k3b for burning. can't tell you if they handle dual layers properly but it's your best bet at the moment

I got some dl's coming in the mail - am going to try k9/k3b next week
verbatim +r dl's are the brand/type  to use  hands down the best

---

### Post by newman on 2007-09-16
I tried k9copy but it kept crashing. Also it doesn't have the options DVDShrink has -ie, compression settings, aec, etc. One more thing I don't like about installing k9copy and k3b is the fact that they're not native gnome apps and they install all the kde libs. , but that's just me...

---

### Post by crav on 2007-09-17
Question: How to backup DVD9 to DVD5?

---

### Post by newman on 2007-09-17
> **crav said:**
> Question: How to backup DVD9 to DVD5?


I use DVDShrink in Wine and save as .iso then burn with GnomeBaker and it works fine.
You can use K9copy if it work on your system.

---

### Post by mc4man on 2007-09-17
While I never used k9 to transcode(shrink) a title I'm sure in does okay when the compression isn't alot or when just backing up the main title.  It will crash on structure protected titles if you don't make some adjustments

---

### Post by newman on 2007-09-17
[QUOTE=

I got some dl's coming in the mail - am going to try k9/k3b next week
verbatim +r dl's are the brand/type  to use  hands down the best[/QUOTE]

please let us know who they work.  I haven't burned any DL discs yet, but I've had xlnt luck with Sony and Fuji brand 4.7GB Taiyo Yuden Japanese made discs.

---

### Post by newman on 2007-09-17
> **mc4man said:**
> While I never used k9 to transcode(shrink) a title I'm sure in does okay when the compression isn't alot or when just backing up the main title.  It will crash on structure protected titles if you don't make some adjustments

What sort of adjustments? I had it sort of working, but it crashes

---

### Post by mc4man on 2007-09-17
It's totally dependent on the type of s.p.(if that's the issue)
have an example(title name) or remember error message - if any

---

### Post by Drakkor on 2007-09-17
I just used K9copy,and did a default copy and burn with K3b,and it worked great, but actually I just tested it out on a DVDRW, rewritable DVD disk,and it by default shrunk it to 4.4 GB , which I had a disk for , plays fine !! :)

---

### Post by Drakkor on 2007-09-17
Nevermind you want uncompressed, try Settings>Configure k9copy>DVD>and make the DVD size 8.5GB or what ever you; can fit to the disks you have ! :)

---

### Post by dvdgorila on 2007-09-17
You can try imgburn in wine.

---

### Post by dylanologist on 2007-09-17
I'm trying the method of using k9copy with Settings>Configure k9copy>DVD set to 8000 MB for the size.  Hopefully I'll be able to see if it works tonight.  I hope so, because I don't want to waste any more of these DL discs.  They're not that cheap.

---

### Post by brennydoogles on 2007-09-17
> **newman said:**
> I tried k9copy but it kept crashing. Also it doesn't have the options DVDShrink has -ie, compression settings, aec, etc. One more thing I don't like about installing k9copy and k3b is the fact that they're not native gnome apps and they install all the kde libs. , but that's just me...

I actually wrote a BASH script to make an exact copy of a DVD into an ISO, which can then be burned directly onto a DVD of the correct size (meaning if it is a newer DVD you may need DL DVDs), or you can use VLC Media player to watch the resulting ISO. You can download the most recent version [HERE]("http://ubuntuforums.org/attachment.php?attachmentid=43447&d=1189773755"), and view a thread about the tool [HERE]("http://ubuntuforums.org/showthread.php?t=545380")

---

### Post by Drakkor on 2007-09-17
Good Luck with that dylanologist, I would be curious to see if that worked also, I've been too cheap to actually buy DL disks, I do have a DL burner, but the 4.7 shrunk disks seem to work fine, been waiting for the DL discks to go down,lol  :)

---

### Post by newman on 2007-09-17
> **Drakkor said:**
> ... I've been too cheap to actually buy DL disks, I do have a DL burner, but the 4.7 shrunk disks seem to work fine, been waiting for the DL discks to go down,lol  :)

same here!:)

---

### Post by mc4man on 2007-09-18
probably never going to drop below 1.50 - 2.00 ea. - at least for  verbatim's

---

### Post by Drakkor on 2007-09-18
That's really not bad, I think the last time I looked, they where about $5bucks apiece,lol :)
It's really too bad that they're no good movies to burn anymore,lol :)

---

### Post by dylanologist on 2007-09-18
I generally have used 4.7 discs myself, but I have a few movies that are my absolute favorites that I would like to back up in full quality.  I admit, I haven't noticed any significant differences in the quality while watching on my 24" SDTV, but nevertheless it would be nice to have the option of burning DL discs in Ubuntu (I've done it just fine in XP).

I just burned a 7.5gb ISO that I created using k9copy (having adjusted the settings as described in a previous post).  I used GnomeBaker to burn the image onto a DVD+R DL, and when burning was finished I received the following details from the program:

Executing 'builtin_dd if=/media/secondary/DVDs/rulesofthegame.iso of=/dev/sr1 obs=32k seek=0'
/dev/sr1: splitting layers at 1956624 blocks
/dev/sr1: "Current Write Speed" is 2.5x1352KBps.
/dev/sr1: flushing cache
/dev/sr1: closing track
/dev/sr1: closing disc

I hope that the "splitting layers" comment means that the DVD was properly formatted to fit onto the Dual Layer disc.  I'll test it when I get a chance today to see if it works without a hitch.  Didn't have any problems playing back in VLC, but standalone players can sometimes be more finicky.

---

### Post by dylanologist on 2007-09-18
Here's the process I used to burn an uncompressed DVD9:

In a terminal I used the command:

vobcopy -m -o /directory

This copies the entire contents of the DVD into the desired directory.  Then I used k9copy to create an .iso file.  In k9copy I went to:

Settings>Configure k9copy>DVD>DVD size = 8000 MB (it doesn't seem to want to go any higher than that)

After I changed the settings in k9copy, I found that I had to restart the program in order for it to register the new settings.

That created an .iso of the DVD that wasn't compressed.  Finally I burned the .iso using GnomeBaker.  This left me what appears to be a exact replica of the original DVD, and it plays just fine in both VLC and on my standalone DVD player.  You could probably skip the first step and jump right into k9copy, though I find, in my very limited experience, that Vobcopy does a better job with copy protected DVDs.

Hope that solves the problem for anyone else trying to create backup DVD9 copies of their DVDs.

---

### Post by andrew.46 on 2007-09-20
Hi,

 I noticed the thread has been marked solved but I have a few thoughts anyway:

> **dylanologist said:**
> I ripped a few of my DVDs in their entirety using Vobcopy.  Now I have some directories with .vob .bup and .ifo files. I would like to be able to burn those DVD directories to DVD9s (ie. I don't want them compressed).

I'm just wondering, if I burn those directories as data files onto a DVD9, will that make for a video DVD playable on my standard DVD player?  Or do I need a program to convert those files and that will produce a disc image for burning?

There is a very cool way of copying and converting to .iso from the command line, it works brilliantly for the 8.7gig disks:

```
$ cd Desktop
$ vobcopy -v -m /media/cdrom0
$ cd <MOVIE Folder>
$ mkisofs -v -dvd-video -o ../MOVIE_Name.iso .
```

And then burn to dvd. I have drawn this from one of my own pages:

[http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#dual](http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#dual)

which has a few more details. But basically you only need 2 files: vobcopy and mkisofs. (plus libdvdcss if dvd is encrypted)

                Andrew

---

### Post by dylanologist on 2007-10-26
Thanks Andrew.46.

I marked the thread solved because I did manage to get the backup I was looking for, but when I originally posted this topic I was hoping to find a solution somewhat more along the lines of what you just gave us.

The way I described has already led me to the problem of forgetting that I had changed the settings in k9copy, so I created a couple of uncompressed .iso dvd files when in fact I wanted compressed versions.

From now on, I'll use k9copy for making compressed backups, and I'll use your command line method for creating uncompressed backups.

Thanks again for your very useful contribution to this thread.

---

