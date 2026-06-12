---
title: "totem-xine in edgy"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Tallman on 2007-02-14
Just upgraded my system from Dapper to Edgy, so now I'm trying to get the packages I was used to.

Since Ubuntu installs the gstreamer version of Totem by default, I now have the following totem packages installed:

libtotem-plparser1
totem
totem-gstreamer
totem-mozilla

When I was on Dapper, I was used to having the xine version. When I did this:

```
sudo aptitude install totem-xine
```

it would remove the gstreamer version automatically.

So I thought to perform this action on Edgy as well. However, trying that, I get the following messages:

```
marpau@marpau-desktop:~$ sudo aptitude install totem-xine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  totem totem-mozilla 
The following packages will be automatically REMOVED:
  totem-gstreamer 
The following NEW packages will be installed:
  totem-xine 
The following packages will be REMOVED:
  totem-gstreamer 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/1102kB of archives. After unpacking 106kB will be freed.
The following packages have unmet dependencies:
  totem: Depends: totem-gstreamer (>= 2.16.2-0ubuntu3) but it is not installable or
                  totem-xine (>= 2.16.2-0ubuntu3) but 2.16.2-0ubuntu1 is to be installed.
  totem-mozilla: Depends: totem-xine (>= 2.16.2-0ubuntu3) but 2.16.2-0ubuntu1 is to be installed. or
                          totem-gstreamer (>= 2.16.2-0ubuntu3) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
totem [2.16.2-0ubuntu3 (edgy-updates, now) -> 2.16.2-0ubuntu1 (edgy)]
totem-mozilla [2.16.2-0ubuntu3 (edgy-updates, now) -> 2.16.2-0ubuntu1 (edgy)]

Score is -130

Accept this solution? [Y/n/q/?]
```

Answering "n" to this question, it gives me this:

```
Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
totem
ubuntu-desktop

Downgrade the following packages:
totem-mozilla [2.16.2-0ubuntu3 (edgy-updates, now) -> 2.16.2-0ubuntu1 (edgy)]

Leave the following dependencies unresolved:
gnome-volume-manager recommends totem
Score is -942

Accept this solution? [Y/n/q/?]
```

Then I quit...

Can anybody tell me what I'm doing wrong here?

---

### Post by Tallman on 2007-02-15
Shamless bump...

It's really bothering me.
Anybody?

---

### Post by zvacet on 2007-02-15
Why don´t you try with synaptic?Remove what you don´t need,and install what you want.Another way is to install totem-xine with Automatix.

---

### Post by frodon on 2007-02-15
Don't use automatix it just makes harder to upgrade to another release once you used it because it use unofficial repositories, so it's a bad idea to use it.

Use synaptic you would avoid many problems if you are not an expert, then about the codecs and libraries needed you will find all you need for ubuntu there :
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Tallman on 2007-02-15
> **frodon said:**
> Don't use automatix it just makes harder to upgrade to another release once you used it because it use unofficial repositories, so it's a bad idea to use it.

Most important reason I don't use automatix is that I see problems like mine as a learning experience. What I've learnt about automatix is that it installs and configures a lot of stuff 'behind the scenes'; I want to see, learn and (eventually) control what's happening on my system

> **frodon said:**
> Use synaptic you would avoid many problems if you are not an expert, then about the codecs and libraries needed you will find all you need for ubuntu there :
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I use aptitude instead of synaptic and apt-get because of this: [http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude"). I could try using synaptic when I'm back at home, but wouldn't it give me the same error message?

I'll definitely double-check that document about the restricted formats. In this thread [http://www.ubuntuforums.org/showthread.php?t=268918]("http://www.ubuntuforums.org/showthread.php?t=268918") I just read something about the dapper-updates repository; in my case that would obviously be the edgy-update repository. I'll check that one as well.

For now, thanks for your reply!

---

### Post by frodon on 2007-02-15
Yep aptidute and apt-get have both advantages and disadvantages and IMO none is better than the other. However i strongly advice you to try as much as possible to not mix the 2, i mean try to use always aptitude or always apt-get and yes i think you will get the same answer.

On the other don't remove totem it's a gnome apps and as a lot of inescapable dependencies so you will just have problems if you remove it, so i would accept the downgrade in this case, i will check the version number i have if you wish once at home because i use totem-xine as well.

---

### Post by louis_nichols on 2007-02-15
The problem is that, for some reason, the package totem-mozilla under edgy depends on totem-gstreamer and does not appear to accept totem-xine.

I noticed this when, having totem-xine installed, I tried to install totem-mozilla and it wanted to replace totem-xine with totem-gstreamer.

I don't know if this has a real technical reason or it's just a bug in enumerating dependencies. It's worth filing a bug in Launchpad, I think, but be sure to check that it hasn't been reported before.

---

### Post by frodon on 2007-02-15
I think it's just dependencies because the totem plugin for mozilla may not support xine backend and i think it should be the reason why it require totem with gstreamer backend installed to get the plugin working.
Anyway you are not obligated to use the totem plugin for embedded streams you can use the mplayer mozilla plugin or the excelent "media player connectivity" extention of firefox which just open the stream with the player of your choice.

In my case i use totem-xine and the media player connectivity extension of firefox.

---

### Post by Tallman on 2007-02-15
> **frodon said:**
> I think it's just dependencies because the totem plugin for mozilla may not support xine backend and i think it should be the reason why it require totem with gstreamer backend installed to get the plugin working.

If that is true, I don't understand why I never had that problem in Dapper. Can a new version of Ubuntu contain depencies that a previous version didn't have?

> **frodon said:**
> Anyway you are not obligated to use the totem plugin for embedded streams you can use the mplayer mozilla plugin or the excelent "media player connectivity" extention of firefox which just open the stream with the player of your choice.

In my case i use totem-xine and the media player connectivity extension of firefox.

I've read good stuff about that extension too. Could give that one a try as well.

---

### Post by Tallman on 2007-02-15
The problem was indeed the edgy-updates repository. I had only the main and restricted repository enabled. After adding the multiverse and universe as well, I can now install totem-xine flawlessly.

One other thing: when I try to remove the totem-mozilla package (since I plan to install the media player connectivity extension of firefox I don't need that one anymore), I get the following:

```
marpau@marpau-desktop:~$ sudo aptitude remove totem-mozilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  ubuntu-desktop 
The following packages will be REMOVED:
  totem-mozilla 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 61.4kB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: totem-mozilla but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
totem-mozilla [2.16.2-0ubuntu3 (edgy-updates, now) -> 2.16.2-0ubuntu2 (edgy-proposed)]

Leave the following dependencies unresolved:
totem-xine recommends totem-mozilla (= 2.16.2-0ubuntu3)
Score is -239

Accept this solution? [Y/n/q/?]
```

```
marpau@marpau-desktop:~$ sudo cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security restricted main universe #Added by software-properties

deb http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu edgy multiverse

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse #Added by software-properties

deb http://security.ubuntu.com/ubuntu/ edgy-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu/ edgy-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb http://archive.canonical.com/ubuntu edgy-commercial main
```

Is there still something wrong with my sources.list?
Can I safely leave the totem-mozilla package installed and get that firefox extension anyway?

---

### Post by AndyCooll on 2007-02-15
It might be because an updated version of Totem came out last week and totem-xine currently doesn't seem to work with it.

I say this because I too prefer totem-xine and the update uninstalled it. When I tried to reinstall it, Synaptic was going to uninstall the Ubuntu-desktop! I'm sure I'll be able to re-install it without such drastic steps but for now I couldn't be bothered to work out how.

:cool:

---

### Post by Gillen on 2007-02-15
I have just got Edgy sorted for all my requirements the last was the poor sound quality in Neverwinter Nights. Anyway here is my source list and the additional steps I took to get things working which includes DVD playback.

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


To install ATI Radeon Drivers

sudo gedit /etc/X11/xorg.conf

Copy the following to the xorg.conf and save

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

then the following

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

to configure

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

then REBOOT

DVD Playback

Install the libdvdread3 package.

sudo  /usr/share/doc/libdvdread3/install-css.sh

sudo apt-get install totem-xine

For AVI (Xvid) and correct Mpeg playback

Install the libxine-extracodecs package

To make thunbnails work in Nautilus for AVI files clear out everything in /home/[username]/.thumbnails/fail/gnome-thumbnail-factory/

Installing RealPlayer 10 for use on BBC site

Download the installer from the Real web site

Verify that the file is executable then

sudo ./RealPlayer10GOLD.bin

Then remove

libtotem-complex-plugin.so

libtotem-complex-plugin.xpt

From

/usr/lib/mozilla-firefox/plugins

then REBOOT

To Rip CDs to MP3 format

install the gstreamer0.10-plugins-ugly-multiverse


Open Sound Juicer, click "Preferences" from the "Edit Menu", click "Edit Profiles" and choose "New". Call your new profile "MP3 Encoding", or whatever else you feel like.
Edit this profile and set Gstreamerpipeline to
 
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux

Then set the profile as active.

To rip DVDs

Install the Thoggen package

To enable Java

sudo apt-get install sun-java5-jre sun-java5-plugin

To fix poor sound in games that use SDL (Neverwinter Nights) create a file .asoundrc in your home directory and copy these lines into it then save.

pcm.!default {
     type hw
     card 0
}

ctl.!default {
     type hw
     card 0
}



Note where I have put install it means install via Synaptic.

Hope this helps. Regards.

---

### Post by Tallman on 2007-02-15
> **AndyCooll said:**
> It might be because an updated version of Totem came out last week and totem-xine currently doesn't seem to work with it.

I say this because I too prefer totem-xine and the update uninstalled it. When I tried to reinstall it, Synaptic was going to uninstall the Ubuntu-desktop! I'm sure I'll be able to re-install it without such drastic steps but for now I couldn't be bothered to work out how.

:cool:

Okay, let me leave it for now. I'll try again in a few days.

Thanks y'all for your replies. For me, this forum is what Ubuntu is all about!

---

