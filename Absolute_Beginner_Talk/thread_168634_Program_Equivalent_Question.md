---
title: "Program Equivalent Question"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-30
I want to know what would be a program to convert video files, from say avi to ogg theora or something.  Also, what format do dvd movies usually use?

---

### Post by Jason_25 on 2006-04-30
ffmpeg works great for that.  

Here's an example.  It's mostly self-explanatory.  man ffmpeg for more.
```

ffmpeg -i videotoconvert.avi -ac 2 -ar 44100 -ab 128 -b 3000  -s 640x480 convertedvideo.ogg

```
I don't know if that's the exact syntax for your application, but maybe it will work.

DVD is basically mpeg2.  It's more complicated than that though.

---

### Post by nalmeth on 2006-04-30
you can go the command line way, or download avidemux
sudo apt-get install avidemux

---

### Post by user1397 on 2006-05-01
Hmm that's weird, avidemux isn't in the universe or multiverse. command line doesn't work, synaptic doesn't work, even though i have multiverse enabled.
what's wrong?

---

### Post by Jason_25 on 2006-05-01
What do you mean by 'command line doesn't work'? and 'synaptic doesn't work'?

---

### Post by user1397 on 2006-05-01
[quote=Jason_25]What do you mean by 'command line doesn't work'? and 'synaptic doesn't work'?[/quote]
I mean that when i type ```
sudo apt-get install avidemux
```
or i try to look for it in synaptic, i get the "E: Couldn't find package avidemux" message

---

### Post by user1397 on 2006-05-01
so ffmpeg is purely a command line program? (no GUI)?

---

### Post by Jason_25 on 2006-05-01
Your sources.list must be corrupted in some way.  I just searched for it and found it.  ffmpeg is purely command line.  The front ends for it are not very good.

---

### Post by user1397 on 2006-05-01
How can I fix my sources.list?

---

### Post by user1397 on 2006-05-01
This is what my sources.list looks like:

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

deb [http://theli.free.fr/packages/breezy/](http://theli.free.fr/packages/breezy/) ./
## created by arniewinechanged

---

### Post by Jason_25 on 2006-05-01
```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse 

deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse 

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse 
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse 

```
Here you go.  Replace your entire sources.list with this.  Change all instances of dapper to breezy if you are using that.  Say with gedit's find and replace function.  Then
```

sudo apt-get update

```

Edit:  I just can't keep up.

---

### Post by user1397 on 2006-05-01
I replaced the parts where it starts with deb, not ## deb, and did sudo apt-get update and it worked fine. 
it still can't find avidemux though!!!

---

### Post by Jason_25 on 2006-05-01
Yeah...if you use mine it will work.  Remember to change all instances to breezy.

---

### Post by user1397 on 2006-05-01
Here's my new sources.list:

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse 
## created by arniewinechanged

is anything wrong?

---

### Post by Jason_25 on 2006-05-01
Yeah.  Comment or delete anything in the file that I didn't give you.  What I posted was all you need to get started.

---

### Post by user1397 on 2006-05-01
Oh ok. still, for some odd reason, avidemux doesn't show up if i search for it in synaptic!!

---

### Post by Jason_25 on 2006-05-01
I just searched for it in the ubuntu archives, and found that it's not available on breezy.  It's only available on dapper.  Sorry about that.  I don't use breezy anymore so I didn't know.

---

### Post by user1397 on 2006-05-01
[quote=Jason_25]I just searched for it in the ubuntu archives, and found that it's not available on breezy.  It's only available on dapper.  Sorry about that.  I don't use breezy anymore so I didn't know.[/quote]
Ah, well that explains that :)
Oh well, any other program that is like avidemux that can be found in breezy?
(i didn't like ffmpeg!)

---

### Post by nalmeth on 2006-05-01
what? I don't even have it on dapper. Only on my breezy desktop.
I don't know why you have so much trouble finding it. I'm not in front of my Breezy now, but you should be able to find a .deb somewhere, like sourceforge.
It's an excellent app, really.
Kino is supposed to be good too, but I prefer avidemux

---

### Post by olsonar on 2006-05-01
all the ubuntu .deb files for all versions of ubuntu can be found at packages.ubuntu.com 
the avidemux page is here: [http://packages.ubuntu.com/dapper/graphics/avidemux]("http://packages.ubuntu.com/dapper/graphics/avidemux")
it's got a lot of dependencies, so be prepared to to a lot of downloading.

---

### Post by nalmeth on 2006-05-02
I just realized that I had used automatix to install avidemux.
If you want it done easy for you, you could do that.

---

### Post by user1397 on 2006-05-02
[quote=nalmeth]I just realized that I had used automatix to install avidemux.
If you want it done easy for you, you could do that.[/quote]
Thanks, finally that worked!

---

