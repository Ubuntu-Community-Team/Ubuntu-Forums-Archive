---
title: "Can't Play .mp3, .wav, .mpeg or any video or audio files!!!"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by minhaz4u on 2006-04-23
Im a newbie to Linux..Im using UBUNTU Ver 5.10
My prob is that I can't Play files like .mp3, .wav, .mpeg or any video or audio files!!

When ever I try to play an audio or video file in TOTEM MOVIE PLAYER..I get this error message : " **Totem could not play 'file:///home/scorpio/Desktop/Eurotrip Soundtrack - Scotty Doesn't Know.mp3**'.There were no decoders found to handle the stream, you might need to install the corresponding plugins "

And in RHYTHMBOX MUSIC PLAYER...I get this : " The file is not an audio stream " 

Several times I tried Synaptic Package Manager to get the needed packages,but It fails or downloads broken packages everytime..I guess my source.list is corrupted.

Here is my source.list content : 
--------------------------------------------------------------------------------------------------------

# Specialized Basic Ubuntu Multimedia Preparation Script sources.

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ dapper main restricted

## Uncomment the following two lines to fetch updated software from the network

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

## PLF repo's.
deb [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_...lf/ubuntu/plf/) breezy free non-free


-------------------------------------------------------------------------------------------------------


Could some one please help me out by providing a fruitful solution ;)  ??? 
Also I can't update or upgrade anything using Terminal because it shows "Connection timed out" and wouldn't download anything 8) 

Minhas,
Russia

---

### Post by Jason_25 on 2006-04-23
Looks like you have a few separate problems.  I suggest starting a new thread if your having networking issues.  As for your media playback, check [this]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29") out.

Also, I noticed your sources.list references dapper.  The list should say breezy if your still using it.

---

### Post by Qrk on 2006-04-23
You sources.list is all Dapper, have you installed these updates yet? Dapper is still beta, so you are better off sticking to breezy. If you haven't upgraded to Dapper and want to stay with Breezy, please replace your sources.list 

```
gksudo gedit /etc/apt/sources.list
```

Delete the contents and replace with this:

```
# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
```

---

### Post by nalmeth on 2006-04-23
The install CD says you installed breezy, but you've upgraded the rest of your sources to dapper?
If you are running dapper, and it is running fine (including internet), then try the bumps multimedia script created by iandefor in the Dapper Forum, to install all the necessary codecs.
If you're having problems, you may just want to reinstall breezy and just use automatix. That is the most stable secure answer

---

