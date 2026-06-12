---
title: "rmvb with mplayer"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by tomcheng76 on 2007-07-19
I installed w32codecs and mplayer plays rmvb without problem (ffmpeg or win32codec)
however, when i want to seek the video to a position, it just go back to the beginning position , the only way to seek is to use mouse scroll,which is not the case for other format
Actually i am tired using mouse scroll, finger is pain due to overuse of muscle 	:lolflag:
how to fix it. Could someone point me in the right direction.

i tried real player but some rmvb cannot be played normally

---

### Post by tomcheng76 on 2007-07-19
bump

---

### Post by phidia on 2007-07-19
Have you looked at xine totem-xine? I'm not sure but that might give you the feature you want.

---

### Post by misfitpierce on 2007-07-19
Maybe try SMplayer can be found at [http://getdeb.net](http://getdeb.net) and it is an upgraded version of mplayer basically.

---

### Post by tomcheng76 on 2007-07-19
So, is that everyone using mplayer+w32codecs will have this problem?

phidia
I go totem with gstreamer based, how to install both version ?
i remember that i need gstreamer for amarok mp3 support, will it be affected if i install totem-xine ?

misfitpierce
i will give smplayer a shot, i saw Neo at Smplayer hp, it seems trustable lol

---

### Post by phidia on 2007-07-19
> **tomcheng76 said:**
> So, is that everyone using mplayer+w32codecs will have this problem?

phidia
I go totem with gstreamer based, how to install both version ?
i remember that i need gstreamer for amarok mp3 support, will it be affected if i install totem-xine ?

misfitpierce
i will give smplayer a shot, i saw Neo at Smplayer hp, it seems trustable lol


I don't use amarok so I'm not sure. I know that the package manager will remove a gstreamer package but is that _the_ gstreamer or a virtual package?

Maybe someone here can shed more light on this.

---

### Post by tomcheng76 on 2007-07-20
Smplayer cannot play rmvb

i just simply remove totem-gstreamer and install totem-xine, then rmvb is okay on totem, thanks phidia

btw, how to set dvd drive in totem ?
i cannot set it to /media/iso that i usually mount image on

---

### Post by rvm4000 on 2007-07-20
SMPlayer /MPlayer can play rmvb videos. Just be sure you have the w32codecs package installed, it provides a codec for it.

The seeking problem can be fixed by updating MPlayer to the a SVN release.

---

### Post by m0rph on 2007-07-20
Hey this RMVB format blows

If you follow fenian instructions #kudos fenian# you can converty your RMVB files to Avi

[http://ubuntuforums.org/showthread.php?t=454130&highlight=mencoder+in.rmvb](http://ubuntuforums.org/showthread.php?t=454130&highlight=mencoder+in.rmvb)

This works well...........

=D>

---

### Post by Kimm on 2007-07-20
> **misfitpierce said:**
> Maybe try SMplayer can be found at [http://getdeb.net](http://getdeb.net) and it is an upgraded version of mplayer basically.

SMPlayer is only a new GUI for MPlayer, there is no added functionality (that will effect playback).

---

### Post by tomcheng76 on 2007-07-20
thanks m0rph , i dont need conversion though
rvm4000, i got w32codecs, but i want to stick with apt repositories version

now i want to use totem-xine as my main video player
can anyone tell me how to set DVDdrive to /media/iso (not /dev/dvd or else)

---

### Post by boumcke on 2007-07-20
Just a word about totem and gstreamer : I suppose you figured that out, but removing the totem-gstreamer package doesn't remove the entire gstreamer out of your system. It just affects totem's behaviour.

About the dvd path issue, you have to modify it by hand in the totem config file. It's not the most user-friendly solution, but I couldn't find it anywhere else. So check the config file, it should be ~/.gnome2/totem_config, there's a commented line somewhere saying media.dvd.device. Just uncomment it and set it to wherever you want it to point. I didn't test it though, but I suppose it should work.

---

### Post by tomcheng76 on 2007-07-20
editing ~/.gnome2/totem_config doesn't work
i think that it is because /media/iso is just a empty folder
while /dev/hdd acturally is a link to /dev/scd0 which is a block device

is that no method for a virtualdrive like /media/iso to treat as a DVD/CD....

---

### Post by phidia on 2007-07-20
Have you checked the FAQ at the [xine]("http://xinehq.de/index.php/faq") site?
There is a link to their mailing list (same link I provided).
Hope that helps.

---

### Post by tomcheng76 on 2007-07-21
found soln
you can open totem, than go to "movie/open location" and type
dvd://absolute/path/to/dvd.iso

or from terminal type
totem dvd://absolute/path/to/dvd.iso

dont even need to mount, thanks phidia

---

