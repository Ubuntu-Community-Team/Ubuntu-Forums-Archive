---
title: "Newbie with Totem DVD Codecs Problems"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by TrikkeDaddy on 2007-01-18
Hi there,
I am new to Ubuntu Edgy.  I have been jumping from Xandros, then to Fedora, and heard Ubuntu was better for my needs.

One common problem I have been struggling with all of the distros I have tried is getting stuff like mp3's, MIDI's, MOV's, and DVD's to work.  I was told to install the codecs. Well, Easy Ubuntu 3.1 alpha 1 was good installing MP3's and flash, but I still need to install the codecs for DVD and MOV to be recognized.  I think I noticed that there were some broken links for updates while I was using Easy Ubuntu, so maybe that was the problem.

How can I fix this?  Be easy on me, I am not quite techy savy just yet and I am still confused on a lot of words they use in Linux.

---

### Post by zerhacke on 2007-01-18
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by JamieC on 2007-01-18
Install the packages one by one (using Easyubuntu) to determine which one(s) are missing. Then we can tell you how yo go about acquiring the missing one(s) which you require.

---

### Post by TwistesdTexan on 2007-01-18
The best way I have found for installing the codecs is with Automatics. It includes the audio and video codecs. [http://getautomatix.com/](http://getautomatix.com/) Good Luck!:-D

---

### Post by zerhacke on 2007-01-18
There is no codec to a DVD player in Ubuntu or Linux in general.  What you need is libdvdcss, which is in the link I provided.

---

### Post by TrikkeDaddy on 2007-01-18
DVD works now,used [http://www.getautomatix.com/](http://www.getautomatix.com/) and installed the program, and ran it. One thing, the video slows down sometiimes, but I think that is memory.

---

### Post by redDEADresolve on 2007-01-18
Ubuntu 6.06 and 6.10

Install the following packages to play most proprietary formats using the Totem and Rhythmbox applications, both of which are included in Ubuntu by default. Since the version of Totem that comes with Ubuntu does not yet play DVDs, the list below also includes packages for the GXine and Ogle players, which do.

    *

      Ensure the relevant repositories are enabled. Click System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and then click Add. Check the Community maintained (Universe)' and Non-free (Multiverse) boxes. When you close the window, click Reload.
    *

      Install the packages. While you could install packages individually using Synaptic, here is one case where any Ubuntu user can save a lot of time by using the command line. Click Application -> Accessories -> Terminal and paste the following command:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

    *

      In order to play most commercial DVDs (which are encrypted with the CSS), you'll need libdvdcss2, which is not available in the Ubuntu repositories. See Playing DVDs.
    *

      Users of x86 systems may also install some additional Windows codecs that are not available in the Ubuntu repositories. See Windows Media and RealPlayer files.

---

### Post by RomeReactor on 2007-01-18
TrikkeDaddy, maybe your dvd drive doesn't have dma enabled and that's why viewing dvd's is slow. In a teminal, write:

```
sudo hdparm -d1 /dev/dvd
```

Press enter. Then:

```
sudo hdparm -k1 /dev/dvd
```

Enter again.

---

### Post by TrikkeDaddy on 2007-01-19
Thanks guys, all DVD's are playing great now.  However, still can't play MOV files, especially when I go to a site and want to play a mov movie.

---

### Post by shareMenaPeace on 2007-01-19
> **TrikkeDaddy said:**
> Thanks guys, all DVD's are playing great now.  However, still can't play MOV files, especially when I go to a site and want to play a mov movie.
Hmm i can play mov files and 3gp i think with totem and realplayer MMPlayzer and FF Plugin and Realplayer from automatix install under multimedia.


But not sure what exactly is the codec here?

---

### Post by RomeReactor on 2007-01-19
Which browser plugin are you using?

---

### Post by TrikkeDaddy on 2007-01-19
Everything plays, but only can download Mov files, then load them in MoviePlayer, can't stream. Plugin? In FireFox, MediaPlayer  Connectivity 0.8.3 in the addons.

---

### Post by RomeReactor on 2007-01-19
Try uninstalling Media Player connectivity, leaving just the Mplayer plugin, then restart Firefox and try to watch that video again.

---

