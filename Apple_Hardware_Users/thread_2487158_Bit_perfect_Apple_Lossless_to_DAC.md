---
title: "Bit perfect Apple Lossless to DAC"
date: 2023-05-25
forum: Apple Hardware Users
---

### Post by afdoughty on 2023-05-25
Hi all,
I've revived my 2014 Mac Mini with Ubuntu and it runs really well. I have both Spotify steaming music and my 500 CDs ripped to the SSD as Apple Lossless audio files.

I use the optical out headphone jack, Toslink, to my external headphone DAC and headphones (Chord and Sennheiser).

Playback worked but not for the Apple Lossless files.

However, the output is not bit perfect as the software is allowed to volume control, either in Spotify or the system tray. My DAC has its own volume control so it needs bit perfect output to get faithful audiophile quality. I can tell with classical music that the software is degrading the quality.

So, unfortunately I started Googling and messing with stuff to overcome the inability to decode Apple Lossless (gstreamer missing plugin) and for using ALSA not PulseAudio.

I have installed various things via terminal and now have no sound from Spotify or my media player, guayadeque.

How do I fix these two issues?

1) install codecs for Apple Lossless

2) get bit perfect sound to the optical out for my external DAC

Thanks!

---

### Post by TheFu on 2023-05-25
Not what you want to hear, but FLAC should have been used instead. That's the industry standard and it is well supported by lots of devices.  I don't use Spotify, but FLAC is well supported for lots and lots of players  - both hardware and software.  Apple makes proprietary software. Best to avoid that when running a F/LOSS OS.

BTW, I rip to FLAC, but re-encode that into 192 kbps vorbis.  My ears can't tell the difference.  I used to use 160kbps mp3, but I can definitely hear that difference.  For mp3, I need 256kbps encodings before I can't tell the difference.

Lastly, PulseAudio is a layer over ALSA, so if you use pulse, you are still using ALSA.  For some reason, I thought audiophiles had switched to using Jack as their audio server.

OT - I ripped my 2K music CD collection in the mid-1990s to 160 Kbps mp3 files.  Decided that FLAC was the needed solution a few years ago and re-ripped all the CDs again, this time to FLAC. 
Before I switched, I tested the players I use - mpd, mpv, vlc, plex, jellyfin, and a few others to be certain I wasn't preventing any playback that I wanted. In short, I started with the goal and worked backwards to create a process that fit those needs.
[LIST]
[*]I never wanted to rip the CDs again.  FLAC solves that.
[*]I wanted the highest quality that my ears and listening environment for the lowest file sizes with support for my normal playback software and devices.
[/LIST]
Here's an album:
```
$ sudo du -sh *
213M    flac
53M     vorbis-q6
```
So a q6 transcode to vorbis is 53MB while the source FLAC is 213MB.  Basically, I can carry around 4x the number of albums on my phone if I choose HQ vorbis encodes and I'm unlikely to hear any real difference.  Q6 results in 192Kbps encoded vorbis/ogg files.  Across my multiple thousands of albums, this approximate savings is pretty accurate.
Here's another album - classical music - it is more complex.
```
$ sudo du -sh *
198M    flac
79M     mp3-160
80M     vorbis-q6
```
So, I get higher quality audio with vorbis for nearly zero difference in size compared to mp3 at 160Kbps.

[https://www.whathifi.com/advice/high-resolution-audio-everything-you-need-to-know](https://www.whathifi.com/advice/high-resolution-audio-everything-you-need-to-know) says, 
> AIFF (hi-res): Apple's alternative to WAV, with better metadata support. It is lossless and uncompressed (so big file sizes), but **not massively popular**.

FLAC (hi-res): This lossless compression format supports hi-res sample rates, takes up about half the space of WAV, and stores metadata. It's royalty-free and widely supported (though not by Apple) and is **considered the preferred format for downloading and storing hi-res albums**.

ALAC (hi-res): Apple's own lossless compression format also does hi-res, stores metadata and takes up half the space of WAV. **An iTunes- and iOS-friendly alternative to FLAC**.

[https://en.wikipedia.org/wiki/List_of_hardware_and_software_that_supports_FLAC](https://en.wikipedia.org/wiki/List_of_hardware_and_software_that_supports_FLAC)
[https://en.wikipedia.org/wiki/Vorbis](https://en.wikipedia.org/wiki/Vorbis)

Vorbis is the best, non-proprietary, music compressor, providing the highest quality, for the lowest bitrate.  There are a number of listening tests and articles where audiophiles try to tell the difference.  I recall reading that in a group of 10 professional listeners, 50% were unable to tell the difference using their music and their hardware/headphones for the tests. That's when I knew vorbis was the answer for my needs.  Being patent free also makes it a better choice, at least for my needs.  YMMV.

**We don't have **any** Apple hardware in the house. **

BTW, AAC at higher bitrates compares favorably to vorbis, but not all devices support AAC.  If you are an Apple household, this may not matter. If you continue to migrate into F/LOSS more, consider switching to ogg containers for vorbis audio files and FLAC is probably the best answer for your ears.

---

### Post by TheFu on 2023-10-31
> **stevenworkman said:**
> [COLOR=#374151][FONT=Söhne]Apple Lossless Audio Codec (ALAC) is a lossless audio compression format developed by Apple. When you play an Apple Lossless audio file on a compatible device, the goal is to ensure that the digital audio data reaches the Digital-to-Analog Converter (DAC) in its original, unaltered form. A DAC is a device that converts digital audio signals into analog signals that can be amplified and played through speakers or headphones.[/FONT][/COLOR]

I think the point is that ALAC doesn't play on non-Apple systems.  This is an Ubuntu forum after all, and lots of people switch to Ubuntu from proprietary OSes, so ALAC doesn't work.  FLAC is lossless and well-supported on all devices and by most media player servers.

BTW, converting from ALAC to FLAC can be automated. [https://askubuntu.com/questions/123405/how-to-convert-alac-to-flac](https://askubuntu.com/questions/123405/how-to-convert-alac-to-flac) answers that using the extremely powerful ffmpeg.  Basically, here's the script:
```
for f in *.m4a; do ffmpeg -i "$f" "${f%.m4a}.flac"; done
```
that will convert all m4a ---> flac.  Be certain the m4a are actually ALAC, not some Apple compressed format like AAC. Converting a compressed audio file to a lossless one just makes it huge and cannot make for a higher quality sound.

---

### Post by coffeecat on 2023-10-31
@TheFu, "stevenworkman's" 1st time post was unattributed ChatGPT output, and hence spam by our definition. I've banned the user and removed the post, but left the quote in situ in your post, as the spammer hadn't (yet) added their link garbage, and your exchange will be useful to someone.

For the record: unattributed ChatGPT posts are getting more common as the [s]imbeciles[/s] spammers refine their techniques for trying to slip in under the radar. A too-well-written-to-be-true text, often marginally or totally off-topic, and often with a non-standard font, is the hallmark of possible ChatGPT spam.

---

