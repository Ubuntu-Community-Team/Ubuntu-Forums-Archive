---
title: "Audio Streams do not ...."
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-11-01
With Feisty this was not an issue, it worked.  A fresh install of Gutsy and no go.  Perhaps I have forgotten to install something but I cannot think what....

All other sounds and streaming audio (say Shoutcast channels through Streamtuner) works well.

These two streams not work .....  

[http://www.rthk.org.hk/live5.ram](http://www.rthk.org.hk/live5.ram)
[http://www.bbc.co.uk/chinese/meta/tx/nb/letterbox_au_nb.ram](http://www.bbc.co.uk/chinese/meta/tx/nb/letterbox_au_nb.ram)

What happens is that Firefox opens the mplayer plug-in and attempts to connect to the server.  The browser then either hangs or the station identifier clip is played after several minutes and then no audio stream.

I have tried VLC but an error message appears which says it cannot play or the player does nothing.

Any suggestions how to get these streams to play?

---

### Post by haldean on 2007-11-01
.ram files are normally opened in Real Player... have you tried using RP to play it?

---

### Post by philinux on 2007-11-01
Go to synaptic and install realplay it has the helix dna plugin to play ram files

---

### Post by expatCM on 2007-11-01
reading round it seems that people do not exactly appreciate RealPlayer.

Apparently based on Helix Player so I thought .. install Helix and all will be fine.  Wrong.  In common with many other media packages that claim to support .ram files it does not ....

So I went to install RealPlayer which apparently is no longer in the repositories.  Installed from the .bin which is also not an obvious find if you go to the real.com site ....   Windows .exe is the default download and Linux is not given as a choice.

I have now installed RealPlayer and there is some improvement in that I can play some streams but for some reason Firefox will now download the .ram as an initial file before RealPlayer appears.  There may also be some network issues since a number of error messages also appear explaining that  the source was not available....

---

### Post by haldean on 2007-11-02
Yeah - the .ram file isn't actually music data; it's information on where RealPlayer can find the stream of music. It's kind of like a torrent - it doesn't hold any information itself. Firefox is always going to have to download it, because it doesn't know how to handle it itself. You can set it to always open with RealPlayer, though, so you don't have to click "Okay" every time.

---

