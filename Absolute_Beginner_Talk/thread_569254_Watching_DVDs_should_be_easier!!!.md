---
title: "Watching DVDs should be easier!!!"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by harbdog on 2007-10-06
as messed up as the DMCA laws are for not allowing the distribution of deCSS in the US, Ubuntu will NEVER get the #1 bug (Windows) fixed if people cannot watch their DVD movies without having to resort to a command line and trying often in vain to get it to work.
 
I used to use Automatix and all was good.  Though now it seems their site is always down so I can't download it.  I even went looking around for a couple hours trying to figure out another way, such as [http://ubuntu1501.blogspot.com/2007/06/medibuntu-how-to-install-dvd-codecs.html](http://ubuntu1501.blogspot.com/2007/06/medibuntu-how-to-install-dvd-codecs.html).  However this didn't really seem to work for me.

I thought it was gonna be as easy as popping in the DVD and then movie player should automatically load, fail to load drivers, then ask the user if they wanna install the stuff automatically... pretty much how about everything else does in ubuntu except this.

i'd say this is a #2 bug, because its gotta be fixed before anything can be done about #1


PS keep up the good work, Gutsy rules!

---

### Post by taurus on 2007-10-06
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---

### Post by n3tfury on 2007-10-06
or just install vlc?  am i missing something?

---

### Post by mramsey on 2007-10-06
> **n3tfury said:**
> or just install vlc?  am i missing something?

funny thing about VLC...I installed it in windows and it wouldn't play half of my dvds...but in Ubuntu it plays all. go figure.:lolflag:

---

### Post by harbdog on 2007-10-06
after installing and trying a few more video players I can now watch DVDs... still too much of a hassle for most users to handle


Movie Player (Totem) - FAILED
MPlayer - FAILED
gXine - works, but the color and brightness is off
VLC - works GREAT... but their UI is crap compared to Totem.

---

### Post by Lord Illidan on 2007-10-06
If only the whole issue of css was solved once and for all, then it would be as easy as ...abc.

---

### Post by Billy_McBong on 2007-10-06
[COLOR="Blue"]if you have universe enabled ```
sudo apt-get install ibdvdcss2
```
should let you play DVDs
i have never had any problems playing them[/COLOR]

---

### Post by MrKlean on 2007-10-06
How about the STICKY...enablng multimedia in feisty ??  That's easy  and werks !!

---

### Post by Pumalite on 2007-10-06
Have you tried:

sudo apt-get ubuntu-restricted-extras

---

### Post by brucewagner on 2008-01-09
Why can't these "restricted extras", or whatever they are, to play commercial DVDs... be installed automatically as needed... after prompting the user...    just like the Firefox plugins are...?

---

### Post by hyper_ch on 2008-01-09
What's not easy about watching DVDs?

---

### Post by Paqman on 2008-01-09
> **brucewagner said:**
> Why can't these "restricted extras", or whatever they are, to play commercial DVDs... be installed automatically as needed... after prompting the user...    just like the Firefox plugins are...?

Some of it is. It's a meta-package containing several subordinate packages including Flash and multimedia codecs (which do get prompted for installation, like you say)

Installing ubuntu-restricted-extras is one of the first things I do on a fresh install, since it's such a useful package. Trouble is, how would a newbie know to do this?

---

### Post by hyper_ch on 2008-01-09
ubuntu-restricted-extras and libdvdcss2 (I'm not sure if that's included in the restrictd-extras)

---

### Post by Paqman on 2008-01-09
Nope, it doesn't, but it contains packages that work with it if it's installed.

[List of packages in ubuntu-restricted-extras](http://packages.ubuntu.com/gutsy/metapackages/ubuntu-restricted-extras)

---

### Post by hyper_ch on 2008-01-09
And for libdvdcss2 add the [medibuntu]("http://www.medibuntu.org") repos

---

### Post by brucewagner on 2008-01-09
> **hyper_ch said:**
> ubuntu-restricted-extras and libdvdcss2 (I'm not sure if that's included in the restrictd-extras)

This page ( [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) ) says that I need libdvdcss2 and w32codecs ...

But you guys said I need, ubuntu-restricted-extras and libdvdcss2 ...

Do I need all three packages?

---

### Post by hyper_ch on 2008-01-09
well, if you still don't see an image or hear sound you can also install w32codecs (I do that)

---

### Post by brucewagner on 2008-01-09
So, just to clarify....

I go to “Applications–>Accessories–>Terminal” and then Paste in each of the following lines — one at a time:

    * sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
    * wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
    * sudo apt-get install libdvdcss2
    * sudo apt-get install w32codecs
    * sudo apt-get install ubuntu-restricted-extras

Yes?

---

### Post by hyper_ch on 2008-01-09
> **brucewagner said:**
> So, just to clarify....

I go to &#8220;Applications&#8211;>Accessories&#8211;>Terminal&#8221; and then Paste in each of the following lines &#8212; one at a time:

    * sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
    * wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
    * sudo apt-get install libdvdcss2
    * sudo apt-get install w32codecs
    * sudo apt-get install ubuntu-restricted-extras

Yes?

That would work but I'd make it different:

```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && libdvdcss2 w32codecs ubuntu-restricted-extras

```

---

### Post by brucewagner on 2008-01-09
Why the change?

What's different about your method?

---

### Post by rkd on 2008-01-09
I see that the difference is that after downloading the file that says where to get the list of packages, he adds a command to remove the non-free ones. (Non-free means the software developer does not release the source code for the programs; it has nothing to do with cost.)

I don't know why he is telling you to do that. Perhaps he thinks you don't want to use non-free software. Perhaps he doesn't want anyone to use non-free software and is trying to trick you into not finding it.  Perhaps he has another reason that I'm not thinking of. (Since my understanding of those software repositories is still quite weak, the third is a distinct possibility.)

It certainly would have been more neighborly of him to tell you why he suggested that change, wouldn't it?

---

### Post by mdpalow on 2008-01-09
I've tried to make watching DVD's easier for people with my script. You're welcome to download it and use it the next time you make a clean install and have to start over.

See my links below in Signature

---

### Post by ubuntu-freak on 2008-01-15
Second post in my how-to focuses on DVD playback 

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

It's easy too.

Nathan

---

### Post by stchman on 2008-01-15
> **harbdog said:**
> as messed up as the DMCA laws are for not allowing the distribution of deCSS in the US, Ubuntu will NEVER get the #1 bug (Windows) fixed if people cannot watch their DVD movies without having to resort to a command line and trying often in vain to get it to work.
 
I used to use Automatix and all was good.  Though now it seems their site is always down so I can't download it.  I even went looking around for a couple hours trying to figure out another way, such as [http://ubuntu1501.blogspot.com/2007/06/medibuntu-how-to-install-dvd-codecs.html](http://ubuntu1501.blogspot.com/2007/06/medibuntu-how-to-install-dvd-codecs.html).  However this didn't really seem to work for me.

I thought it was gonna be as easy as popping in the DVD and then movie player should automatically load, fail to load drivers, then ask the user if they wanna install the stuff automatically... pretty much how about everything else does in ubuntu except this.

i'd say this is a #2 bug, because its gotta be fixed before anything can be done about #1


PS keep up the good work, Gutsy rules!

Here is a tutorial on watching encrypted DVDs.  First install your codecs.

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Then follow this tutorial.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

I can watch all of my Hollywood DVDs on my PC if I wish.

---

