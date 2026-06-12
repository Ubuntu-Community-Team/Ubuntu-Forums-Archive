---
title: "New Ubuntu user (some help please)"
date: 2007-04-22
forum: Apple PPC Users
---

### Post by Atp on 2007-04-22
I've been a mac guy for years, and I just recently decided to download ubuntu.  It seems to be running quite well on my powermac g5.  I'm running it off an external harddrive.  I have 2 screens one 23" cinema display, and the other a 15" cinema display.  Both are the older type (with the big white border around it).  I'm lovin' the interface, but I'm running into some problems:

1. My second moniter (the 15") is just a blank white screen.  I really have no experiance in changing files so when some other threads told me to tamper with some of the system files I wasn't sure if that would work for me or not so I decided to ask you first.

2.  Changing resolutions:  Dosn't work.  Basically i change to any resolution and it just looks like the refresh rate isn't right or somthing.  It messes up the whole screen so I can barly see anything, and then I expect it to go back to the resolution that works after a while, and it does, but to add insult to injury, that resolution is messed up too, only MORE messed up.  I thought it was supposed to go back to the resolution that it was just on...

that crappy 1024x768 resolution that I cant stand compared to the 1900x1000 or whatever it is on osx, (i cant even find it in the list anymore.)

... but it dosn't.  I'm getting tired of this tiny resolution.  I have no room to work and I feel like I'm using windows when its this small.

3. The software.  Ok, other than the resolution, so far ubuntu seems pretty cool.  The software kinda pisses me off though...  I know that isn't related to ubuntu at all, just not enough developers care enough to make it available.  GAIM is the worst chat cliant I have ever seen, and i just can't stand firefox.  I know its hella better than IE, but where is camino or safari?  Oh yeah, thats right, they are only for mac.  Any chat cliants or browsers for linux that don't suck?  If you know of any, please let me know.

4. Everything else seems pretty cool.  I can't really figure out what it did to my external HD that I installed it on.  Before installing i partitioned it into 2, one 600 gig section for storage, and one 100 gig (freespace) section for linux.  After installing, it says its now in 4 partitions.  I can't really figure this out since one says is only 20 gigs, one is 400 gigs, and the other two seem to have just a few megs.  Not exactly sure, but in osx only 1 shows up and it has 600 gigs so i'm happy and i wont worry about this.

If you have answers for any of these points i would be very happy!  Thanks so much!

---

### Post by spin2cool on 2007-04-22
1) If you're having resolution/xorg problems, you'll want to look at this:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Also, do a thorough search of these forums and google to find other people that have had similar problems and resolved them.

3) Personally, I find firefox to be superior to safari in about every way.  Perhaps you just aren't used to it??  Have you looked into the extensions, which let you customize the browser about any way you want?  Have you gone through the preferences of GAIM and tweaked it?  Personally, I don't like the defaul huge buddy list w/ icons, so I shrink it to a more standard looking list - there are lots of other options and tweaks in 'plugins'

4) want to see how your hd is partitioned?  install gparted (if it isn't already), then run it:

sudo apt-get install gparted
sudo gparted

---

### Post by Auria on 2007-04-22
For a better instant messaging program, perhaps tell us what services you use (MSN, AIM, Jabber, etc.). Gaim does a lot of services, but if you only use one we can perhaps tell another app that focuses on a single one.

What do you find wrong with FF?

---

### Post by phidia on 2007-04-22
If you're not happy with firefox try ephinany. It should be available through synaptic.

---

### Post by 3rdalbum on 2007-04-23
I personally can't see how Safari or Camino is better than Firefox. You might also want to try Konqueror; I can't guarantee that you'll like it, but it's very powerful.

While you're at it, snag Kopete from the repositories - it's an alternate chat client.

---

### Post by gnaunited on 2007-04-23
> **Atp said:**
> I'm getting tired of this tiny resolution.  I have no room to work and I feel like I'm using windows when its this small.

What does the resolution have to do with Windows? I REALLY would like to know cause last time I checked Windows supports whatever resolution your hardware does.

---

