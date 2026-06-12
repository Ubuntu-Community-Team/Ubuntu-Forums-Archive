---
title: "Flash for G5 PPC"
date: 2010-04-09
forum: Apple Hardware Users
---

### Post by Relative Prime on 2010-04-09
Hi there,

Flash videos are displayed in a grey box on my PPC G5 running karmic, I think this is most likely due to the G5 needing 64-bit flash. I'm not having much luck googling about for a workable solution though. 

I've tried the gnash plugin by installing:  mozilla-plugin-gnash and swfdec-mozilla as per the instructions at: 
[https://wiki.ubuntu.com/PowerPCFAQ#Flash,%20Flash%20video%20and%20Gnash](https://wiki.ubuntu.com/PowerPCFAQ#Flash,%20Flash%20video%20and%20Gnash)

It is enabled and shows in about: plugins as:
File name:  libgnashplugin.so Shockwave Flash 10.1 r999. Gnash 0.8.6, the GNU SWF Player

Does anyone have any hints on how to get flash to work on a G5?

Thank you,
Relative Prime

---

### Post by Dukenukemx on 2010-04-28
I get the same problem here, but with a 32-bit Ubuntu 9.10.  Why does gnash display a white box where flash should be?

---

### Post by Dukenukemx on 2010-04-28
I uninstalled Gnash in favor of swfdec and it works, sorta.  Videos from [Newgrounds](www.newgrounds.com) mostly work, except for it's really slow and sound stops working randomly.  Youtube doesn't work at all.

I got a more updated version of swfdec, version 0.9.2.  Flash videos don't seem to cut audio out as much, but now it's even slower.

From what I understand, Gnash is better, but Gnash doesn't seem to work.  Some people seem to have gotten it to work by compiling the latest on their own.  I believe Gnash is version 0.8.7 now.  

Can someone please make a .deb file to install the latest working version of Gnash for PPC?  I know I can download videos from YouTube and play them separately, but I want working flash for websites like Newgrounds.

---

### Post by linuxopjemac on 2010-04-28
If I have time, I can do it for you tonight.

---

### Post by Dukenukemx on 2010-04-28
Thanks, that would be great, as I'm not the only one having problems it seems.

---

### Post by linuxopjemac on 2010-04-28
Update:
I could finally configure gnash. It needs a lot of stuff. I am now making the beast, My PowerBook Pismo baby really gets hot at the moment. I will post when I know more. By the way, I totally forgot, but I am builing in a 32-bits environment. I don't have a G5 unfortunately, so I can't build a 64-bits version I'm afraid.

---

### Post by B_Free on 2010-04-28
linuxopjemac explained this in previous postings. Greasemonkey extension for Firefox works great. You just have to find the right script to attach to that extension. You can download a Youtube video as a Mp4 or flv or ? 
Right now I am experimenting with other sites.

---

### Post by linuxopjemac on 2010-04-28
I never tried flash myself, thinking it would be impossible. Well, it`s not. I installed clive and I did in my video folder
```

clive URL-of-youtube

```
this will give you a flv file in that folder

then open vlc. Open the vlc file in vlc. I could then see the video, but no sound...

---

### Post by linuxopjemac on 2010-04-28
It only worked once :( I get an error now

main demux error: possibly corrupt module cache

in verbose:
cannot load module `/usr/lib/vlc/demux/libavformat_plugin.so' (/usr/lib/libavcodec.so.52: R_PPC_REL24 relocation at 0x0daa64c4 for symbol `cos' out of range)

---

### Post by Dukenukemx on 2010-04-28
I don't have a problem watching YouTube videos, as I just use a FireFox add on called DownloadHelper.  It downloads .flv or .mp4 videos right away.  Then I use Vlc to watch them.  

But again, I'm interested in flash based websites like Newgrounds.com, where they don't use .flv or .mp4 flash videos.

BTW, I don't have a G5 Mac, but I do have a G4.  Having it as 32-bit is perfect for me, but sucks for Relative Prime, who started this thread.

---

### Post by linuxopjemac on 2010-04-29
I am sorry, the make process ended in an error:
```

gtk.cpp: In member function &#8216;void gnash::<unnamed>::PreferencesDialog::addPlayerTab()&#8217;:
gtk.cpp:1671: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.
make[4]: *** [gtk_gnash-gtk.o] Error 1
```

Don't know what to do with this.

I am trying one more time...It looks more promising this time....Hang on.

---

### Post by linuxopjemac on 2010-04-29
Ok, got it now. You can download it at:
[http://mac.linux.be/files/gnash_0.8.7-1_powerpc.deb](http://mac.linux.be/files/gnash_0.8.7-1_powerpc.deb)

   1. Install Gnash
   2. Copy or create a symbolic link to libgnashplugin.so in your Mozilla plugins directory.
something like: /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) or /usr/lib/firefox/plugins/flashplugin-alternative.so (firefox-plugin) linked with /usr/lib/gnash/libgnashplugin.so 
Let me know if it works.

update, it does not work. I forgot to set something in ./configure. Keep you updated...later.

---

### Post by zeroti on 2010-04-29
Great! :P I'm curious though, what's the difference between your compiled version and what I can download from the ubuntu servers?

---

### Post by linuxopjemac on 2010-04-29
The one you can download is built in a Lucid environment. I will try to recompile that stuff (as a backport) in Karmic.

---

### Post by Dukenukemx on 2010-05-01
Well, I installed lucid and have Gnash 0.8.7 installed and working.  Guess if a PPC Ubuntu owner wants flash, you gotta upgrade to lucid.  I got it right from the the repository.  

So far it plays flash better then swfdec, but in some cases swfdec is better.  Both Gnash and swfdec screw up sound when you change the volume in Ubuntu.  Flash videos tend to get out of sync easily in Gnash, and I don't mean YouTube like videos.  Newgrounds videos that are large can easily get out of sync.  Lowering the detail doesn't seem to actually effect the detail.  BTW, the Mac OS X version would also skip frames, but it at least stayed in sync.  Not a big deal when you consider the videos weren't watchable in Mac OS X either.

YouTube still doesn't work, but I don't think it's Gnash's fault.  It requests codecs to be installed, and the required codec couldn't be found for YouTube.  Bet there's a way around this, but I haven't tried looking.  I know it works because you can see the YouTube player appear and it shows related videos, it just needs the correct codec to play them.

---

### Post by %hMa@?b&lt;C on 2010-06-01
try out lightspark
[http://en.wikipedia.org/wiki/Lightspark](http://en.wikipedia.org/wiki/Lightspark)
its a new project that seems promising.

---

### Post by sha.goyjo on 2010-06-02
> **linuxopjemac said:**
> Ok, got it now. You can download it at:
[http://mac.linux.be/files/gnash_0.8.7-1_powerpc.deb](http://mac.linux.be/files/gnash_0.8.7-1_powerpc.deb)

   1. Install Gnash
   2. Copy or create a symbolic link to libgnashplugin.so in your Mozilla plugins directory.
something like: /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) or /usr/lib/firefox/plugins/flashplugin-alternative.so (firefox-plugin) linked with /usr/lib/gnash/libgnashplugin.so 
Let me know if it works.

update, it does not work. I forgot to set something in ./configure. Keep you updated...later.

linuxopjemac, Do you know of any current powerpc PPA's? If not, we should definitely start one up. Packages like this, and the packages that are getting dropped from medibuntu, really need to be available for ubuntu PPC users. If there isn't one, one should be made

---

### Post by linuxopjemac on 2010-06-02
I don't know of any, not for Ubuntu. I have some files on my own site.

---

### Post by sha.goyjo on 2010-06-03
Maybe, if we compile lightspark, and a couple other things, we might have some success.

---

### Post by linuxopjemac on 2010-06-04
I tried that, I couldn't do it. But if you succeed, good luck. It would be great indeed.

---

### Post by sha.goyjo on 2010-06-04
Yeah, I see the problems with lightspark. Missing dev-libs, which would have to be compiled first in order to compile lightspark. Maybe I'll give it a try sometime this summer, but other projects are mounting, strong likelyhood that I won't be able to get to it.

---

