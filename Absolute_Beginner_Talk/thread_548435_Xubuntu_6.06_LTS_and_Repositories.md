---
title: "Xubuntu 6.06 LTS and Repositories"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-11
Hi, I just loaded up Xubuntu 6.06 LTS on an old 400mhz Laptop.
It's a little slow but works great ( Anythings better than 98SE ).

Anyways, I'd like to get this think set up the way I like and I have
noticed that when I go to the repositories and search for stuff
certain things won't come up as they do on my Desktop Ubuntu 7.04
machine. 

I have all only the Binary's checked in Symaptic Packet Manager
with Universe, Mutiverse checked.  I did check (non free) and
(restricted) as well.  Why won't certain things show?

Example.  In the search box, I type in lame
it searches and nothing comes up. I go to my
other pc with Ubuntu 7.04 and ton of stuff
comes up including the codec that I need.

Is it my Xubuntu 6.06 LTS version, I thought it was still supported
and wouldn't a codec work with anything as long as it's linux?

---

### Post by hyper_ch on 2007-09-11
Use this generator to create your sources.list:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by Orbital75 on 2007-09-11
I tryed your suggestion but nothing that I needed came up.
It's strange when I choose my version ( Drapper ) the
Medibuntu multimedia packages doesn't show up as they do
with Feisty.  I'm thinking I can't get this stuff because I have
Drapper.

I just want lame so I can rip a few cd's in mp3 on my laptop.
I also wouldn't mind loading up some other codecs. 
I can't do much with it because it's so slow but I can still
listen to music while I work and surf the net

---

### Post by hyper_ch on 2007-09-11
well, once you have added all the repos you need to update the whole list of applications

```

sudo apt-get update

```

---

### Post by Orbital75 on 2007-09-11
I don't have any more to add than what I already have.
The list maker doesn't list anything new.

Humm.... anything else you can think of.

I'd really just like to add lame so I can rip a few cd's
Here is the error I am getting....

```
myname@orb-1685:~$ sudo apt-get install lame
Reading package lists... Done
Building dependency tree... Done
Package lame is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lame has no installation candidate
myname@orb-1685:~$

```

---

### Post by zach12 on 2007-09-11
i think this would work on xubuntu 
but ther is a xine codec for mp3s in the ubuntu dapper repositories
hope this helps:):lolflag:

---

### Post by Orbital75 on 2007-09-11
Well, I don't have any trouble playing Mp3's 
I'm Using XMMS to play podcast and such

I just need a mp3 encoder for ripperX, Sound Juicer, or Grip.

---

### Post by mikewhatever on 2007-09-11
Lame should be available for Dapper, it is in Multiverse [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=lame&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=lame&searchon=names&subword=1&version=dapper&release=all)
Have you run sudo apt-get update?

---

### Post by ubuntu27 on 2007-09-11
[Note to everyone: This instruction is for (X/U/K)buntu 6.06 LTS, code named Dapper Drake. It should not be followed by the users of other version. [Here is a guide for everyone]("https://help.ubuntu.com/community/RestrictedFormats")

Hello Orbital75. Try this:

```
sudo aptitude install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui 
```


```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo aptitude install libdvdcss2 
```

```
sudo aptitude install w32codecs vorbis-tools libxine-extracodecs
```

If you use K3B to burn CDs, also install this: ```
sudo aptitude install libk3b2-mp3
```

That should take care of codecs problem. [Now let's configure your Sound Juicer so it can rip your CD in MP3:]("https://help.ubuntu.com/community/CDRipping")

1) Open Sound Juicer, click "Preferences" from the "Edit Menu", click "Edit Profiles" and choose "New". Call your new profile "MP3 Encoding", or whatever else you feel like.

2) Edit this profile and set Gstreamerpipeline to audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux (The last number specifies the quality of the file, a larger number means better quality, but larger file size. Optionally, you can change 160 to something else (e.g. 192, 256) if you want a specific (constant) bitrate other than the default of 160).

3) If you are using Ubuntu 6.06 and above, you should use the [WWW] "--preset standard", which will give you very high quality files. The Gstreamer pipline should be set to audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001 ! xingmux ! id3v2mux

4) Finally, set File Extension to mp3, click the Active checkbox and then OK.

5) Restart Sound Juicer for the changes to take effect.

---

### Post by Orbital75 on 2007-09-11
Sorry guys, I over looked that. The apt-get Update worked.
I'm new to linux and didn't understand how important that
was. I was thinking the changes happen immedently. 

Thank you for your help.
Lame is now installed.

By the way, what is the difference between lame and liblame0

---

### Post by hyper_ch on 2007-09-11
> **Orbital75 said:**
> Sorry guys, I over looked that. The apt-get Update worked.
I'm new to linux and didn't understand how important that
was. I was thinking the changes happen immedently. 

Easy... we were all noobs at one stage ;)
I bet you won't forget to "apt-get update" anymore ;)

---

### Post by ubuntu27 on 2007-09-11
> **Orbital75 said:**
> 
By the way, what is the difference between lame and liblame0

This is what is says in Synaptic:

**liblame0**
This package contains the dynamic libraries, which provides the encoding
functionality of lame.

**lame**
This package contains the frontend encoder binary.

---

### Post by Orbital75 on 2007-09-11
That's for sure.... :KS

I love linux, it's just different and takes some getting use to.
There are things that you have to manually do before certain
things work but that just makes you learn your systme better.
:)

---

### Post by ubuntu27 on 2007-09-11
> **Orbital75 said:**
> That's for sure.... :KS

I love linux, it's just different and takes some getting use to.
There are things that you have to manually do before certain
things work but_ that just makes you learn your systme better._
:)

Very true. :)

---

