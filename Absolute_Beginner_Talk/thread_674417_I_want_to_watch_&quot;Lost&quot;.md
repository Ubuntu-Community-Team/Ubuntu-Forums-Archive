---
title: "I want to watch &quot;Lost&quot;"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by bdemers on 2008-01-21
I have Ubuntu 7.10.  Totem is installed using the gstreamer variant.  When I place a commercially available dvd in the dvd rom player, Totem returns a message indicating that there isn't a codec installed which reads the format on the disc.  Drive is being accessed as determined by lite and directory. Totem auto launches .  I really don't have an issue with installing codecs, I'd love to do just that!  Thing is I don't know which ones to put in.  The blurbage makes me think to use gst-plugins-good and gst-plugins-base.   Looks like I want to avoid -ugly..  Is this correct?, do I need additional plugins or anything else?  I assume the codecs are available on the Totem site? apt-get install didn't locate anything, so can't be on the harddrive.

---

### Post by PurposeOfReason on 2008-01-21
You can either install VLC (a different media player that won't have problems) or the gstreamer ugle and bad packages. Also might need to open up the add and remove packages, choose enable all, and look for gstreamer and install the three or so it gives you.

---

### Post by Arthur Archnix on 2008-01-21
You can't watch DVD's without adding in support for DVD playback. VLC has it built into the program, which is why it works. For everything else, see here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Kilz on 2008-01-21
[This page may be of some help.]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by bdemers on 2008-01-24
I thank all who helped me out.  It works out that I had to deal with the scrambling first.  Then I ended up with artifacts that required some messing with.

I found a distribution called LinuxMint which brings in  the appropriate codecs during install.  LinuxMint is Ubuntu based.  It would be nice if Ubuntu had (or, maybe it already does) a media package which would allow for a single source for the bazillion different ways that audio and video can be presented on a computer.  

I would like to be of some assistance in such an endeavor.  Someone point me in the proper direction, not sure how to proceed.

---

### Post by LowSky on 2008-01-24
arthur gave you the right infor

in terminal  type or copy paste this

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

then this
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

 then

```
sudo apt-get install libdvdcss2
```

then

```
sudo apt-get install w32codecs

```



then everything should work

---

### Post by billgoldberg on 2008-01-24
Ubuntu can't preinstall the dvd codecs without paying fees to whoever owns the dvd format.

Linux mint might be illegal in most countries.

I wouldn't switch to mint just for dvd playback.

It's (dvd playback) easily installed by adding the medibuntu package to your repositories and downloading the drivers. Those steps are already listed here. Or use vlc media player (available in add/remove and synaptic).

There is also an program you can download that will install dvd-playback, flash, java, ... [Click here]("http://ubuntuforums.org/showthread.php?t=613462") for that program.

---

### Post by bdemers on 2008-01-24
Thanks, once again.  I reread the link that Arthur provided, and I admit that I didn't pay close enough attention on first pass.

By the way, am I missing something on acknowledging the help that is provided to me?  I notice a tally by peoples name.  Is that obtained from these replies, or how?

---

### Post by mdpalow on 2008-01-24
See link in my signature for help now or in the future if/when you need to install the proper files again...

---

### Post by stchman on 2008-01-24
> **bdemers said:**
> I have Ubuntu 7.10.  Totem is installed using the gstreamer variant.  When I place a commercially available dvd in the dvd rom player, Totem returns a message indicating that there isn't a codec installed which reads the format on the disc.  Drive is being accessed as determined by lite and directory. Totem auto launches .  I really don't have an issue with installing codecs, I'd love to do just that!  Thing is I don't know which ones to put in.  The blurbage makes me think to use gst-plugins-good and gst-plugins-base.   Looks like I want to avoid -ugly..  Is this correct?, do I need additional plugins or anything else?  I assume the codecs are available on the Totem site? apt-get install didn't locate anything, so can't be on the harddrive.

I have a tutorial that will get that DVD player working just fine.

Install the proprietary codecs.
[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

Install the css software.
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

This will work.

---

### Post by bdemers on 2008-01-24
Ya know, at some point in my life I need to learn to accept things without forcing the issue.

I dropped LinuxMint and reinstalled Ubuntu 7.10 to follow the suggestions that you all gave me.  Keep in mind the LinuxMint is Ubuntu 6.06 based (I think its 6.06) and out of the box played my dvd without any issue.  
This would imply that hardware was not the cause here.  I mean, look at it, it plays great.

So I put in Ubuntu 7.10, update all 165 files and the immediately proceed to follow instructions as outlined.  It played, but terrible.  Noisy display, unwatchable.  So I dropped resolution, aha, noise, though some still there, is abating. 

Ran to the junk box, pulled out a riva tnt2 card and stuck that in. Bingo, it all fell into place.  Display has crisper text, brighter screen and no artifacts on video. 

About the only thing that I can come up with is a driver change on the original video card from 6.06 (Mint) to 7.10.  Old driver worked better.  I'm not going to go any further, just take it as a gift.

Thanks for everyone's help.  If someone could tell me how to increment your thanks counter I'd be pleased to do that.

---

### Post by stchman on 2008-01-24
> **bdemers said:**
> Ya know, at some point in my life I need to learn to accept things without forcing the issue.

I dropped LinuxMint and reinstalled Ubuntu 7.10 to follow the suggestions that you all gave me.  Keep in mind the LinuxMint is Ubuntu 6.06 based (I think its 6.06) and out of the box played my dvd without any issue.  
This would imply that hardware was not the cause here.  I mean, look at it, it plays great.

So I put in Ubuntu 7.10, update all 165 files and the immediately proceed to follow instructions as outlined.  It played, but terrible.  Noisy display, unwatchable.  So I dropped resolution, aha, noise, though some still there, is abating. 

Ran to the junk box, pulled out a riva tnt2 card and stuck that in. Bingo, it all fell into place.  Display has crisper text, brighter screen and no artifacts on video. 

About the only thing that I can come up with is a driver change on the original video card from 6.06 (Mint) to 7.10.  Old driver worked better.  I'm not going to go any further, just take it as a gift.

Thanks for everyone's help.  If someone could tell me how to increment your thanks counter I'd be pleased to do that.

What kind of video card did you have originally?  Nvidia cards are most compatible with Linux.

To give thanks, click the stars on each post in the lower right corner.

---

### Post by bdemers on 2008-01-24
The original video is a Savage.  Built into the mama board.  Bios doesn't let me shut it down, but Ubuntu picked up on the new card right away.  Couldn't id though, thought that was interesting.  I also noticed that with both video devices , the display "Test" button returned a "fail", this being true for both devices at a number of resolutions.

---

### Post by suttles95 on 2008-05-10
I'm trying to download an episode through abc.com, but I get the following message:

Oops
Our new video player is only available for:
Windows 2000/XP/Vista - Internet Explorer, Firefox
Mac - Firefox, Safari
To watch, please download the appropriate browser.

Is there anything I can download to solve this or allow me to watch the episode?

---

### Post by PurposeOfReason on 2008-05-10
> **suttles95 said:**
> I'm trying to download an episode through abc.com, but I get the following message:

Oops
Our new video player is only available for:
Windows 2000/XP/Vista - Internet Explorer, Firefox
Mac - Firefox, Safari
To watch, please download the appropriate browser.

Is there anything I can download to solve this or allow me to watch the episode?
Can you give me a direct link?

---

### Post by suttles95 on 2008-05-10
Absolutely...

[http://dynamic.abc.go.com/streaming/popup?aff=null](http://dynamic.abc.go.com/streaming/popup?aff=null)

---

### Post by abuakel on 2008-05-10
> **LowSky said:**
> arthur gave you the right infor

in terminal  type or copy paste this

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

then this
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

 then

```
sudo apt-get install libdvdcss2
```

then

```
sudo apt-get install w32codecs

```



then everything should work


Will this work with Hardy or do I need other commands?

---

