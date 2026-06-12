---
title: "i would like to have a media player that supports mp3's"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by TBone13 on 2006-07-18
considering i am a massive noob to linux (i've been actively working with it for about 5 days now) i have managed to do a few pretty decent tasks by doing google searches. i have installed unreal tournament 2004(even though i tried updating it with a patch and now it won't work right) i have made directories with the command prompt and have transferred a lot of files from my windows partition to my ubuntu partition(by using cd's i burned) and most of the files i wanted to use on ubuntu were mp3 files. i have even installed wine and winetools and still can't get anything to help me out. i have searched for mp3 players for ubuntu with google and i have attempted to use XMMS(which keeps giving me odd error messages) and i tried to install Xine, but it didn't work. if anyone could tell me some good media players to download for ubuntu that support mp3's, or tell me how to get mp3 codecs or something, it would be truly appreciated. :-k

---

### Post by lerrup on 2006-07-18
Try one of the suggestions [here.]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by crystal on 2006-07-18
Read the wiki on [RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats).

---

### Post by Erunno on 2006-07-18
Hi there !

Considering that I'm also rather new to Linux you should take everything I write with a salt of grain. ;) Here we go, there are 3 possible ways to get support for all kind of funky codecs that Ubundu doesn't support out of the box.

1. Use EasyUbuntu. It can add a lot of functionality to Ubuntu with a couple of mouse clicks. Get it [here]("http://easyubuntu.freecontrib.org/") and just follow the instructions. Totem should be able to handle your desired formats then.

2. Install VNC. It's a media player which can play a wide range of formats (audio and video) without the need to install additional codecs.

3. (the slightly less easy way) Start the Synaptic package manager and install the following packages:

gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg
gstreamer0.10-gl
gstreamer0.10-pitfdll
libquicktime0

Download the win32 codecs froh [here]("http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb") and use Synaptic to install it.

Mind you that EasyUbuntu probably does the same things as outlined in the third option so I'd rather use EasyUbuntu.

Hope that helps.

Cheers,
Erunno :)

---

### Post by eeried on 2006-07-18
> 2. Install VNC. It's a media player which can play a wide range of formats (audio and video) without the need to install additional codecs.

You mean **VLC (Videolan)** which plays audio and video files. It plays mp3 files natively and the sound is much better than Xmms but Xmms is very easy to use.

Please everyone do read the excellent Wiki. You don't need wine at all to play mp3!

Mp3 being a proprietary format which you're supposed to pay royalties for when you use it Ubuntu can't deliver mp3 codecs or whatever makes it possible for the players present in the Ubuntu Linux distribution to play mp3 files.

Feel free to download, or listen to, **Ogg Vorbis** files -- the sound is much better and this format is free! -- you can find perfectly legal OGG files on the Jamendo music website (a portal in fact) for instance.

In a word, look out for free formats !

---

### Post by TBone13 on 2006-07-18
i used easyubuntu to download a lot of stuff and totem will now play my mp3's, but no sound comes out of my speakers... i don't know what to do from here, so more help would be nice ](*,)

---

### Post by GuitarHero on 2006-07-18
Sounds like you need drivers.  Do you have a sound card?  Go into device manager(look in the system tab, preferences i think).  Look to see if a sound device is recognized, if not you need drivers.  They may be available on your motherboard/sound card maker's web site.

---

### Post by taurus on 2006-07-18
Is your soundcard working?  Do you hear the music when you log into Gnome?  Try opening a terminal (Applications -> Accessories -> Terminal) and type

```

sudo alsamixer

```
Now, use the up arrow key to increase the volume of all of them...

---

### Post by TBone13 on 2006-07-18
yes i hear sound when i get into gnome, and i can hear sounds from all sorts of different websites. when i went into the alsamixer i turned everything i could up to 100, but there were 3 things that i couldn't do anything with.


Mic Boost -> MM

IEC958 -> MM

External -> 00


the external i couldn't turn up, but that's because i'm not using any external amplifiers.


... i guess i'll just have to be patient and do a lot of google searches or something.

---

### Post by s_h_a_d_o_w_s on 2006-07-18
To get the codecs simply install automatix. It will do it for you really simply. Here the howto: [http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

---

