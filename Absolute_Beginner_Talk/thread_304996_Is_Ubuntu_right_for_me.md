---
title: "Is Ubuntu right for me?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by dmber on 2006-11-22
Hi.  Thanks a lot for reading this.  Sorry if the title wasn't descriptive enough, I wasn't sure what to put exactly.

My first question should be easy enough: I'm running Dapper from a live CD.  If "stuff" is working, does that mean it will work after an install: my monitor seems to be recognized fine, my wireless keyboard and mouse are working fine.

I'm thinking about making the switch to Ubuntu.  I've been a windows user for a while on my desktop computer, and I recently got a macbook for school.  I have been contemplating making the switch on my desktop to Ubuntu for a while now...I've just been "too scared" to do it.  I really only use my desktop for a few specific purposes and I was hoping someone could just tell me whether or not Ubuntu would be a fit with these purposes.  (Also, I'm not wanting to "replicate" windows on Ubuntu, I just don't see the point of having a bulky OS that I'm just sick of, if I can use Ubuntu, which I see as something that can teach me some stuff in the long run).

I collect live music.  This is 95% of what I use my desktop computer for.  So...I would need to be able to:

[LIST=1]
[*]Use Bit Torrent (Azureus)
[*]Listen to and Decode (to wav) then encode (to mp3) both FLACs and SHNs
[*]Burn Data DVDs
[*]Burn Audio/Video TS DVDs
[*]Surf the Net (Firefox)
[*]Office Functions (OOo)
[/LIST]

So, I know that I can use Azureus for BT, Firefox for the net, and Open Office.org for Office Functions.  I found a plugin on xmms.org for playing shn files on xmms.  To my knowledge, VLC plays flacs.  Is there a decoder for those two file types?

The other big thing I would like out of Ubuntu is the Beryl / Compiz multiple desktop graphical sweetness.  I have Virtue Desktops on my Macbook and I love it.  I have a feeling this is going to be the point where I get lost.  I read some of the HOWTo's and FAQs on Beryl and Compiz but I got lost.  I've never worked with Terminal before -- but I'm more than willing to learn.  Is that all do-able to set up?

Thanks for listening and any help you have.

Russ

---

### Post by Henry Rayker on 2006-11-22
Welcome!

BitTorrent is supported by a couple of different programs. If Azureus is what you're comfortable with, then that is what you can use.

I have transcoded FLACs to mp3s with no problem. I believe I had to install a codec or two, but it wasn't bad at all. No experience with SHNs

I've burned data DVDs with no problem on my laptop.

I'm not sure what a TS DVD is...

Surfing the net with Firefox is no problem at all...some sites, however, won't work (IE dependencies) or will take some work (flash, movie players in general).

OpenOffice is great. I know someone will come and say, "wait, it's not exactly the same because x is in y and whatever"...for me, it looks the same. I've worked in both a fair amount and found no HUGE differences. OpenOffice will even save to their formats.

If everything works on the disk, it -should- work on the installation...or it can be configured to work (I have heard of problems like that).

If possible, you could always make a little partition on your hdd and dual boot. See if you can get the features you need out of Ubuntu. If you can, you can just resize the partition over your Windows partition.


Hope that helps!

---

### Post by 23meg on 2006-11-22
It seems everything you want to do can be done under Ubuntu, and you're willing to invest some time to get things going the way you want. Give it a try, and if you run into any problems, don't hesitate to ask questions here.

---

### Post by agger on 2006-11-22
> **dmber said:**
> Hi.  Thanks a lot for reading this.  Sorry if the title wasn't descriptive enough, I wasn't sure what to put exactly.

My first question should be easy enough: I'm running Dapper from a live CD.  If "stuff" is working, does that mean it will work after an install: my monitor seems to be recognized fine, my wireless keyboard and mouse are working fine.

Yes, you should be able to count on that - whatever works on the live CD will work after installing, too.

When looking at your list:

> 
[LIST=1]
[*]Use Bit Torrent (Azureus)
[*]Listen to and Decode (to wav) then encode (to mp3) both FLACs and SHNs
[*]Burn Data DVDs
[*]Burn Audio/Video TS DVDs
[*]Surf the Net (Firefox)
[*]Office Functions (OOo)
[/LIST]


Then yes, you can do all of these things with no problems. The only thing I don't know is the virtual desktop thing - never used it myself. You could try installing Beryl og Compiz and getting it to work from the live CD, though, before taking the actual plunge - or you could make a separate partition for Ubuntu and dual boot until you felt like getting rid of Windows altogether.

---

### Post by Doug11 on 2006-11-22
As a "noob" to the world of Linux I can tell you one thing. I've been using Linux now for the last two weeks, four different distros I have tested and I keep coming back to Ubuntu Edgy. I like doing all the things you have stated in your list and more. Slowly things are starting to happen for me. So, my advice as a beginner is, have patience, do a ton of reading, and before you know it, you'll be doing what you want.

---

### Post by dmber on 2006-11-22
thanks a lot!  that's a really good idea to do a small partition so i can dual boot.  will i be able to use the files in linux that are on the "windows" partitions?

i'll just keep reading around....thanks for the votes of confidence.

---

### Post by PurplePenguin on 2006-11-22
If the live CD works for you, after a hard drive installation, it'll work even better (being on a CD slows it down quite a bit).
I recommend checking out [Automatix]("http://www.getautomatix.com/"), since it will let you install almost everything that you want (Azureus, DVD and other multmedia codecs, etc) that isn't installed by default.  Just follow the instructions on the site to the letter and you'll be off and running in no time.  It makes things so much easier.

As for AUDIO/VIDEO TS DVDs, I'm assuming that you're referring to making audio or video DVDs that will play in your average set-top player.  Shouldn't be a problem.  You can even get a number of programs that basically do what dvdshrink used to do under windows (shrinking a full size DVD onto a normal size disc) - this makes the VIDEO TS directory.

You'll be able to read your Windows partition without a problem, too.  It's just the other way around that doesn't work that well (that is, reading linux partitions in windows).

Keep ubuntuforums.org bookmarked, too, and you'll have absolutely no problems. :)

---

### Post by dmber on 2006-11-22
thanks a lot.  i'll definitely put automatix to use.  i was just reading in another thread about using remote desktop with ubuntu and a macbook.  that's one thing i forgot to put in my list of "have-to-be-able-to's".  thanks for the help!

---

### Post by PurplePenguin on 2006-11-22
Oh, about ripping audio tracks into FLAC... Sound Juicer does this automatically (that is, you don't have to convert to WAV then to FLAC, it does it all in one shot).  You just have to go into the program's options and make sure that FLAC is set as the default output file type (mine's set to OGG right now).

Sound Juicer and other programs like it are very easily installed through Ubuntu.  They make it very easy. :)

---

### Post by 23meg on 2006-11-23
> **PurplePenguin said:**
> 
Sound Juicer and other programs like it are very easily installed through Ubuntu.  They make it very easy. :)
Actually Sound Juicer is installed by default.

---

### Post by derjames on 2006-11-23
You can give it a try using VMware, 
Currently I am running Ubuntu Edgy under Windows XP using VMware server in a Core 2 duo Laptop, I am pretty impressed of the performance. Ubuntu really runs quite fast. Also is a good way to test software without modifying your hard drive (i.e. adding partitions)...

---

### Post by glotz on 2006-11-23
Ubuntu is the perfect choice for you.

---

### Post by PurplePenguin on 2006-11-23
> **23meg said:**
> Actually Sound Juicer is installed by default.

Ah, my bad. :)  Well, then, that just makes it one step easier! :p

---

### Post by namah on 2006-11-23
there are some nice essays on windows/linux comparisons and whether on not Linux is for you here

[http://psychocats.net/essays/index.php](http://psychocats.net/essays/index.php)

Scroll down to the computer section

---

