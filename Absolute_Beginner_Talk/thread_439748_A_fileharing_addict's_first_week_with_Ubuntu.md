---
title: "A fileharing addict's first week with Ubuntu"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by stylofone on 2007-05-11
I felt the urge to share my thoughts a week after installing Feisty. I've been a Windows user for about 10 years, before that it was Amiga, C64, and even  TRS-80, haha! Yes I was on the ark!

1. On balance, you can do everything you need with free software, just as easily as you can with commercial software. Under Linux, a few things are trickier, many things are simpler. But everything is cheaper. I kept my Windows 2000 partition in case I needed to dip into it to get things done. I haven't had to boot it at all!

2. I am a passionate supporter of file sharing, and using Ubuntu gives me a very good feeling. The excellent functionality of Linux proves the merits of the info-freedom model, that everything should be free, and life will be better. 

3. Video and audio successes: Totem plays all my media files. CD Juicer extracts CDs. I am abandoning mp3 and will now favour ogg vorbis. DVD::rip rips DVDs and transcodes to xvid. Avidemux transcodes other video files. OGMdemux and Avidemux allow me to convert multiple-stream ogm files into avis which I can watch on my Mediagate MG-35. All of this is simpler under Ubuntu than it was using the Windows tools I had amassed after exhaustive reading of videohelp.com!

4. Filesharing successes: Nicotine+ works for soulseek. Amule works for emule. KTorrent snares bittorrent files. My life is complete! Azureus gave me grief so I'm sticking with KTorrent.

5. Other functons: K3B burns CDs and DVDs. Gimp is good enough to replace Photoshop for my purposes. I will miss Irfanview, but Gthumb is good. Filezilla is a familiar friend from the Windows World. Seamonkey installs and works well for web browsing and html WYSISYG editing. Points 3, 4, and 5 were all a revelation. I  thought I'd have to compromise on some of these, but they all equal or surpass the Windows functionality. I have even replaced an entire windows cataloging program with a single linux command: 
ls -RCla media/cdrom0> /home/stylofone/stuff/dvd_list.txt
Sweet!

6. I'm still working on: finding a two-pane file manager like Directory Opus. The best available fall well short. Also, a Desktop Search as good as Copernic. 

7.Music making is yet to be explored. Finding sound editors, sequencers and the like, to replace my beloved Reason, Acid and Cool Edit, could be Linux's biggest test yet.

8. My Mediagate MG-35 Network Media Player will only see files on a Windows Network which allows access without a password. It is POSSIBLE for Ubuntu to do this, but it gave me lots of grief and then it broke. So my Ubuntu PC will stay invisible to the Mediagate.:-(. This is as much a fault of Mediagate as it is Ubuntu. Solution: just use USB, until I can afford a NAS which both systems can see, and move the music and video collection there.

---

### Post by irish_flu on 2007-05-11
> **stylofone said:**
> 
7.Music making is yet to be explored. Finding sound editors, sequencers and the like, to replace my beloved Reason, Acid and Cool Edit, could be Linux's biggest test yet.


Hey pal, check out "Audacity" for sound editing.  I use it in both Windows and Linux (there's a Mac OS version too!).

You can grab it right from the Repositories; it's in the "Multimedia" section of the "Universe" Repository in Synaptic.

Have fun, I think you'll dig it.

You might also wish to check out "Ubuntu Studio"; it's brand-new, and I don't know much about it, but their website looks cool.   :lolflag:

---

### Post by k33bz on 2007-05-11
> **irish_flu said:**
> 

You might also wish to check out "Ubuntu Studio"; it's brand-new, and I don't know much about it, but their website looks cool.   :lolflag:

whats the link

---

### Post by pirothezero on 2007-05-11
For 6, you have beagle. If you mean desktop search as in something that indexes all your files.

For 7, you may want to check out the Ubuntu Studio, not sure if that was released or not. 

For 4, if you get into using newsgroups for your file leeching (not so much file sharing) then check out SABnzbd or perlnzb if you like the console application side of things.

Glad to see you had a lot of success with all your desires. It seems like you've used linux before, I am a little surprised to see this much success come from someone who just decided to try out Ubuntu. So have you?

---

### Post by pirothezero on 2007-05-11
> **k33bz said:**
> whats the link
[http://ubuntustudio.org](http://ubuntustudio.org)

---

### Post by stylofone on 2007-05-11
Thanks for that suggestion. I actually tried the Windows version of Audacity once and was pretty impressed. It didn't have all the features of Cool Edit, but it looks really solid and I think I won't be disappointed.  I'm definitely going to give Ubuntu Studio a try, but there's a lot for me to do before that, relearning everything after 10 years of Windoze! I'm enjoying it though.

> **irish_flu said:**
> Hey pal, check out "Audacity" for sound editing.  I use it in both Windows and Linux (there's a Mac OS version too!).

You can grab it right from the Repositories; it's in the "Multimedia" section of the "Universe" Repository in Synaptic.

Have fun, I think you'll dig it.

You might also wish to check out "Ubuntu Studio"; it's brand-new, and I don't know much about it, but their website looks cool.   :lolflag:

---

### Post by stylofone on 2007-05-11
Well, I'm not quite a raw beginner. My first internet experience was with Shell Accounts, back in the 90s, using Unix command line, with lynx and similar text progs. I also do a tiny bit of administration on a Unix-based system at work. And the combination GUI and CLI reminds me of the old Amiga days. Yes, I'm a life-long geek!! Also, I think I got lucky with my hardware, it just seems to like Ubuntu. 

Oh yeah, a while ago I tried out a Knopix live CD which just crashed and misbehaved, and I gave up on it after less than an hour, so I guess this is really my 2nd go at Linux. 

I'm also the family help desk... the one who gets to show the grandparents how to get online. They struggle with Windows. I really think they'd be able to handle Ubuntu just as well. 

Or am I just having fun with a new toy and it's blinded me to the reality??? 

I've installed Beagle, I just need to poke around to make it work.

> **pirothezero said:**
> For 6, you have beagle. If you mean desktop search as in something that indexes all your files.

Glad to see you had a lot of success with all your desires. It seems like you've used linux before, I am a little surprised to see this much success come from someone who just decided to try out Ubuntu. So have you?

---

### Post by pirothezero on 2007-05-11
> **stylofone said:**
> I've installed Beagle, I just need to poke around to make it work.
if you run
```
ps aux | grep beagle
```
you should get (if its active, if you get nothing, then go down to the beagle-shutdown and start from the export command.
```

xxx@jackson:~$ ps aux | grep beagle
xxx    10911  0.0  7.8 106352 40536 ?        Sl   May10   0:04 beagle-search --debug /usr/lib/beagle/Search.exe --icon
xxx     10912  0.2  5.5  91096 28592 ?        Sl   May10   0:36 beagled /usr/lib/beagle/BeagleDaemon.exe --replace --bg
xxx     15661  2.1  4.2  65140 22072 ?        SNl  May10   1:48 beagled-helper /usr/lib/beagle/IndexHelper.exe
xxx    18672  0.0  0.1   2880   748 pts/0    R+   00:31   0:00 grep beagle
```

if you want to set the indexer into over drive and index everything quicker by over taking cpu cycles then do this
```

$ beagle-shutdown
$ export BEAGLE_EXERCISE_THE_DOG=1
$ beagled

```

Not much else to it.

---

