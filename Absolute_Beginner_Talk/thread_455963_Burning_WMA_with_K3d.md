---
title: "Burning WMA with K3d ?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by stooker on 2007-05-27
Hey there,

I searched the forum and web with this question and installed the following plugins:

Musepack
FLAC
FFmpeg
Libsndfile

But still my k3d doesn't support WMA files? 

Anybody? Or does anybody know a burning programm who does?

---

### Post by stooker on 2007-05-27
Or if there is no solution does anybody know a converting programme from WMA to MP3 ?

---

### Post by Kobalt on 2007-05-27
There's a little french program that does it all (converting audio files into many formats), but I don't know if it has been translated though... It's called [XFCA]("http://bulin.claude.neuf.fr/xcfa-download.html").

---

### Post by stooker on 2007-05-27
Hmmm...thanks for the reply, but my french is awfull. 

There must be somebody that can help me to get K3b burning WMA files. I read on the internet that it is possible. Normally installing FFmpeg should do the job.

---

### Post by Kobalt on 2007-05-27
In this case this would suffice : ```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by stooker on 2007-05-27
I tied it, but get the following error:

stooker@stooker-desktop:~$ sudo apt-get install libxine1-ffmpeg
Password:
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
E: Kon pakket libxine1-ffmpeg niet vinden
stooker@stooker-desktop:~$

---

### Post by Kobalt on 2007-05-27
Which version of Ubuntu do you have ?

---

### Post by stooker on 2007-05-27
Kubuntu drapers 6.06

* edit * Oh sorry the error message is in dutch. It says: Couldn't vind the package libxine1-ffmpeg

---

### Post by Kobalt on 2007-05-27
Ok then, you need to [enable the Universe and Multiverse repos]("https://help.ubuntu.com/6.06/kubuntu/desktopguide/C/extra-repositories.html") in order to install libxine1-ffmpeg.

---

### Post by stooker on 2007-05-27
I enabled all repository line and even added some already.

---

### Post by Kobalt on 2007-05-27
What does this exactly mean : "E: Kon pakket libxine1-ffmpeg niet vinden" ?

---

### Post by stooker on 2007-05-27
"E: Kon pakket libxine1-ffmpeg niet vinden" ? means:

"E: Couldn't find package  libxine1-ffmpeg"

---

### Post by Kobalt on 2007-05-27
Then I'm affraid you don't have te apropriate repos enabled... Can you please post your sources.list file.

---

### Post by stooker on 2007-05-27
deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib 
deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib 

# Line commented out by installer because it failed to verify:
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper main restricted 
# Line commented out by installer because it failed to verify:
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
# Line commented out by installer because it failed to verify:
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper universe 
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main 
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

---

### Post by Kobalt on 2007-05-27
You do miss the multiverse repos. Check this site out to have the apropriate sources.list : [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by stooker on 2007-05-27
Done, I checked every box to be sure :P

And now install that ffmpeg again? Or a reboot, cause I tried installing it again but he still can't find the package.

---

### Post by Kobalt on 2007-05-27
Yes

---

### Post by stooker on 2007-05-27
hmmmpzzzzzzz......I so close with buying software for the first time in my life, windows is oooow sooo easy.

It still can't find the package. :(

I'm trying to get K3b and Apollon at work for 2 weeks now :(

---

### Post by Kobalt on 2007-05-27
Then simply try to install the *ffmpeg* package (at least we're sure it's here).

---

### Post by forestpixie on 2007-05-27
I haver had similar problems with the odd audio file - you could try this

[http://linux.softpedia.com/get/Multimedia/Audio/Audio-Convert-3104.shtml](http://linux.softpedia.com/get/Multimedia/Audio/Audio-Convert-3104.shtml)

you might have better luck getting it to work than I did. Someone with more experience might be able to help with getiign it going.

I - unfortunately - still do odd things in win if I have to and I found it easier to convert some files there

good luck - :)

Someone with more experience might be abl;e to help with getiign it going.

---

### Post by stooker on 2007-05-27
that one I already installed from the adept programm or synaptic dunno anymore.

I'm done for today, spend the last 3 hours trying to fix those two problems with no result.

Thanks for al the help anyway, maybe next week I get some new energie to try and fix this.

---

