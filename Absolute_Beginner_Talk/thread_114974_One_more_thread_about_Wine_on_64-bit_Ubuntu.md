---
title: "One more thread about Wine on 64-bit Ubuntu"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by J-B on 2006-01-09
Hi all, 

First let me say that I know that there are already several threads dealing with installing Wine in 64-bit Ubuntu.  I did a search and read through tons of them.  But I'm totally lost here, and embarassingly enough, don't really know enough about linux to understand half of what I read.  

So here's the thing.  I'm getting the same error message when trying to compile Wine that alot of people are.  This:

"Running configure...

configure: creating cache config.cache
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details."

My questions are thus:

1.  Has anybody successfully installed Wine in 64-bit Ubuntu?  

2.  If so, would you be willing to walk a noob through the process?  

I'm totally lost.  Any help would be appreciated immensely.

---

### Post by poofyhairguy on 2006-01-09
> 
1.  Has anybody successfully installed Wine in 64-bit Ubuntu?  


Yes with chroot.

Honestly, 64 bit Ubuntu is pretty darn hard. Even I have to admit that. I tried to use it recently and despite a huge amount of Linux knowledge I gave up and move back to 32 bit version.

Most problems like the one you are having can only be solved with chroot. Here is best guide for it:

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Good luck.

---

### Post by diggs on 2006-01-09
While we are on the topic of wine (and me sucking at linux) I did this:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
but I can't figure out exactly what I should do. when I search for wine in the synaptic package manager, I get a whole bunch of options. What package do I install and after it's been installed, how do I run it? I want to install 2 programs: windows media player and photoshop CS to start. this seems like an awful lot of work to watch some porn, IMO.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=diggs]While we are on the topic of wine (and me sucking at linux) I did this:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
but I can't figure out exactly what I should do. when I search for wine in the synaptic package manager, I get a whole bunch of options. What package do I install and after it's been installed, how do I run it? I want to install 2 programs: windows media player and photoshop CS to start. this seems like an awful lot of work to watch some porn, IMO.[/QUOTE]

That is too much for porn. Totem-xine and VLC has played EVERY file I have between them. All of them. So I hope its just not for the media player.

And as far as Photoshop CS....I don't think it runs that well in WINE. The older versions run really well, but CS is too new and its support has not been perfected yet.

If you want to try, the best way to install WINE is to use Automatix. Then click on some exe and it should work.

---

### Post by J-B on 2006-01-09
[QUOTE=poofyhairguy]Yes with chroot.

Honestly, 64 bit Ubuntu is pretty darn hard. Even I have to admit that. I tried to use it recently and despite a huge amount of Linux knowledge I gave up and move back to 32 bit version.

Most problems like the one you are having can only be solved with chroot. Here is best guide for it:

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Good luck.[/QUOTE]


Hmmm....I don't know.  MAybe I should just switch to 32 bit.  I mean, is there even any advantage to 64 bit?   I've never run 32 so I don't have anything to compare my current install to.    But it does seem like I have problems every time I try to install anything.

---

### Post by J-B on 2006-01-09
Just installed 32 bit Ubuntu.  Automatix is installing now, and thus far no problems.  I don't see a bit of difference between the two flavors of Ubuntu.  I dunno,   but I just don't see any reason at all for 64bit.  At least not at this point.

---

### Post by poofyhairguy on 2006-01-09
[QUOTE=J-B]Just installed 32 bit Ubuntu.  Automatix is installing now, and thus far no problems.  I don't see a bit of difference between the two flavors of Ubuntu.  I dunno,   but I just don't see any reason at all for 64bit.  At least not at this point.[/QUOTE]

I honestly thought the 64 bit version felt faster. 

But is it worth it? Not for me...I gave up.

---

### Post by diggs on 2006-01-09
[QUOTE=poofyhairguy]That is too much for porn. Totem-xine and VLC has played EVERY file I have between them. All of them. So I hope its just not for the media player.

And as far as Photoshop CS....I don't think it runs that well in WINE. The older versions run really well, but CS is too new and its support has not been perfected yet.

If you want to try, the best way to install WINE is to use Automatix. Then click on some exe and it should work.[/QUOTE]
Seriously!!

teh pr0n doesn't work! well at least the files that require a password/user name in WMP. is nobody l33t enough to help me out here?

---

### Post by J-B on 2006-01-10
One more question about Wine, and I didn't see the need to make another thread.   Where does automatix install Wine to?   I installed through automatix, and then tried to run Winecfg, but I got the error "command not found".  So I figured it just wasn't in my path, so I used the "find / "wine""   but it couldn't find it either.  Where the heck is Wine?

---

