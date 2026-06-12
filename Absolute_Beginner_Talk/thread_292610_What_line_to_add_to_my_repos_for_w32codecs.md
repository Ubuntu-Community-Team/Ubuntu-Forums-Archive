---
title: "What line to add to my repos for w32codecs?"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-11-04
Hello all!

I just installed ubuntu v6.10 Edgy Eft.

I would like to install the "w32codecs".

However, I can not find it with the Synaptic.

My "sources.list" file looks like this:

> 
# For Ubuntu v6.10 - Edgy Eft:
# ---------------------------

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) edgy-updates main restricted


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) edgy universe


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


## This was added (as asked)
## Multiverse

deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse


## The following 2 lines are required for the "w32codecs" package:

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free


## This is required if you would like to install a Webcam.
## The Repo below, helps you locate & install the required package 
## named "easycam2".

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

## Backports:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

Are the above lines correct?

And what line is missing to be able to locate the "w32codecs" package?

Thanks.

---

### Post by jordanmthomas on 2006-11-04
I searched Ubuntu's repositories and it isn't in there.
So, you could just do this:
```
wget http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
sudo dpkg -i w32*.deb

```

---

### Post by hyper_ch on 2006-11-04
You could use Automatix2 to get the W32 codecs :) I guess that's probably the easiest way...

---

### Post by jordanmthomas on 2006-11-04
my way would get it in two commands, so there!  ;)

---

### Post by hyper_ch on 2006-11-04
But with automatix you can install also a few more things easily :)

---

### Post by dvarsam on 2006-11-04
But when I click on the "Reload" button on Synaptic Package Manager, why do I get these messages?

> [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/source/Sources.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/source/Sources.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/source/Sources.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/source/Sources.gz:) 404 Not Found

What line is wrong on my "sources.list" file?

Thanks.

---

### Post by jordanmthomas on 2006-11-04
Just visited the freecontrib.org, and I believe the name of the repository is edgy-plf, not edgy as you have listed...so, change those two lines to
```
## The following 2 lines are required for the "w32codecs" package:

deb http://packages.freecontrib.org/ubuntu/plf/ edgy[COLOR="Red"]-plf[/COLOR] free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy[COLOR="Red"]-plf[/COLOR] free non-free
```

---

### Post by boban on 2006-11-04
As sjau said - try automatix2... And check [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by jordanmthomas on 2006-11-04
People don't always want to use Automatix, and I think it's important to answer the questions that are being asked instead of just pointing them to (an easier) solution.

---

### Post by hyper_ch on 2006-11-04
Isn't linux about choices?
You offered him one way to do it...
I offered him another...
For sure there are a couple more ways...

Which one he picks is then up to him (or her)...

---

### Post by jordanmthomas on 2006-11-04
touche

---

### Post by hyper_ch on 2006-11-04
;)
Thx for your solution also :) Didn't know how to do that without automatix :)

---

### Post by dvarsam on 2006-11-04
> **jordanmthomas said:**
> Just visited the freecontrib.org, and I believe the name of the repository is edgy-plf, not edgy as you have listed...so, change those two lines to
```
## The following 2 lines are required for the "w32codecs" package:

deb http://packages.freecontrib.org/ubuntu/plf/ edgy[COLOR="Red"]-plf[/COLOR] free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy[COLOR="Red"]-plf[/COLOR] free non-free
```

Dear "jordanmthomas",

Thanks!

This was what I was looking for!

I went & replaced those 2 lines with what you suggested & it worked!!!

However, when I click on the "Reload" button on Synaptic Package Manager, I get a different error:

> W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy-plf Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

Any ideas how to correct this?

Thanks.

---

### Post by jordanmthomas on 2006-11-05
[http://ubuntuforums.org/showthread.php?t=274699](http://ubuntuforums.org/showthread.php?t=274699)
See if that helps.

---

### Post by dvarsam on 2006-11-05
> **jordanmthomas said:**
> [http://ubuntuforums.org/showthread.php?t=274699](http://ubuntuforums.org/showthread.php?t=274699)
See if that helps.

Dear "Jordanmthomas",

I tried importing the key, as suggested in the above post & this is what I got:

> 
root@dimitris-desktop:/# [color="Red"]gpg --keyserver subkeys.pgp.net -recv F120156012B83718[/color]

gpg: conflicting commands

root@dimitris-desktop:/# [color="Red"]gpg -export -armor F120156012B83718 | sudo apt-key add -[/color]

gpg: Invalid option "-export"
gpg: no valid OpenPGP data found.



What is wrong and I can not import the key manually?

Thanks.

---

### Post by jordanmthomas on 2006-11-05
On the recv and export switches, you have only used one -
You need two.

Try copying and pasting the commands into your terminal and see if they work any better.

And, this is importing the key manually...I'm not sure what else you could be looking for (unless you mean actually finding the proper gpg key and importing rather than getting it from subkeys.pgp.net)

---

### Post by autocrosser on 2006-11-05
Just a FYI in reguards to Automatix:

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-November/022185.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-November/022185.html)

---

### Post by jordanmthomas on 2006-11-05
If the other method *still* doesn't work, try this (straight from plf)
```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
```

Maybe this is the 'manual' way you were mentioning?

---

### Post by crimesaucer on 2006-11-07
I think you did everything correctly (if you followed the wiki page instructions), I read in some forum posts that the "plf" repository isn't being maintained right now and needs more volunteers working on it, so it still won't work even if you install it correctly. 

I could be wrong, but it was working up until the time edgy was released (using the wiki page instructions during the edgy betas), and since final release, I've had use the link that jordanmthomas gave you.

wget [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)
sudo dpkg -i w32*.deb

it works, and I can't tell the difference between the plf w32codecs, and the debian-multimedia w32codecs.

---

### Post by dvarsam on 2006-11-07
> **jordanmthomas said:**
> If the other method *still* doesn't work, try this (straight from plf)
```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
```

Maybe this is the 'manual' way you were mentioning?


Dear "jordanmthomas",

Thanks for your reply!

The above command you provided, solved this Error from flashing, whenever I hit the "Reload" button on Synaptic.

It hasn't shown up since...

Thanks again!

---

