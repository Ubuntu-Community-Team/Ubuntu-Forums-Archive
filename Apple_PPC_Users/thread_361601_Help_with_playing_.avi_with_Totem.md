---
title: "Help with playing .avi with Totem"
date: 2007-02-14
forum: Apple PPC Users
---

### Post by maniacrobbins on 2007-02-14
I'm trying to play a .avi movie that uses the Xvid codec.  How do i install this into Totem so my movie plays?  Or should i just find another player for my PPC Mac?

Thanx

Dave

---

### Post by mssever on 2007-02-14
Does this help? [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by maniacrobbins on 2007-02-14
No, sorry it doens't.  I tried it and it didn't seem  to work.  Synaptic downloaded the packages but when I pasted the given code, an error came up.

---

### Post by grazie on 2007-02-14
Some of the Windows codecs will not play on ppc, but you shouldn't have problems with Xvid. I tend to use mplayer and vlc (which has the advantage of coming with its own codecs). Also the [easyubuntu]("http://easyubuntu.freecontrib.org/") script is a great little tool for getting exta codecs and checking what's installed already.

---

### Post by maniacrobbins on 2007-02-15
MPlayer doesn't work with the video I'm using.  I'm responding to this post with my OS X computer and will post agian if the EasyUbuntu package works.

---

### Post by ekravche on 2007-02-15
you'll need to enable external repros and then install  libavifile-0.7c2 and  avifile-xvid-plugin. I enabled all repros through automatix.

---

### Post by dpny on 2007-02-15
> **ekravche said:**
> you'll need to enable external repros and then install  libavifile-0.7c2 and  avifile-xvid-plugin. I enabled all repros through automatix.

There's no PPC version for libavifile.

---

### Post by maniacrobbins on 2007-02-16
Easy Ubuntu doesn't work and neither does MPLAYER.  When I try to load the video with GXine though, it seems like it loads.  when I hit play, the GXine logo stays on the screen but the bar at the bottom jumps from point to point in the movie. (10:00-15:00-20:00).  IS THIER ANY WAY TO PLAY .AVI MOVIES USING THE XVID CODEC ON PPC COMPUTER USING UBUNTU?

---

### Post by grazie on 2007-02-16
I can play thiis [avi xvid test video]("http://tdw.nchc.org.tw/demo/passive_stereo/smatsuri_xvid.avi") (it's a 15M download) wthout any problems in both vlc and mplayer. If there's something you can't play give the details. If you've tried stuff, state exactly what you've done. You're probably trying to use an unsupport windows codec.

---

### Post by maniacrobbins on 2007-02-17
Thanx everybody, but I got it figured out.  I didn't know VLC media player could run on PPC.

---

### Post by sh4d3z on 2007-03-01
Totem could not play 'fd://0'.

Video codec 'XviD' is not handled. You might need to install additional plugins to be able to play some types of movies

this is the err i'm getting
vlc works fine
i'd really like to get mplayer working again like i had it on dapper
i followed the how-to [HTML]http://ubuntuguide.org/wiki/Dapper[/HTML] for that, but this one [HTML]http://ubuntuguide.org/wiki/Ubuntu_Edgy[/HTML] ain't working so well
atoumatix is funny about installing - sometimes it works, sometimes it doesn't 
take avidemux... i installed that via automatix first time no go, second time installed it, but no entry via Applications > Sound and Video > Avidemux... i uninstalled it and reinstalled it and now the entry is there
easyubuntu just plain sux balls in my opinion(maybe i'll screw with it again nevertheless)
and then there is this script [HTML]http://www.iki.fi/kuparine/comp/ubuntu/install.sh[/HTML]  (very beautiful i might add), but still no way to play avi in mplayer or totem
i'm not all that pleased with this release(edgy), on dapper it just worked, but i do enjoy trying to get this to work anyways... guess it is because i don't have much of a life, lol, but the fixes should be addressed by yall l33t mofos, cus i noticed this distro seems to be a way to save the souls (lol) of the winblows users and they're not too much into hacking for the most part (sorry if i'm stereotyping)

okay, i'll stop ranting about this(i'm drunk) and try to get the solution to this prob myself... oh and google sux.......

---

