---
title: "Installing Gnash"
date: 2006-06-18
forum: Apple PPC Users
---

### Post by nib on 2006-06-18
Has anyone successfully installed Gnash and have some flash ability on PPC?  Several of my favorite Web sites are unuseable.

---

### Post by ebeyer on 2006-07-24
> **nib said:**
> Has anyone successfully installed Gnash and have some flash ability on PPC?  Several of my favorite Web sites are unuseable.

I have been attempting to compile the binary without success.  Has anybody else compiled it into PPC?

---

### Post by gleng on 2006-07-24
I've managed to compile the latest release (0.7.1), and it works as a stand alone player, but without sound.

Unfortunately the Firefox plugin didn't work at all for me.

---

### Post by kprasanna16 on 2006-08-02
can anyone please tell no to configure and install gnash 0.7.1
I tried it on Linux FC2 and got following error.
--------------------------------------------------------------------------
In file included from /usr/include/SDL/SDL_mixer.h:29,
                 from sound_handler_sdl.cpp:15:
/usr/include/SDL/SDL_rwops.h:102:1: warning: "SDL_RWtell" redefined
In file included from /root/flash/include/SDL/SDL_audio.h:33,
                 from /root/flash/include/SDL/SDL.h:30,
                 from ../libbase/tu_types.h:48,
                 from ../libbase/utility.h:15,
                 from ../libbase/container.h:72,
                 from ../server/Object.h:45,
                 from ../server/gnash.h:54,
                 from sound_handler_sdl.cpp:13:
/root/flash/include/SDL/SDL_rwops.h:110:1: warning: this is the location of the previous definition
In file included from /usr/include/SDL/SDL_mixer.h:31,
                 from sound_handler_sdl.cpp:15:
/usr/include/SDL/SDL_byteorder.h:40:1: warning: "SDL_BYTEORDER" redefined
In file included from /root/flash/include/SDL/SDL_stdinc.h:28,
                 from /root/flash/include/SDL/SDL_main.h:26,
                 from /root/flash/include/SDL/SDL.h:28,
                 from ../libbase/tu_types.h:48,
                 from ../libbase/utility.h:15,
                 from ../libbase/container.h:72,
                 from ../server/Object.h:45,
                 from ../server/gnash.h:54,
                 from sound_handler_sdl.cpp:13:
/root/flash/include/SDL/SDL_config.h:51:1: warning: this is the location of the previous definition
make[2]: *** [sound_handler_sdl.lo] Error 1
make[2]: Leaving directory `/root/flash/gnash-0.7.1/backend'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/flash/gnash-0.7.1'
make: *** [all] Error 2
--------------------------------------------------------------------------

Does anyone has any idea what is the problem

regards,
Prasanna

---

### Post by Ububurns on 2006-08-02
I have compiled and installed gnash on PPC, with the firefox plugin.

It is worth noting that Gnash is a work in progress. Yes, it can play some flash files, but without sound, and without user interaction (ie: flash games or "Click to play" etc.)

Regardless, it's great to know that you can at least partly knock out one of the top three "don't haves" for PPC (ie: flash, java and wmv3 playback).

I have made a deb for gnash on ppc - if anyone wants it, I'll put a link up here.

[Coincidentally, I've also got java in firefox, and wmv3 decoding working...]

---

### Post by eidex on 2006-08-02
hi, i'd be happy to get your deb !!

greetings, eidex

---

### Post by Ububurns on 2006-08-03
[FONT="Tahoma"]Please find gnash-0.7.1_powerpc.deb here.

Please let me know if it works for you - it works for me!  You may need to install a few other packages for this to work.  Being my first official deb, it doesn't know what libraries it requires to run.  I have a feeling it might need some SDL packages installed.

Would be nice to see gnash in a repo for Edgy, hey?

To check that this gnash has installed correctly, in the location bar of Firefox type in "about:plugins" and look for an entry titled "Shockwave Flash" that refers to gnash. [/FONT]

---

### Post by eidex on 2006-08-04
thanks a lot for the deb, just had to add one more lib and it worked, even the firefox plugin!

---

### Post by Ububurns on 2006-08-04
Eidex, 

Would you be able to to tell me what extra package you had to install to get gnash to work?  I would like to make it so that in the future, dependencies are automatically satisfied (like in the case of most other debs).

Ta!

---

### Post by eidex on 2006-08-04
i only had to install libgtkglext1, but i think with a fresh install you need more packages, i had some libs installed due to prior compiled software... is there a howto for building a deb, i always just compiled it with configure/make..

greetings

---

### Post by n00bWillingToLearn on 2006-08-04
> **Ububurns said:**
> [FONT=Tahoma]Please find gnash-0.7.1_powerpc.deb here.

Please let me know if it works for you - it works for me!  You may need to install a few other packages for this to work.  Being my first official deb, it doesn't know what libraries it requires to run.  I have a feeling it might need some SDL packages installed.

Would be nice to see gnash in a repo for Edgy, hey?

To check that this gnash has installed correctly, in the location bar of Firefox type in "about:plugins" and look for an entry titled "Shockwave Flash" that refers to gnash. [/FONT] I get "**Parse error**:  syntax error, unexpected '<' in **/www/vhosts/www.filelodge.com/html/fileads.php** on line [B]174" from that link. I would be glad to mirror it for you just send me the file @ trogdoor at gmail dot com
[/B]

---

### Post by Ububurns on 2006-08-06
It seems that filelodge has a couple of problems at the moment.

Try here for a ppc deb for gnash: [http://filexoom.com/files/11540/gnash-0.7.1_powerpc.deb]("http://filexoom.com/files/11540/gnash-0.7.1_powerpc.deb")

Thanks for your offer - but FileXoom seems to be just as great!

---

### Post by Breepee on 2006-08-06
> **Ububurns said:**
> I have compiled and installed gnash on PPC, with the firefox plugin.

It is worth noting that Gnash is a work in progress. Yes, it can play some flash files, but without sound, and without user interaction (ie: flash games or "Click to play" etc.)

Regardless, it's great to know that you can at least partly knock out one of the top three "don't haves" for PPC (ie: flash, java and wmv3 playback).

I have made a deb for gnash on ppc - if anyone wants it, I'll put a link up here.

[Coincidentally, I've also got java in firefox, and wmv3 decoding working...]
isn't there a pretty usable GNU Java? Together with Gnash that strikes out 2 of the 3, and wmv isn't something to be particularly unhappy about ;)

---

### Post by Ububurns on 2006-08-07
IBM's java (JDK - not JRE) works for me in Firefox, on PPC.

It took time to set it up, but it runs fine (albiet a litte slow).

I would post my deb of java for ppc... but IBM would be unhappy with me, I believe.

If you want more information, I can let you know how I went about it.

---

### Post by Ububurns on 2006-08-07
.

---

### Post by avtolle on 2006-08-09
>   If you want more information, I can let you know how I went about it. 

I certainly would. For those installing Gnash, I had another dependency other than that listed by eidex. I needed to install libsdl_mixer (something, I didn't keep a good note) through Synaptic. Once the two dependencies were met, works as well as can be expected (no sound, of course, Firefox plugin does what it's supposed to do with the things I've tried out; probably others will find issues extant). Good job.

---

### Post by icase81 on 2006-08-09
I got the .deb to install properly (i think) but it doesn't show up in firefox at all. Is there a way to manuall make firefox see it?


Ignore this. I got it to work. Works great, thanks! I was missing libgtkglext

---

### Post by n00bWillingToLearn on 2006-08-11
> **icase81 said:**
> I got the .deb to install properly (i think) but it doesn't show up in firefox at all. Is there a way to manuall make firefox see it?


Ignore this. I got it to work. Works great, thanks! I was missing libgtkglext

I am having the same problem, how did you get it to work? I already have libgtkglext1 installed. It is also worth noting that when I tried just double clicking the .deb file I got this error from GDebi [http://trogdoor.googlepages.com/gnashInstallError.png](http://trogdoor.googlepages.com/gnashInstallError.png)
But when I used `dpkg -i`it did not give any errors. When I try to run gnash from the terminal I get ```
$ gnash
gnash: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory
```

*update* I installed libsdl-mixer1.2 and libmad0 and everything is working great now ( although gdebi is still not happy with the .deb )

---

### Post by fuoco on 2006-10-04
Are there any news about this? Is there a more up to date deb that takes care of dependencies? or better yet a repo that includes that?

By the way for java I think at some point there would be a plugin that works with the GNU java implementation... that would be better than IBM. I'm talking about 'gcjwebplugin'.

---

### Post by kellogs on 2006-10-05
i installed Gnash from CVS recently, and now its working as firefox plugin perfectly.you must compile it with "./configure --enable-plugin" as the only needed option. all the rest is done automatically.

the dependencies that are needed for gnash to work are shown in screen when you first invoke configure.

for those who may compile it: install from CVS, and it will work directly... no need to link or copy any library in firefox plugins directory as in previous versions, it does work now with firefox 1.5.0.7.

---

### Post by fuoco on 2006-11-19
Anyone tried the new version 0.7.2 ? ;)

---

### Post by eidex on 2006-11-22
thanks for the tip, i just compiled it, havent noticed any differnce yet, sites with "light" flash implementation work fine, others like youtube still dont work.

greetings..

---

### Post by Torrance on 2006-11-22
Yeah, Youtube and Myspace videos, for example, are still a few months off from working. When that starts working I'll be installing Gnash (ah, all thse wonderful emo videos! ;) ).

Also, if you don't want to compile, 0.71 is in the unstable tree in Debian... and 0.72 can't be too far off.

---

### Post by fuoco on 2006-12-07
How do I get gnash, is there a deb somewhere ? I found on the feisty and debian repos but I'm using edgy and I failed to install them manually that way - is it possible to do it?

---

### Post by Gen2ly on 2006-12-17
See:

[Got Gnash Going! Woot!]("http://ubuntuforums.org/showthread.php?p=1896551#post1896551")

---

### Post by fuoco on 2006-12-18
Yeah I should have mentioned that gnash is now both in feisty and in edgy-backports.
Just install the package 'mozilla-plugin-gnash' and that would take care of everything needed.

---

### Post by saritha123 on 2007-07-26
i had installed gnash ,how can i use SDL to run gnash? can u help me out

---

### Post by saritha123 on 2007-07-26
can u tell me how to install gnash with SDL,how to run as standardalone player,wht r the packages,how to install,how did u write a configure ,can u help me out

---

### Post by stmiller on 2007-07-26
Gnash 0.8.0 is now in Feisty backports. It plays back youtube, lulu.tv, revision3, and perhaps other video.

Assuming you are using Feisty, do this:

Applications>Add/Remove>Preferences>

Updates> Check 'unsupported updates' Feisty Backports

Close and reload if it asks. Now search in Add/Remove for gnash and install.

---

