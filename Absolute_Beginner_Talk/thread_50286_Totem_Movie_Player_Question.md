---
title: "Totem Movie Player Question"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-07-19
It seems I need libdvdcss installed in order for Totem to playback DVDs. I found a source for various libdvdcss binaries but I'm not sure which one is correct for my system. How does one figure out which one is correct ?

---

### Post by Kyral on 2005-07-19
Easy.

sudo apt-get install libdvdcss2 libdvdcss2-dev

When in doubt, search Synaptic :P

---

### Post by damonw5 on 2005-07-19
[QUOTE=grofaz]It seems I need libdvdcss installed in order for Totem to playback DVDs. I found a source for various libdvdcss binaries but I'm not sure which one is correct for my system. How does one figure out which one is correct ?[/QUOTE]
 The best way is to follow the instructions at UbuntuGuide.org (or the ones on this mirror, since the main page seems to be down right now):

[http://www.frankandjacq.com/ubuntuguide/5.04/#dvdplayback](http://www.frankandjacq.com/ubuntuguide/5.04/#dvdplayback)

Tell us how that works out. :)

---

### Post by damonw5 on 2005-07-19
[QUOTE=Kyral]Easy.

sudo apt-get install libdvdcss2 libdvdcss2-dev

When in doubt, search Synaptic :P[/QUOTE]
 Before you do what Kyral suggests, you must have the extra repositories installed as described in the ubuntuguide. More info can be found at [http://www.ubuntuguide.org/#dvdplayback](http://www.ubuntuguide.org/#dvdplayback) or [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) .

---

### Post by grofaz on 2005-07-19
I've got the extra repositories for synaptic but when I search for libdvdcss or libdvdcss2 etc. synaptic comes up blank. I opened Totem and followed a link in the Totem manual concerning DVD playback and found a whole list of libdvdcss binaries but I'm not sure which file is correct for my machine. Should be either i386 or x86, but which ?

And, why doesn't libdvdcss show up in my synaptic pakages list ?? Everybody keeps saying to get the extra repositories which I have done but libdvdcss isn't there as far as I can see. Help!!

Cunfused

---

### Post by grofaz on 2005-07-19
Here's what happens when I try sudo apt-get:


gc@kudu:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

So what the heck does this mean ??

---

### Post by damonw5 on 2005-07-19
[QUOTE=grofaz]Here's what happens when I try sudo apt-get:


gc@kudu:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

So what the heck does this mean ??[/QUOTE]
 can you "sudo gedit /etc/apt/sources.list" and paste the file here?

Or, if you haven't refreshed your package lists since you added the new repositories, click "refresh" in Synaptic and search for the package again.

---

### Post by grofaz on 2005-07-19
Ask and you shall receive. Here it is...



deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

Regards,
grofaz

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=grofaz]Ask and you shall receive. Here it is...

[/QUOTE]

There is you problem. Replace whats in your sources.list with this one:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then do:

> sudo apt-get update

and then try to install what you want.

---

### Post by buddyjay on 2005-07-31
I am having the exact same problem.  I have all of the updated repositories, but libdvdcss2 is still not found.

---

### Post by ieatw0rms on 2005-07-31
I found this information very helpful.  I stared with no audio or video on avi or dvd.  with this information i was able to get video on both.  i found information in the users guide about codecs and now ive got everything but audio on dvds.

any suggestions??

---

