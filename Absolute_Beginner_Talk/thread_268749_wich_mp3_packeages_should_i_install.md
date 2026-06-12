---
title: "wich mp3 packeages should i install"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2006-09-30
i have xmms working ok... but.. isnt there a way to just plug the mp3 support to al the aplications... like, the default player... is it able to make it read mp3.

also serpentine audio cd creator still not accept mp3 files. How can i add suport for mp3 and some other formats?

should i install any codec? can i do it wsing apt?

---

### Post by Iarwain ben-adar on 2006-09-30
Hi,
if you use the xine engine
```
sudo apt-get install libxine-extracodecs
``` should do the trick.

If you use an other engine, you probabely have to replace xine with the other engine.


Iarwain

---

### Post by easyease on 2006-09-30
the first page i go to whenever ive got a fresh install of ubuntuy is this one, 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 then i merrily read through and cut and paste the bits i want to get everything set up nicely media-wise.

---

### Post by pedrotuga on 2006-09-30
i'm sorry, but what's the xine engine?
i use whatever one came with the default instalation.

---

### Post by easyease on 2006-09-30
xine is a different media player, read through that page i showed you above and you can install all the codecs etc you need through the terminal depending on which version of ubuntu you are using.

---

### Post by pedrotuga on 2006-09-30
ok, something is worng with my sources.list, this package does not exist:
gstreamer0.10-pitfdll

i never got this whole sources mess... does it maters wich country i am from? why? if not can somebody provide me a full working repository list?

---

### Post by PPAAUULL on 2006-09-30
Just use Automatix or Easy Ubuntu to install the codecs. That is what I always do.

---

### Post by PPAAUULL on 2006-09-30
Saves time too!!!!

---

### Post by easyease on 2006-09-30
> **pedrotuga said:**
> ok, something is worng with my sources.list, this package does not exist:
gstreamer0.10-pitfdll

i never got this whole sources mess... does it maters wich country i am from? why? if not can somebody provide me a full working repository list?have you enabled your extra repository's in synaptic? read the bit about universe and multiverse repositories in the "before you start" paragraph on that page. automatix is a very useful application but its good to get to get a grip of things manually a bit sometimes, that way you learn about linux.

---

### Post by PriceChild on 2006-09-30
> **PPAAUULL said:**
> Just use Automatix or Easy Ubuntu to install the codecs. That is what I always do.Yeah, using automatix means you don't get anywhere near understanding how your system is working or how to fix it.

Those programs don't crash very well either....

---

### Post by PPAAUULL on 2006-09-30
Listen how the hell is copying a command from here any better? oh ya that is right it isn't!!!!

---

### Post by pedrotuga on 2006-09-30
mmm...
i went ant activate the universe and multivers repositories and...

```


The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences


http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz: 404 Not Found
http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz: 404 Not Found
http://theli.free.fr/packages/breezy/./Packages.gz: 404 Not Found
ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz: Unable to fetch file, server said 'Failed to open file.  '
ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz: Unable to fetch file, server said 'Failed to open file.  '
ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz: Unable to fetch file, server said 'Failed to open file.  '
ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz: Unable to fetch file, server said 'Failed to open file.  '

```

---

### Post by easyease on 2006-09-30
hey mate that looks like a bad source list, try going here.....
 [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
and working through the questions and it will give you the perfect source list to copy and paste into your sources list.

---

### Post by pedrotuga on 2006-09-30
ok... sorry. I guess all those repositories are breezy repositories. I upgraded from breezy.
I got it working by installing all those packages listed in
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

thank you all.

I usually use apt simply because i am used to, using automatix, syaptic, whatever... i dont know... i guess they are all as easy to use as apt. Ok... i got to learn that i should activate the universe and multiverse repositories and what they are.

anyway, please dont start any kind of fight because of this.

---

### Post by easyease on 2006-09-30
no fights round here my friend........ :-D

---

### Post by pedrotuga on 2006-09-30
> **easyease said:**
> hey mate that looks like a bad source list, try going here.....
 [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
and working through the questions and it will give you the perfect source list to copy and paste into your sources list.

my experience with source-o-matic is terrible. Also, my country's (portugal) free repository servers are everything but stable or reliable.
I think i will ask a friend for a copy of a sources.list or something.

---

### Post by easyease on 2006-09-30
well if i were you id just delete those koti and plf breezy repo's by using synaptic firstly. glad you got the sound working though.

---

