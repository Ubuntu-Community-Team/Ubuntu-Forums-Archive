---
title: "Music editing software"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Snoo on 2007-04-18
Hiya, New ubuntu newbie.

Got a few things on my mind but everything running fairly smoothly and I'm quite keen to try to solve somethings myself first (I'll be back!)

I was wondering though, I like to mess around with tunes and under XP i was using software like Sony Acid, Steinberg Wavelab and the like.

Can anyone reccomend stuff to install for Edgy Eft? Trying to slowly wean myself off of XP.

Thank you all.

Snoo

---

### Post by lamalex on 2007-04-18
give audacity a try, it's decent for what I do which isn't much. It probably has more power than I'm using it for, you could also check out ubuntu-studio, it's an ubuntu distro for that kind of thing. it's going to be released sometime in april

---

### Post by Marsolin on 2007-04-18
There are a number of really solid audio editors for Linux.  See [here]("http://linuxappfinder.com/multimedia/audioeditors") for a list. [Audacity]("http://linuxappfinder.com/package/audacity"), [Jokosher]("http://linuxappfinder.com/package/jokosher"), [soniK]("http://linuxappfinder.com/package/sonik"), and [LMMS]("http://linuxappfinder.com/package/lmms") are some to start with. Those are only the tip of the iceberg though.

---

### Post by Snoo on 2007-04-19
Thanks guys. I'll have a dig through those links.

---

### Post by pppetter on 2007-04-19
Hi there! 

Also keep your eyes open on this project, might be interesting when it arrives!
[http://ubuntustudio.org/]("http://ubuntustudio.org/")

Also look at their specs page for programs in the wiki.

---

### Post by Rexbron! on 2007-04-19
If you are running fiesty, ```
sudo aptitude install ubuntustudio-audio
```.

That will get all the packages you need to get started.

---

### Post by evilc on 2007-04-19
There is also a good deppoer prog called Gnome wave cleaner just search for it and check uot it's web site.

---

### Post by s9am_me on 2007-04-19
never tried this program but I heard its good.  Its a multi-track audio program similar to Pro-Tools...  [http://ardour.org/](http://ardour.org/)

---

### Post by Snoo on 2007-04-20
> **Rexbron! said:**
> If you are running fiesty, ```
sudo aptitude install ubuntustudio-audio
```.

That will get all the packages you need to get started.


Running Edgy sadly.

Keep 'em coming folks! :guitar:

---

### Post by Snoo on 2007-04-20
> **Rexbron! said:**
> If you are running fiesty, ```
sudo aptitude install ubuntustudio-audio
```.

That will get all the packages you need to get started.

Just upgraded to fiesty.

Had no luck though:

> Couldn't find any package whose name or description matched "ubuntustudio-audio"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used

??

---

### Post by epicaricacy on 2007-05-04
> **Rexbron! said:**
> If you are running fiesty, ```
sudo aptitude install ubuntustudio-audio
```.

That will get all the packages you need to get started.

thank you!

---

### Post by Matt Yun on 2007-05-04
There is a fairly [comprehensive list of multimedia projects]("http://debianlinux.net/multimedia.html") with debian packages at debianlinux.net.  The ubuntustudio-audio metapackage, mentioned above, will get you many of these projects.

Take a look at the Audio Synthesizing and Editing Tools.  I think that [Ardour]("http://ardour.org/") and [Rosegarden]("http://www.rosegardenmusic.com/") are the most mature of these.  

[Audacity]("http://audacity.sourceforge.net/"), which someone mentioned above, isn't really a sequencer; it's a wave editor, which is useful for recording, cleaning and trimming your samples.

If you're interested in [FastTracker2]("http://en.wikipedia.org/wiki/Fast_Tracker")-clone MOD trackers, these don't appear on the debianlinux.net list.  Linux FastTracker2 clones include [SoundTracker]("http://www.soundtracker.org/"), [MilkyTracker]("http://www.milkytracker.net/") and [CheeseTracker]("http://en.wikipedia.org/wiki/CheeseTracker").  

I'm playing around with a tracker called [Psytexx2]("http://warmplace.ru/docs/psytexx2/").  The Psytexx2 developer ported his program to Windows, Linux and PalmOS.  (I use it primarily on my Palm Lifedrive).  However, I'm a complete novice with this stuff.

---

### Post by k1001001 on 2007-05-04
What repository is ubuntustudio-audio in? I couldn't find it either.

I'm really excited about it though. Me, Ardour, and JACK just do not cooperate very well.

---

### Post by Matt Yun on 2007-05-04
> **k1001001 said:**
> What repository is ubuntustudio-audio in? I couldn't find it either.

I'm really excited about it though. Me, Ardour, and JACK just do not cooperate very well.

I'm using Feisty with main, restricted, universe, and multiverse repos enabled.  See the [Ubuntustudio Wiki]("https://wiki.ubuntu.com/UbuntuStudio/PackageList") for a list of packages.

---

### Post by imdidactic on 2007-05-04
Use [hydrogen]("http://www.hydrogen-music.org") for your beats.

---

### Post by k1001001 on 2007-05-05
I'm still using Dapper, so that may be why I can't get the packages. Do you have to use Feisty in order to run Ubuntu Studio?

---

### Post by Najand on 2007-05-05
> **Snoo said:**
> Just upgraded to fiesty.

Had no luck though:


Quote:
Couldn't find any package whose name or description matched "ubuntustudio-audio"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used

??

You have to enable all univer and multiverse repositories.
Go to System -> Administration -> Software Sources.

---

### Post by DirtDawg on 2007-05-07
> **k1001001 said:**
> I'm still using Dapper, so that may be why I can't get the packages. Do you have to use Feisty in order to run Ubuntu Studio?

Yes, but I also run Dapper and over the last few days I have installed most everything mentioned here. Ardour was tricky (but awsome), Audacity won't pick up my usb mic due to an apparent bug that was fixed later (but edits okay), Hydrogen's in the repos, and there's a better, more up-to-date version of Lmms [here]("http://ubuntuforums.org/showthread.php?t=323225") than what's in the repos, if you want to screw around with some farily simple loops/beats.

---

### Post by mahiyar on 2007-05-07
As far as audacity is concerned try the beta version its awesome. I installed it from here [B][http://ubuntuforums.org/showthread.php?t=419358&highlight=audacity+beta](http://ubuntuforums.org/showthread.php?t=419358&highlight=audacity+beta)

[/B]Please read the complete post there are a few corrections to the original.

---

