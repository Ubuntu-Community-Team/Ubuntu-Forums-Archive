---
title: "install problem"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by paulmann on 2007-04-22
I've been trying to install some sort of MP3 codec thing so that I can play MP3s on my laptop.  Tried a few but so far no luck.  

The ./configure bit seems to go OK - at least I don't get any error messages.
The make bit seems to go OK - again, no error messages that I can see.
But the make install bit doesn't seem to work.  Here are the last few lines:

make[3]: Entering directory `/home/paul/lame-3.97/libmp3lame'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libmp3lame.la' '/usr/local/lib/libmp3lame.la'
/usr/bin/install -c .libs/libmp3lame.so.0.0.0 /usr/local/lib/libmp3lame.so.0.0.0
/usr/bin/install: cannot create regular file `/usr/local/lib/libmp3lame.so.0.0.0': Permission denied
make[3]: *** [install-libLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/paul/lame-3.97/libmp3lame'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/paul/lame-3.97/libmp3lame'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/paul/lame-3.97/libmp3lame'
make: *** [install-recursive] Error 1
paul@paul-laptop:~/lame-3.97$ 

Can anyone make any suggestions?  Thank you for your time.

---

### Post by NESFreak on 2007-04-22
just install mp3 support from the reposity?

if you want lame it's just there.

If you want playback support
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Campingman on 2007-04-22
What package are you trying to install.  If it is lame that is in the repositories and can be installed from system/administration/synaptic package manager and search for lame.

---

### Post by kariopto on 2007-04-22
Are you only typing make install? It should be sudo make install. This should solve your problem.

---

### Post by paulmann on 2007-04-22
All I want to do is be able to play MP3s on my laptop.  Didn't realise it would be so difficult.

The sudo make install went OK with no error messages, but I still can't play any MP3s through applications such as rhythmbox as still get the error about codec not being installed.

However, if I have an mp3 on the desktop and move the mouse over it, the little blue "note" appears over the icon and it starts playing with no problem at all.  I don't understand why it should play this way but not if I try to play the mp3 through some sort of music player.

I've no idea what things like repositories and lame and synaptics and tarballs mean.  I've spent the last two weeks reading various "easy / beginners" guides but feel like giving up and going back to Windows.  But I'll give it one more try.... can someone suggest what I should do now?

As ever, thanks for your help.

---

