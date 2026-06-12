---
title: "ytmnd.com"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by paul6 on 2006-11-11
Does anyone know how to get ytmnd.com working with Firefox under Edgy? On most of them the sound doesn't even play... ](*,)

---

### Post by CSMatt on 2006-11-11
Type "about:plugins" into the Address bar of Firefox and find out what formats are already supported.  YTMNDs are created with either wave or MP3 sound formats.  In theory, you should be able to play wave files out of the box as there are no patents on uncompressed wave files.  MP3s, though, are patented formats and you will need to install MP3 support manually.

Synced YTMNDS also use Flash, so you will need either Adobe's Flash plugin or SWFdec to play them.

---

### Post by paul6 on 2006-11-11
I checked and according to Firefox I have "Totem Web Browser Plugin 2.16.2" to be able to play .wav and .mp3 files... but they still don't seem to work for some reason.

I tried downloading and installing the MediaPlayerConnectivity extension recommended in some threads, but ytmnd is stil not functioning. :(

---

### Post by Albi on 2006-11-11
You can install the firefox plugins with automatix...and can u play mp3 otherwise?

---

### Post by Albi on 2006-11-11
Hmm it turns out I had the same problem (haven't checked YTMND since my last reformat), and I fixed it by deleting all my totem plugins from firefox and installing the mplayer ones

---

### Post by Azakus on 2006-11-11
The best way to do this is delete the totem plugins for Firefox (they suck) and replace them with MPlayer's plugins. Here's the easy way
```
cd /usr/lib/firefox/plugins/
sudo rm libtotem*
sudo apt-get install mplayer mozilla-mplayer
```
Restart Firefox and try going to YTMND again.
This assumes you have the 32 bit version of Ubuntu, not the amd64 version.

---

### Post by Peepsalot on 2006-11-11
Well, it seems to mostly work for me.  Would be nice if wavs looped though.  Never could figure that out.

---

### Post by SZF2001 on 2006-11-23
Sorry, I know this thread may be long dead, but I didn't want to make a new one.

So can anyone tell me if there is a way to get the sound files to loop? Anything at all?

---

### Post by CSMatt on 2006-11-26
They should loop automatically.

---

### Post by Peepsalot on 2006-11-26
> **CSMatt said:**
> They should loop automatically.

They should but they don't.  Actually, I think maybe the ones with the flash preloader do, but any others won't

---

### Post by SZF2001 on 2006-11-26
I say there should be a wiki page specifically for ytmnd.com and other sites that use movie coded pages. But I don't know how to make a wiki...

---

### Post by strabes on 2006-11-29
I still cannot even get any sound to play at ytmnd.com. Websites like youtube.com work so it's not the alsa conflict thing. I have mplayer and mozilla-mplayer installed. about:plugins shows these two entries:

application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by xabbott on 2006-11-29
I use the following extention for ytmnd.

[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)

Just click the black arrow icon in the lower right hand corner.

---

