---
title: "Ok I have followed the wiki"
date: 2007-08-16
forum: Apple PPC Users
---

### Post by Ripfox on 2007-08-16
I followed the ppc Ubuntu community doc, and I STILL can't get .flv videos which I have downloaded to play. Can someone PLEASE walk me through this problem, I would appreciate it greatly. Also, the mplayer Firefox plugin just buffers it to like 35% then stalls out. 400mgz imac, blue/white, 755 mb ram.

Thnx!

BTW, I tried VLC and it crashes when I try to play them...

---

### Post by Ripfox on 2007-08-16
bump

---

### Post by stmiller on 2007-08-17
Start vlc from a terminal, play a downloaded video from your hard disk, and give us the terminal output here when it can't play the content. And are you running Feisty?

---

### Post by Ripfox on 2007-08-18
desktop:~$ vlc
VLC media player 0.8.6 Janus
Illegal instruction (core dumped)

---

### Post by johng4 on 2007-08-18
Did you add the medibuntu codecs?

I use Democracy from the repos, plus the medibuntu repos, to play flv.  Works most of the time.

---

### Post by Ripfox on 2007-08-18
Well I THINK I added the medibuntu codecs, but just for kicks how did you do it?

---

### Post by Ripfox on 2007-08-18
VLC media player 0.8.6 Janus
Illegal instruction (core dumped)

Yes, I have them installed

---

### Post by Auria on 2007-08-18
Then try Democracy as he suggested

---

### Post by Ripfox on 2007-08-19
I tried Democracy, and it seems obvious to me that flash just isn't working at all. I read that you can achieve a certain level of success with gnash 8 but no go on anything except some banner ads here. I tried the video downloader and vlc and democracy suggestions but it won't work here.

---

### Post by stmiller on 2007-08-20
Do you have any other third party (unsupported) repos installed, or did you try to use Automatix? Those things could have possibly created these problems.

---

### Post by Ripfox on 2007-08-20
Here is my sources.list (I know Automatix is not for ppc :))

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) feisty/

:confused:

---

### Post by makinasvp on 2007-08-22
Ok this is how I did it... I hope it works for you ok?

Open up terminal and then type:

```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
```
It will probably ask you to type in your password so go ahead and do that.

Then type:

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Once that is done, type:

```
sudo apt-get update
```

Then simply type:

```
sudo su -c 'echo deb http://packages.medibuntu.org/ feisty free non-free > /etc/apt/sources.list.d/medibuntu.list'
```

Then once again:

```
sudo apt-get update
```

and finally...

```
sudo apt-get install ibm-j2re1.5 ppc-codecs libdvdcss2
```

Once you have done that give it a good update and upgrade by doing this:

```
sudo apt-get update && sudo apt-get upgrade
```

And you are good to go.
Works perfect for me. Hopefully this has helped. :)

---

