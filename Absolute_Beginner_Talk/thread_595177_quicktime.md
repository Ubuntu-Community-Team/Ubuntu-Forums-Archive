---
title: "quicktime"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by cg125 on 2007-10-28
hi
can someone explain how to watch quicktime movies in firefox from the apple movie trailers site.

---

### Post by linuxwizard on 2007-10-28
Install MPlayer with the Mozilla mplayer plugin

---

### Post by fetisha on 2008-03-18
I installed the MPlayer from the add/remove programs thing, but where is the firefox plugin?

---

### Post by fetisha on 2008-03-18
I take that back, I've found the firefox plugin and installed that as well, but it's still not working. Firefox still tells me I need a plugin to see the video.

---

### Post by Neo0351 on 2008-03-18
Try this thread
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by fetisha on 2008-03-19
Alright, so, I've found out that MPlayer does work on my 64-bit firefox, which I don't use because I can't get flash or Java to work on. How can I get it to work on my 32-bit firefox so I can have everything on one browser?

---

### Post by fetisha on 2008-03-20
*bump* any ideas?

---

### Post by aonegodman on 2008-03-22
Let me jump on this also and add that my mplayer seems to work fine in Firefox most of the time. I seem to have problems with playback/streming of Quicktime Video on some sites.

Firefox just sits there loading ((.)) and then after a few minutes just crashes and closes the browser.  :(

Now I don't understand since I seem to have no problems with YouTube videos which I believe are .flv(flash) mostly and I can play .mov too. There seems to be a difference in what I think are "true" quicktime MOV files and others.

Any suggestions or comments?  Thanks.  :)

---

### Post by Neo0351 on 2008-03-22
> **fetisha said:**
> Alright, so, I've found out that MPlayer does work on my 64-bit firefox, which I don't use because I can't get flash or Java to work on. How can I get it to work on my 32-bit firefox so I can have everything on one browser?

I'm running 64-bit swiftweasel which is based off Firefox and it and flash runs great.  You just need to install this script [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)
As for the java, I don't really use it so it's not much of an issue for me.

---

### Post by marco123 on 2008-03-22
I've always used the MediaPlayerConnectivity plugin for Firefox: - [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

I use vlc for video and xmms for audio and I've never had any problems.

Cheers, Marco.

---

### Post by frank002 on 2008-03-22
Get rid of all the other players. They conflict. I only have the MPlayer and now I can see the Quicktime movies, movies in Wimp.com and Youtibe movies. Also, you can try the Epiphany browser. I use it a lot instead of Firefox. Good luck.

---

### Post by aonegodman on 2008-03-24
Here's what worked for me on playing Quicktime videos -

Go to  EDIT > Preferences > Content > Under File Types click on Manage >

scroll down to "QT  QT Video"  Change "Open with Quicktime plug-in 7.2.0" to

"Open with Movie Player" and Close.

There is a conflict here for some reason in Firefox, but I can now play Quicktime videos in my browser with no problems. Might want to give it a try.

By the way, I found this solution on a web site where Windows users were running Firefox and had same issues. This tells me this is not an O/S problem but a Firefox issue.

Hope this helps someone.  :)

---

