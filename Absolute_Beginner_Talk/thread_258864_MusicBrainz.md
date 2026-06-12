---
title: "MusicBrainz"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by candlepin on 2006-09-16
please forgive the noob that I am. 

I'm trying to install MusicBrainz. I've tried installing it 2 different ways.

First, with Synaptic.  I get the error message:
picard:
 Depends: python-tunepimp but it is not going to be installed

When I try to install python2.4-tunepimp I get the error:
python2.4-tunepimp:
 Depends: libtunepimp4 but it is not going to be installed

When I try to install libtunepimp4 I get the error:
libtunepimp4:
 Depends: libmp4v2.0 (>=2.0.0+cvs20040908+mp4v2+bmp) but it is not available

Frustrating!!


Secondly, I tried using a scripted approach:

sudo echo "deb [http://users.musicbrainz.org/~luks/ubuntu](http://users.musicbrainz.org/~luks/ubuntu) dapper main" >>/etc/apt/sources.list
sudo apt-get update
sudo apt-get install picard

I get up to the command:
sudo apt-get install picard 

but I get an error:
picard: Depends: python-tunepimp (>= 0.5.1) but it is not going to be installed
E: Broken packages

Please help!!

---

### Post by shinythings on 2006-09-16
I guess you are following the instructions in the MB wiki?

[http://wiki.musicbrainz.org/PicardLinuxInstall?highlight=%28picard%29#head-5f60c040c32c67c304b335181b88678ad34149c2](http://wiki.musicbrainz.org/PicardLinuxInstall?highlight=%28picard%29#head-5f60c040c32c67c304b335181b88678ad34149c2)

Perhaps you have not activated all the needed repositores (eg. Multiverse)?

---

