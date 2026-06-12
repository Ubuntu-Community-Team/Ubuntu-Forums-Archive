---
title: "Help- Can't play DVDs in Mplayer"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by marksy1984 on 2007-08-16
Hello. I've just installed Ubuntu 7.04 on my old laptop and I can't get it to play DVDs. I ran through the whole sticky on setting up multimedia, but MPlayers says that it cannot play DVD because it cannot load the HAL Daemon or something similar. 

Can anyone help?

---

### Post by philinux on 2007-08-16
Does Totem or vlc play your dvd's?

---

### Post by stchman on 2007-08-16
> **marksy1984 said:**
> Hello. I've just installed Ubuntu 7.04 on my old laptop and I can't get it to play DVDs. I ran through the whole sticky on setting up multimedia, but MPlayers says that it cannot play DVD because it cannot load the HAL Daemon or something similar. 

Can anyone help?

Sounds like you don't have all the codecs installed.  I will assume you are using Feisty.  Do the following:

```

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update

sudo apt-get install libdvdcss2


```

This should do it.

---

### Post by Orbital75 on 2007-08-16
Hi.... I am having the same issue. in Totem.

Totem will play unencrypted DVD's that I have made from Home Videos
but will not play a Purchased DVD movie.

I installed the Ugly plugin's from Add/Remove in Ubuntu 7.04
Do I need to do anything else to get encrypted Discs to play?

I keep getting an error I don't have the correct plugin to play DVD
when I put a purchased DVD in.

Thanks.....

---

### Post by stchman on 2007-08-16
> **Orbital75 said:**
> Hi.... I am having the same issue. in Totem.

Totem will play unencrypted DVD's that I have made from Home Videos
but will not play a Purchased DVD movie.

I installed the Ugly plugin's from Add/Remove in Ubuntu 7.04
Do I need to do anything else to get encrypted Discs to play?

I keep getting an error I don't have the correct plugin to play DVD
when I put a purchased DVD in.

Thanks.....

Do what I have listed above your post.

---

### Post by philinux on 2007-08-16
I know this sounds crazy but I had same problem. Found an obsure post somewhere anyway it suggested installing regionset from synaptic.

Now all I did was install it I didn't even run it and pop, dvd's now play.

After that I ran regionset just to see what gives and it said "no region code set" would I like to set one. So I said no.

But in windows this dvd player was set from manufacturer as region 2.

Anyway give it a go nowt to loose. :lolflag:

---

### Post by Orbital75 on 2007-08-16
Thanks......  New to Linux and didn't know what would happen
if I had the ugly package already installed.  I'll do as you stated
in the post above.....

Thanks

---

### Post by marksy1984 on 2007-08-16
I installed VLC and now it all works fine.

---

### Post by Hobo Joe on 2007-08-16
VLC will fix that.

---

### Post by Orbital75 on 2007-08-17
> **stchman said:**
> Do what I have listed above your post.

I did just as you said and everything installed correctly but still can't play
commercial DVD's

I also tried installing VLC player and that didn't help either.
Totam keeps telling me that I don't have the correct plug-ins
but didn't I just install them?

---

### Post by Arthur Archnix on 2007-08-17
I used to run all those installs, but now I just do
```
sudo apt-get install ubuntu-restricted-extras
```
It takes care of all that. It's easier than automatix, but uses apt, so you're all good! Check out the ubuntuguide for more info.

---

### Post by Orbital75 on 2007-08-17
> **Arthur Archnix said:**
> I used to run all those installs, but now I just do
```
sudo apt-get install ubuntu-restricted-extras
```
It takes care of all that. It's easier than automatix, but uses apt, so you're all good! Check out the ubuntu guide for more info.

I see that some of the packages state ( nonFree )
I don't know what that that means. Is the plugins trialware
or something. Thanks

---

### Post by Arthur Archnix on 2007-08-17
No, nothing like that. Others will correct me if I'm wrong, but it only means (AFAIK) that the programs /   drivers / codecs are not open source. So, for instance, it will install java as non-free, even though it is free to use. Just like on windows. Or the codecs to play dvd's. And so on. But it certainly does not mean "trial ware" I'm not even sure that such a thing exists on Linux. Does it?

---

### Post by Bachstelze on 2007-08-17
To play DVD movies, you need libdvdcss :

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by RomeReactor on 2007-08-17
Hi Orbital75. Did you install libdvdcss2 as stchman and HymnToLife suggested? Have you installed ububtu-restricted-extras as Arthur Archnix said? Did you try regionset as philinux said? if after all that you are still unable to play encrypted DVDs, try switching Totem to xine, and you might get the w32codecs while you're at it:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs w32codecs
```
There's no particular reason why this might help, but you'd be surprised the number of times this has worked.

---

### Post by Orbital75 on 2007-08-17
I've tryed everything that was listed above that had command line code
and nothing has worked so far.

Now I haven't tried **regionset** yet.
that's next on my list.

---

### Post by Orbital75 on 2007-08-17
Ok..... I install **regionset** but I can't find an icon in any of the pull downs
to run it.  Is this going to do anything to my DVD RW?

---

### Post by RomeReactor on 2007-08-17
You run it from the command line; it's been a while since I last used it, so I can't tell you how to use it. Read [philinux's post]("http://ubuntuforums.org/showpost.php?p=3200518&postcount=6") on the previous page. Also, read the manual:
```
man regionset
```

---

### Post by forevertheuni on 2007-08-21
I'm having this damned problem. I tried with vlc mplayer (xine systems like xine-ui kaffeine), totem(is it xine?). I have regionset, I've set it to europe(2) nothing. I tried the libdvdcss2 from mediubuntu the stuff from automatix I tried:
```

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs w32codecs 

```
tried with the sh /usr/share/doc/libdvdread3/install-css.sh 

Nothing in totem or kaffeine..sometimes the menus come but it doesn't pass from them.
Vlc and mplayer play some dvd's with squares and a not good picture

kaffeine says after the menu that it is an encrypted dvd and that it can't read it, like totem

In my StarWars epIII dvd 
 mplayer plays. but gives this in the output:
a52: CRC check failed!  1.772 ct:  0.972 243/244 12%  0%  4.9% 0 0 
a52: error at resampling
And the image is full of squares
However with other dvd that was around everything was ok for mplayer and vlc.
Is this other error?

---

### Post by sdowney717 on 2007-08-21
Rome Reactor, your post worked for me.

In this computer. there is a Hercules 64mb 4500 video card and the performance is poor in full screen.
So I suppose their is no way to help this.

---

### Post by RomeReactor on 2007-08-21
Hi sdowney. I could find very little information about your card; [this entry]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsKyro") in the Ubuntu Community documentation and [this thread]("http://ubuntuforums.org/showthread.php?t=363015") both suggest you're stuck with the Vesa driver for that card, since support for it went out with the 2.4 kernel.

---

