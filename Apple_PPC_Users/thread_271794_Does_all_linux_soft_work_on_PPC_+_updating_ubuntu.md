---
title: "Does all linux soft work on PPC + updating ubuntu ?"
date: 2006-10-05
forum: Apple PPC Users
---

### Post by Powerwing on 2006-10-05
As I've said in my other post about PFD, I'm new to Linux. But I'd like to know whether most available software works also on PPC, like Mame, VLC video player, NVC web design, open office...
Also, what if Ubuntu 7 is released in a couple of months time. Can I just update the existing version 6 or will I have to wipe my hd and reinstall ubuntu from scratch ?

---

### Post by siman on 2006-10-05
"most available software" runs under PPC as well, without any problems. I have ubuntu running on a powerbook G5 with great success.

openoffice, NVU and such shouldn't give you much problem - when it comes to multimedia, there is a bit more hassle to install the codecs..but there are great howtos in the forums (also checkout the wiki page called "essential codecs" or smth like that).

when you have ubuntu installed on PPC apt-get will give you a message "this programm is not supported on PPC" - so you won't end up installing progs, that don't work.

---

### Post by Powerwing on 2006-10-05
Thx !
I'm concerned about not being able to display Quicktime (more specifically QT7) files. Every quicktime movie on Apple's website requires QT7 and I just hope VLC supports that (H264). But I guess that's just up to the qt plugin in firefox... I guess I'll find out. I have OS X.3 on my powermac but I'll play around with Ubuntu on my old pismo until I'm comfortable with it before I install it on my main machine. By the way, what about my question about updating ?  And where did you get that G5 Powerbook ? :-k

---

### Post by stmiller on 2006-10-05
VLC plays anything. And mplayer plays current quicktime files. It's all there to install if you want that software. Ubuntu has more PPC software available than any other distro. It's very good for PPC.

There is no Skype for PPC Linux. They do not release the source, so no Skype. And of course no wine, or vmware either.

PS: I'd like a powerbook G5 also. :)

---

### Post by Powerwing on 2006-10-06
One more question : will the quicktime 7 files play in the browser (is there a qt7 firefox plugin for linux and is there a way to save QT files on the HD as I do now in  OS X with QT Pro ?
And about that G5 powerbook : siman must have the only G5 powerbook in existence :^o   Seriously, though, it would have been great to actually have a Powerbook G5, but if the current MBPro's already run quite hot, I'd hate to think what kind of heat a G5 PB would give off :wink:

---

### Post by stmiller on 2006-10-06
> Also, what if Ubuntu 7 is released in a couple of months time. Can I just update the existing version 6 or will I have to wipe my hd and reinstall ubuntu from scratch ?

Ubuntu has a 6 month release policy. 6.10 is expected at the end of October. So it will be awhile before the next update.

I tried playing quicktime trailers from apple.com to test for you. Using mplayer, and the mozilla-mplayer-plugin, the trailers will play, but the video is not 100% clear. I think the mplayer qt component on x86 is better (as it uses the windows codecs) than on ppc Linux, unfortunately.

With the mplayer-plugin, I can right click and 'copy url,' then paste that into a new browser window. When that starts playing again, I can right click and choose 'save movie as...." and save it to the hard drive.

So yes, you can save movies. Playback of video is not 100%. I think it COULD be an issue with xv/X11, and not the codec.

PS: There is no flash for PPC Linux. A couple of opensource flash projects have releases, and they playback basic webpage flash. But no google video/you tube, etc. on ppc linux. This is the one bad (or good?) thing.

---

### Post by Powerwing on 2006-10-06
Thx for the info

---

