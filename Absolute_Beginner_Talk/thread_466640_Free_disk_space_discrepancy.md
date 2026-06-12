---
title: "Free disk space discrepancy"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by doublecheese on 2007-06-06
How come when I view my filesystem through Disk Usage Analyzer it says:

```
capacity 225.9 GB (used: 2.4 GB available: 223.5 GB)
```

And when I view that same filesystem through the File Browser it says:

```
Free Space:  211.8 GB
```

?

Which one is correct and why does it give me two different available space numbers (223.5 and 211.8)?  Where did that 12 GB go?  I have very little software installed and no personal files yet as I am just now getting the machine set up.  

Using 7.04.....

---

### Post by CaptainInsaneO on 2007-06-06
Some of the file sizes in your filesystem are unreadable by Nautilus. That's why there is a discrepancy.

Hope this helped. :D

---

### Post by doublecheese on 2007-06-06
It does make sense I just don't understand how I'm using up 12GB of space!

Installed from a CD image.  Have downloaded multimedia codecs, two media players, video drivers, essential updates, and Open Arena.

I guess what I'm asking is...how did I get so bloated?   :)

---

### Post by punx45 on 2007-06-06
most likely a discrepancy in the counting methods for quantities of memory.   some use the more accurate method where one unit of a magnitude equals 1024 units of one magnitude lower, e.g. 1 MB = 1024 Kb and so on; and others round everything by even 1000s.   same reason you buy a disk that says "120 GB" on the box, and when you put it in it ends up being 114.6GB*   Thats my guess.


*estimated.

---

### Post by NeoLithium on 2007-06-06
5% of the drive space is reserved for the root file system, in case your hard drive fills up; that way you can still log and not have to worry about being unable to do so due to a full hard drive.

---

### Post by ryanVickers on 2007-06-06
Yes, some files could be unreadable by nautillus, and one more thing:  Go into System > Admin. > System monitor and check out the filesystems tab.  You'll notice that "free" and "available" are 2 *different* numbers.  Why this is still escapes me, but did this clarify?  I'm guessing that the 12Gb isn't actually used, but it is unusable, go it? :)

Edit: Oh, I wish this would update as new thingws come in.  Those are both excellent suggestions!

---

### Post by NeoLithium on 2007-06-06
You bet. It's basically reserved space just in case. :)

---

### Post by Atomic Dog on 2007-06-06
> **punx45 said:**
> most likely a discrepancy in the counting methods for quantities of memory.   some use the more accurate method where one unit of a magnitude equals 1024 units of one magnitude lower, e.g. 1 MB = 1024 Kb and so on; and others round everything by even 1000s.   same reason you buy a disk that says "120 GB" on the box, and when you put it in it ends up being 114.6GB*   Thats my guess.
*estimated.

I find it annoying that drive manufacturers years ago started rounding to 1000 to sell drive sizes.  It causes confusion.  Why not just call a 150GB drive a 150 instead of 160.  Ticks me off all this marketing crap.  ...I work for a market research company, I see how companies pray on the ignorance of the consumer.  probably why I hate humanity.

---

### Post by CaptainInsaneO on 2007-06-06
> **doublecheese said:**
> I guess what I'm asking is...how did I get so bloated?   :)

That's an allergic reaction to a lil' something I like to call the 'Buntu Bug! ;)

---

### Post by punx45 on 2007-06-06
> **CaptainInsaneO said:**
> That's an allergic reaction to a lil' something I like to call the 'Buntu Bug! ;)

and all that newfangled desktop eye candy.   heck, my mac uses up something like 4GB just for *languages ill never use!*

---

### Post by NeoLithium on 2007-06-06
> **doublecheese said:**
> I guess what I'm asking is...how did I get so bloated?   :)

That's easy :) 5%(Approx) of 225.9GB = 12GB give or take a bit. :)

---

### Post by ryanVickers on 2007-06-06
> heck, my mac uses up something like 4GB just for languages ill never use!
Then why did you install the extra languages package!? ;)
(I don't have a mac but I know a little something...)

---

### Post by punx45 on 2007-06-06
> **Atomic Dog said:**
> I find it annoying that drive manufacturers years ago started rounding to 1000 to sell drive sizes.  It causes confusion.  Why not just call a 150GB drive a 150 instead of 160.  Ticks me off all this marketing crap.  ...I work for a market research company, I see how companies pray on the ignorance of the consumer.  probably why I hate humanity.
I agree
but really... would it be too difficult for them to give an exact bit count? 

[SIZE="1"][COLOR="Silver"][SIZE="3"][COLOR="Red"]super media drive! holds up to 2,576,980,377,600 binary digits![/COLOR][/SIZE][/COLOR][/SIZE]
as an aside, that figure courtesey of google caclulator which does conversions as well.   just search n gigabytes in bits, or any unit for that matter.

---

### Post by punx45 on 2007-06-06
> **ryanVickers said:**
> Then why did you install the extra languages package!? ;)
(I don't have a mac but I know a little something...)

silly, mac users dont have to bother with scary things like installing software! haha.

---

### Post by doublecheese on 2007-06-07
System Monitor:

Total:  225.7 GB, Free:  223.3 GB, Available:  211.8 GB, Used: 2.4 GB (1%)

Makes sense.  Thanks for the explanation.  I'm still learning the ins and outs of linux.  The numbers just seemed abnormal but it makes a bit more sense now.

---

### Post by Atomic Dog on 2007-06-07
> **punx45 said:**
> silly, mac users dont have to bother with scary things like installing software! haha.

Yea.  You're given little choices and are thankful for what mother mac provides :p

ps.  Don't forget to renew your .mac account for only $99/yr!

---

### Post by ryanVickers on 2007-06-07
> super media drive! holds up to 2,576,980,377,600 binary digits!
Not only would that be accurite, it would fool the general public way more then they think they are with the 1000 per Gb thing!  Can you immagine the average person... :lolflag: "OMG, my drive thing only has 200 giga thingies, this looks WAY better!" :p

---

### Post by CaptainInsaneO on 2007-06-09
> **ryanVickers said:**
> Not only would that be accurite, it would fool the general public way more then they think they are with the 1000 per Gb thing!  Can you immagine the average person... :lolflag: "OMG, my drive thing only has 200 giga thingies, this looks WAY better!" :p

I may be sent to Hell someday for it, but those types of people are going to make me rich. Very, very rich.

---

### Post by angryhomer17 on 2007-07-24
> **NeoLithium said:**
> 5% of the drive space is reserved for the root file system, in case your hard drive fills up; that way you can still log and not have to worry about being unable to do so due to a full hard drive.

Is there anyway to lower the amount of reserved space? How much journaling space does an ext3 file system really need? I have 71 mb free on a 300 gig hdd, and would like to add more files (hopefully I can get a half terabyte sata hdd soon, maybe 2)

---

### Post by ryanVickers on 2007-07-24
You filled up a 300Gb drive completely!?  What on earth are you doing!? :p

I've seen 750Gb drives in average stores (vs. high-tech/high-end stores), and I thi9nk 1Tb drives are on their way soon!

---

### Post by angryhomer17 on 2007-07-25
Actually...
300 gig-- 100% full mp3 and flac
200 gig--mp3 bckp, ogg, flac (that won't fit on 300 gig), dvd bckp (no dvd burner on my laptop) pics bckp
40 gig--(from old laptop) dvd backup
40 gig--(this laptop) ubuntu, docs, pics, etc.

Total (actual useable space) ~500 gig

So I need lots of dvd's (blueray would be nice) to back up all my flac, which backs up my cd's or a large hdd. I can get a 500 gig sata-300 for ~100, 120ish. 750 gig is running ~$250 and 1 tb is ~$400. So I can get 2 tb for $400 with 500 gig drives.That also spreads the data out. I really need a desktop.

---

### Post by ryanVickers on 2007-07-28
Wow, sounds like you should just buy a 10Tb RAID server and just plug into that! :p

Why would you have flac files though?  Correct me if I'm wrong, but doesn't that stand for "Free Loss**less** Audio Codec", which means it's like a .wav file; super high sample rate (~10 times more than really good quality)!

---

### Post by saltydog on 2007-07-30
Did you have a look into root's Trash folder??

---

### Post by angryhomer17 on 2007-08-04
@ryan---yes flac is free lossless audio codec, and yes it is superior to most (if not all) codecs in terms of lossless quality (at least as far as I have been willing to research). Why do I use it? One, I hate mp3. It sucks. Poor quality, poor sound, mutilates the music, etc. Why not ogg, bc that is lossy too. Why do I care about it being lossless? Well, because it's a bckp for my music, it's sounds superb (exactly as the original cd), and because I don't have to worry about a new, and better, codec coming out and cursing myself for converting lossy to lossy (blech!).

Saying that flac is ~10x better than a good mp3 (i assume mp3), is true, except that mp3 sucks. Even at 320 kb/s. I am really not worried about space (well except when I run out), and bc it is relatively cheap. Oh, and I am not playing my music on crappy speakers. I certainly don't have the best, or even really good, but they are superior to most desktop speakers. Sony SS-MF650H and 125 watt sub.

@saltydog---I don't know if looking into root's trash folder was directed at me....but if it was, I do not have a trash folder on my external hdd. So no problem there. It's just extra storage space, ext3 formatted, no os.

---

### Post by ryanVickers on 2007-08-08
You sound like someone who would also enjoy a nice $60,000 LP stereo system instead of CD's!

---

