---
title: "Playing dvds"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-06-10
HI

Well, I've got 6.06 installed - the manual partition option is easy if you know what you're doing, but potentially tricky otherwise. Ideally, I'd like to be able to play dvds - I've paid for  them so why not. I managed this with Suse 9.1, but it was a real struggle. Easyubuntu, promised to solve all such problems at a stroke, but it doesn't seem to have worked, so I'm trying to follow the advice in the Ubuntu Wiki 'Playing no-free media'.

I gather the first step is to 'Enable the multiverse and universe repositorties'. Being very new to Ubuntu I'm a bit hazy as to what these are, but I've been giving it a go.

I fire-up the Synaptic Package Manager, as instructed; under 'Settings' click on 'Repositires', but then what I get on my screen does not match the Wiki explanation. In particular,  there's no 

'Settings button at the bottom' so I can't

'tick Show disabled software sources.'

Is this because th Wiki refers to 5.10, in which case maybe I've could to wait for the documentation to catch-up, or am I doing something wrong.

All help much appreciated. 

This is a lovely distribution, the interface is clean and elegant, and all the basic stuff is wonderfully easy and intuiative.

Roger D

---

### Post by x64Jimbo on 2006-06-10
The method of playing DVDs in Linux is technically illegal in the US due to the Digital Millennium Copyright Act (DMCA).
Because of this, it's probably a bad idea to be talking about this kind of thing in too much detail here. However, the wiki has a good bit of info on how to get the DVD decoding library installed properly. 
[https://wiki.kubuntu.org/RestrictedFormats](https://wiki.kubuntu.org/RestrictedFormats)
Hope that helps somewhat. I also hope your DVD player doesn't get skippy like mine does :(

---

### Post by ubuntu27 on 2006-06-10
Follow this guide: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)


ABout adding or anebling other repos:

It seems the guide has not been update to refrect the changes in Dapper. In dapper you do not need to "Click the Settings button at the bottom and tick Show disabled software sources. Then click the Close button." [
[https://wiki.ubuntu.com/AddingRepositoriesHowto]](https://wiki.ubuntu.com/AddingRepositoriesHowto])


Just open the Synaptic P. Manger, click on Settings, Repositories.

And then check (enable) all the white boxes on the left side, then click Close.  

:)  Now that you enabled the Universe/Multiverse Repo, you can install Restricted Codecs or Formats :)

---

### Post by grsing on 2006-06-10
You could also try automatix, it's always worked for me (similar concept to EasyUbuntu).

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by nalmeth on 2006-06-10
yeah you need the libdvdcss package

as for skippy playback, [enabling DMA]("https://wiki.ubuntu.com/DMA") should fix that

---

### Post by RogerD on 2006-06-11
Many thanks. I'll give this a go

---

### Post by RogerD on 2006-06-11
This is going to sound a bit dumb. I've clicked on all the white boxes and followed the on-screen prompts, so I reckon I must have enabled the Universe/Multiverse Repo. The Wiki now tells me I have to install Totem-Xine by installing the package:
totem-xine gxine libxine-extracodecs mplayer.

I've looked for this package in Synaptics, but I can't find it.

What next please?

---

### Post by Angellis_ater on 2006-06-11
I believe Totem is already installed in Dapper.

---

### Post by Perfect Storm on 2006-06-11
Can you post your source list?

```
nano /etc/apt/sources.list
```

It seems there's something that isn't enable.

---

### Post by RogerD on 2006-06-11
You mean this?

nano /etc/apt/sources.list
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiv$
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted

---

### Post by RogerD on 2006-06-11
Hi 
I've gone down the automatix route. Not for the total newbi, and it took me a little while to realise I needed super user status to amend souces.list, but it all worked bueatifully in the end.

All those great people who have worked on 6.06 and automatix have done a brilliant job.

Roger D

---

### Post by ubuntu27 on 2006-06-11
```
sudo apt-get update
```

EDIT: never mind**  You already used automatix :D


Welcome to the community Roger, you and I have more learning to do. ;)  But in the end it all pays.

---

