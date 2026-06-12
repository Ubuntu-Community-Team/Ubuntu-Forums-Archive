---
title: "Best Software for CD/DVD Burning?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-05-19
I tried using the Nautilus window to burn last night and ended up making 4 coasters.  As I recall, Windows Explorer in XP also sucks for burning.  I have used NERO for a long time on XP for burning but I guess it isn't available on Linux.  Will NERO work with WINe?  Or is there some other app that I should try in Ubuntu?

---

### Post by taurus on 2007-05-19
k3b.

```
sudo aptitude update
sudo aptitude install k3b
```

---

### Post by halitech on 2007-05-19
actually there is a version of Nero for linux ( [http://www.nero.com/eng/NeroLINUX.html](http://www.nero.com/eng/NeroLINUX.html) ) and I have it but I use k3b the most, it does everythign nero does but it's free. don't be worried by it saying it's a KDE app, it will still work in Ubuntu as well.

---

### Post by kc5hwb on 2007-05-19
Thanks, I was wondering if it would work alright in GNOME

---

### Post by Death_Sargent on 2007-05-19
K3B does everything nero does and is free :P

---

### Post by halitech on 2007-05-19
it works great, only reason I got nero is because for some reason when trying to burn dvds, k3b was burning very slow (0.5 to 1.0x) but nero would burn fine. Recently k3b has been working great (5x-6x) when selecting 8x burning so haven't needed to use it (thanks to whoever fixed whatever was broken :) )

---

### Post by burt_57 on 2007-05-19
> **taurus said:**
> k3b.

```
sudo aptitude update
sudo aptitude install k3b
```


Where do you had this code ?

---

### Post by Happy_Man on 2007-05-19
In a terminal: Applications --> Accessories --> Terminal.

---

### Post by halitech on 2007-05-19
open a terminal and put them in there

---

### Post by icechen1 on 2007-05-19
I am afraid of installing k3b because when i go in add/remove program the description of k3b is
>  K3b
A sophisticated KDE CD burning application - Medibuntu package  
K3b is a GUI frontend to the CD recording programs cdrdao and cdrecord. Its aim is to provide a very user friendly interface to all the tasks that come with cd recording.
It can be used to copy CDs and burn:
• audio CDs (from wav, mp3 or ogg vorbis files)
• data CDs and DVDs
• mixed-mode CDs (CD-Extra support)
• VCDs (1.1, 2.0 and SVCD)
• ISO files (Joliet/Rockridge and El Torito support)
• eMovix CDs
For more information, visit the homepage at [http://www.k3b.org](http://www.k3b.org)
This package is built with dvd ripping support. Therefore, it is in Medibuntu as it might violate patents.
[COLOR="Red"]This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU![/COLOR]
Please report any bug to our bug tracker instead: [https://bugs.launchpad.net/medibuntu/+bugs](https://bugs.launchpad.net/medibuntu/+bugs)
Version: 1.0-0ubuntu2+medibuntu1 (k3b)
K3b integrates well into the Kubuntu desktop

---

### Post by OoooMatron on 2007-05-19
k3b works fine. unfortunately, my burner doesn't seem to write at full speed with any native linux burning app so its Nero Linux all the way for me. The new beta 3 is awesome.

---

### Post by Tombo5150 on 2007-05-19
I'd suggest Gnomebaker, click add/remove in the applications menu. Then you'll find it in CD/DVD writer Gnombaker. It works great and is fast. But it can only do data dvds. So you could make a dvd and watch it on your computer but not a dvd player. I usually use dvdshrink for my ripping and burning dvds. However, I am looking for a program which will burn avi files from my harddrive. (and so I can watch them in a dvd player) will this k3b or w/e do that for me?

---

### Post by jimrz on 2007-05-19
> **kc5hwb said:**
> Thanks, I was wondering if it would work alright in GNOME

yes ... or you could try brasero, if you do not want to add all the kde stuff required for k3b

---

### Post by mahiyar on 2007-05-19
I would second Oooomatron Nero beta 3 rocks. No problems at all.

---

### Post by burt_57 on 2007-05-19
Tank it work..........  saw all kind of line in terminal, but now where is the program

---

### Post by burt_57 on 2007-05-21
> **Happy_Man said:**
> In a terminal: Applications --> Accessories --> Terminal.
Tanks now it work and I watch The GodFather  :popcorn:
You all are so helpful
Since I have install Ubuntu amd64 I have not been in Windows since.

---

### Post by kc5hwb on 2007-05-23
I've used K3B a couple of times since I posted this and it seems to work great.

---

### Post by drs305 on 2007-05-23
> **kc5hwb said:**
> I've used K3B a couple of times since I posted this and it seems to work great.

Does the synaptic download version work with Ubuntu Feisty? I can't get my nautilus burner to work and from what I've read there seem to be a lot of issues with cd burning and Feisty... I don't use KDE or Kubuntu if that makes a difference.

---

### Post by Happy_Man on 2007-05-24
It doesn't make a difference, go ahead and install K3B. It will work fine...

---

### Post by stchman on 2007-05-25
> **icechen1 said:**
> I am afraid of installing k3b because when i go in add/remove program the description of k3b is

If it is in the Add/Remove then it will work on Gnome.  Use this line:

sudo apt-get install k3b libk3b2-mp3

This will install the mp3 plugin for K3b and allow it to burn mp3 files and create an audio CD.

---

### Post by ramjet_1953 on 2007-05-25
K3b is definitely the most elegant Linux solution for burning CD's and DVD's

I have found that if you are using it under GNOME, it helps to create the following directories:

/home/<username>/kde/share
/home/<username>/kde/socket-<username>-desktop

K3b seems to want these directories, for some reason and is sometimes very reluctant to start-up without them.

Also, if you want a really great DVD compressor, I would highly recommend k9Copy. It works fine under GNOME and compresses a DVD9 down to DVD5, with no noticeable pixelisation, unlike other compressors that I have tried.

Regards,
Roger :cool:

---

### Post by dpzektor on 2007-05-26
I just purchased Nero Linux myself. I have always been a Nero guy in Windows, and have actually been yearning the app since the switch to ubuntu. K3B seems to be the only free app that can actually burn UDF format discs, which is something that I need. But, K3B is slow and kind of unstable in ubuntu. I am very glad that Nero has been released for Linux. It did kind of stink that I had to fudge my location (said I was in the UK in the payment page) as it seems the purchase is unavailable to us USA people. Yeah, it costs money, but since burning is something that is very important to me, well, it is most certainly worth it. It works just as well (if not better) than the Windows counterpart.

---

### Post by burt_57 on 2007-05-26
> **stchman said:**
> If it is in the Add/Remove then it will work on Gnome.  Use this line:

sudo apt-get install k3b libk3b2-mp3

This will install the mp3 plugin for K3b and allow it to burn mp3 files and create an audio CD.

I get this when usingthis command ,  [FONT="Arial Black"][COLOR="DarkRed"]  sudo apt-get install k3b libk3b2-mp3 [/COLOR][/FONT]
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ron999 on 2007-05-26
> **Tombo5150 said:**
> . However, I am looking for a program which will burn avi files from my harddrive. (and so I can watch them in a dvd player) will this k3b or w/e do that for me?

Nope
If you burn them as AVI files then some DIVX standalone DVD players will play them.
Otherwise you can only view them on your pc.
If you want to make those AVI files into a genuine DVD format disc to play on all players then you need to do some more work on them first.
Try using the program DeVeDe. Then use k3b to do the burn.
:cool:

---

### Post by Icarosaurus on 2007-05-28
> **jimrz said:**
> yes ... or you could try brasero, if you do not want to add all the kde stuff required for k3b

Oh yes..brasero is really interesting and integrates into gnome very well.
Personally I used GnomeBaker but I found it's a little buggy...
Graveman is a good burner too...

---

### Post by mattva01 on 2007-05-28
> **icechen1 said:**
> I am afraid of installing k3b because when i go in add/remove program the description of k3b is
> K3b
A sophisticated KDE CD burning application - Medibuntu package
K3b is a GUI frontend to the CD recording programs cdrdao and cdrecord. Its aim is to provide a very user friendly interface to all the tasks that come with cd recording.
It can be used to copy CDs and burn:
• audio CDs (from wav, mp3 or ogg vorbis files)
• data CDs and DVDs
• mixed-mode CDs (CD-Extra support)
• VCDs (1.1, 2.0 and SVCD)
• ISO files (Joliet/Rockridge and El Torito support)
• eMovix CDs
For more information, visit the homepage at [http://www.k3b.org](http://www.k3b.org)
This package is built with dvd ripping support. Therefore, it is in Medibuntu as it might violate patents.
This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU!
Please report any bug to our bug tracker instead: [https://bugs.launchpad.net/medibuntu/+bugs](https://bugs.launchpad.net/medibuntu/+bugs)
Version: 1.0-0ubuntu2+medibuntu1 (k3b)
K3b integrates well into the Kubuntu desktop

The reason for this is because you have the mediubuntu repository enabled. Bugs should be reported to them and not to canonical.

---

### Post by JUOKAS on 2008-01-28
I have one problem with my k3b, wen i want to burn emovix dvd I had this error:
**Could not find a valid eMovix installation.**

---

