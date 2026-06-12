---
title: "mp3 support"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by jbutler12 on 2006-12-19
Hi,

Im brand new to linux as of saturday morning.  The last two days ive been pouring over wiki and forum posts and finally got my wireless Belkin USB antena to work using ndiswrapper.  Pretty exciting.  Im loving the way stuff is added, but ive run into a few problems and i dont know how to solve them.  In this post ill try to give some information about my system, the steps ive tried so far from the wiki, and where im stuck.  Im trying to install mp3 support. In doing so, i went through the RestrictedFiles wiki, which recommended a few ways to go about doing it, which i tried.

1. I installed Amarok and tried to play a mp3.  Sure enough i got a prompt that said "MP3 support not enabled, would you like to enable it now?"  I selected OK, and after thinking for a while Amarok told me mp3 support was installed and i needed to restart the program.  I tried restarting both the program and the computer (in that order) and both times i got the same "mp3 support not enabled" message.

2. I tried to find a way to do it on google, and they suggested Automonix (not spelled right).  I tried to install automatix but it came up with 404 file not found errors when trying to install the mp3 codecs.  Installed some cool stuff (like fonts) but no mp3 support.

3. I tried to use EasyUbuntu.  Despite being billed as incredibly easy, it was anything but.  From a pretty much clean install aside from the above two steps and my wireless card configuration, EasyUbuntu gave me like a million incomprehensible errors. 

4.  I tried to enable the Universal and Multiverse repositories via the GUI in System - Select Software, the Synaptic Repository Selections and the apt update at the command line, to install through apt, and got the same error each time:

gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
  Sub-process gzip returned an error code (1)
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [4655kB]
99% [6 Packages gzip 0]            
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
  Sub-process gzip returned an error code (1)

And neither the Universe nor Multiverse of software is availible for me to use.

Anyone have any ideas?  Im liking linux, and it certainly is much more stable and fast (my machine is old and so much faster for what i use it for (email, word processing, running a custom web service) and i like it (espcially since my windows unusable due to spyware), but man, it took me literally 30 hours of pouring over docs just to get my wireless working, and i really hope i dont have to do it again just to get music to play.  Im running Ubuntu 6.1 ("Edgy Eft").

Anyway, any ideas would be great.  Thanks.

-John

---

### Post by xopher on 2006-12-19
For mp3 (and other restricted formats) check out:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And please post your /etc/apt/sources.list here so we can see if that's causing the problems you are having with the repositories.

---

### Post by ziggykg on 2006-12-19
mp3 codecs are not open source and therefore are not part of a standard Ubuntu install.

I suggest installing [Automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation").  It gives you access to the mp3 codecs, among other quite useful apps.

Actually, installing Automatix is among the first things I do after a fresh install of Ubuntu.

---

### Post by jbutler12 on 2006-12-19
Hm.  Well, ziggykg, im not sure i understand... i tried installing automatix, but it wouldnt install the mp3 codecs as i said... is there another automatix you are referring to other than the one i referenced in my original post?

Ive read that wiki many times, and ive taken the steps suggested in that wiki with the exception of compiling from the tarballs of the codecs (which i might try tommorow if i cant get this to work).

Here is my sources.list file:

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by xopher on 2006-12-19
> **ziggykg said:**
> mp3 codecs are not open source and therefore are not part of a standard Ubuntu install.

I suggest installing [Automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation").  It gives you access to the mp3 codecs, among other quite useful apps.

Actually, installing Automatix is among the first things I do after a fresh install of Ubuntu.

Just pointing out what he said in the first post of this thread, he already tried both Automatix and EasyUbuntu, without success..

Edit, and I pointed him to the RestrictedFiles wiki, haha, which he had already read too. SNAP.

---

### Post by xopher on 2006-12-19
Everyting seems to be in order with that too.. So this should work:

```
sudo apt-get update && sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

That would (should in your case :)) install most of the codecs and support for dvd-playing.

---

### Post by jbutler12 on 2006-12-19
I still get the same error when trying that command that i get when i try to install anything from the Universe or Multiverse repositories:

gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 6B in 22s (0B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

And there is no support.

Any idea why this might be happening?  Your help is greatly appreciated!

---

### Post by xopher on 2006-12-19
Hm, you could try using a different repository, replace 'us' with something else, eg. the country code of Canada, if it's not too hard on your ego ;) Maybe it's a mirror related problem.

Edit, my laptop's battery is about to die (in 2mins) so Ill be away until I get it recharged.

---

### Post by TooRight on 2006-12-19
You haven't got those sources enabled.

You see those lines that start with "#deb-http" and "deb src", and end with "multiverse" and "universe"? Uncomment them... that is, remove the "#" that is in front of them. Then install automatix again, and click to install the audio and video codecs that you need.

Honestly, Automatix is awesomeeeeee!! It just hasn't been able to access the files it needs to install what you want. Automatix will automatically change your sources.list and add what repositories it needs for each install. It surrounds those sources in bold comments so that you know it's automatix that put them there.

---

### Post by jbutler12 on 2006-12-19
Thanks for that, ive gotten it down to one error by uncommenting out those lines, but still

```
sudo aptitude update
```

and

```
sudo apt-get update
```

return the same error:

Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [4655kB]
99% [Working]                      
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
  Sub-process gzip returned an error code (1)

I used to get that error for almost every line in the sources.list file, but since changing the addresses to ".ca" instead of ".us" the error went away.  However, i cant find [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages anywhere in my sources.list file to change to ".ca".  Here are the contents of my sources.list file:

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

I feel like im pretty close... .wav now works (i guess it isnt in the Unverse repository, which im failing to download), but mp3 still refused to install b/c of the above error on update.  Any ideas?

I really appreciate all the help.

Take Care,

John

---

### Post by jbutler12 on 2006-12-19
For future reference, i solved this problem by changing all instances of "http://" in the sources.list file to "ftp://" and by changing all instances of "us" to "ca".  Thanks to everyone for their help!

---

