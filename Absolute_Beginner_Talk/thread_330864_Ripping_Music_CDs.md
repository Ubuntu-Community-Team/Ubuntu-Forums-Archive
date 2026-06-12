---
title: "Ripping Music CDs"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by DeathOnJuice on 2007-01-03
Hey, everyone. I recently purchased a Sansa e200 line MP3 player, and this is my first. In the past I have only used CD players and Pandora, so I've never really worried about ripping music. Now that I need to move my collection to the new player, I have a couple of questions.

1. What is the best Linux app to rip CDs? The best Windows one? Is there any extra setup I need to do in these apps to rip properly?

2. Which format should I rip to? Tell me the best few in general, and the best one that the Sansa supports (MP3, WMA, and PlaysForSure DRM which won't apply to CDs)

Also, how would I burn audio CDs in Linux?

Finally, what would happen if I ripped to one format and converted it to another?

---

### Post by Bachstelze on 2007-01-03
1. I'm not pretending to use the best but in Linux I use abcde (command line tool) and in Windows Audiograbber.

2. If your player supports it, Vorbis (generally in .ogg files) is the best but I guess mp3 is good enough.

3. To burn just anything in Linux, one must-have : k3b :)

---

### Post by Dmole on 2007-01-03
Windows:
  rip:
    EAC
  encode:
    FLAC or LAME
Linux:
  use WINE to run windows apps
  or if you are making mp3s and are not a KRAZY audiophile then just use anything that works Automatix2 is quick ans simple


:)

---

### Post by 23meg on 2007-01-03
> 1. What is the best Linux app to rip CDs?I can't know what's best for you, but Sound Juicer comes preinstalled with Ubuntu and is pretty good.
> Also, how would I burn audio CDs in Linux?Serpentine, which lets you burn audio CDs, comes preinstalled as well.

---

### Post by DeathOnJuice on 2007-01-03
OK, I'm not an audiophile at all; I just want it to be easy and sound good.

When I look at SoundJuicer, I don't see an option to encode as MP3. Are there other options or apps?

---

### Post by AndyCooll on 2007-01-03
Found this in another thread (did a "soundjuicer mp3" search):

> As long as you can hear MP3s (meaning you have the mp3 codec working) all you need to do is;

In Sound Juicer, go to "Edit" --> "Preferences", then down by "Output Format" click on "Edit Profiles". Add a "New" profile with the following;

Profile Name: MP3
Profile Description: MPEG Layer 3
GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=192 ! id3mux
File Extension: mp3

and tick the active box. You should now be able to rip in MP3.

:cool:

---

### Post by MetalMusicAddict on 2007-01-03
[ HOWTO: Create Mp3s with Grip and understand what you are doing]("http://www.ubuntuforums.org/showthread.php?t=183125hp?t=25151")

---

### Post by igknighted on 2007-01-03
As far as burning k3b is the best burning software I have found.

---

### Post by DeathOnJuice on 2007-01-03
[COLOR="Red"][SIZE="4"]THIS IS THE LAST AND PROBABLY MOST IMPORTANT POST; AFTER THIS, I'LL BE READY[/SIZE][/COLOR]

Alright, thanks for all the help so far. I've chosen to use Grip for ripping with this option under "encoder command line":

-V 3 --vbr-new %w %m

What kind of quality/file size will this produce compared to ripping with iTunes or WMP? Will VBR be compatible with the Sansa e260? I'm still not sure if I should just reboot into Windows when I need to rip. If this is just as good, I'll keep it.

Last question: how should I configure ID3 tags in Grip? Should it be v1 or v2?

Thanks so much!

---

### Post by DeathOnJuice on 2007-01-03
Anyone?

---

### Post by userundefine on 2007-01-04
VBR should play just fine since it is still an mp3.  Use ID3v2.  I'm not sure on comparable quality since I've never ripped with WMA/iTunes.

---

### Post by tagra123 on 2007-01-04
> **DeathOnJuice said:**
> Anyone?

grip is my favorite too

I used the default setting except for switching to lame so it would encode to mp3/

I've got good sounding mp3 cds.  We have a mp3 cdplayer and a ipod look-a-like and they work great on both..


To get rid of the drm -- if you have access to windows and media player just burn to a cd from the media player.  DRM gone  Copy to your mp3 player, linux computer --etc Walmart has a decent place on their cite explaing it./

---

### Post by DeathOnJuice on 2007-01-04
OK, I've decided on using Grip with the default LAME settings, since the files are smaller than the -V3 --vbr-new settings. Does this sound good?

Thanks again!

---

### Post by MetalMusicAddict on 2007-01-04
> **DeathOnJuice said:**
> OK, I've decided on using Grip with the default LAME settings, since the files are smaller than the -V3 --vbr-new settings. Does this sound good?

Thanks again!

Its a quality thing. I *think* the default settings make 128kbps mp3s. The **-V3 --vbr-new** makes a VBR mp3 that averages 192-224 or so. They will be bigger but sound better. I would make one of each and compare. Try something with cymbal crashes.

---

### Post by DeathOnJuice on 2007-01-04
OK, I guess I'll do that. I know that your method produces higher quality, but I couldn't notice much of a difference. Still, in case I become more of an audiophile or a better sound card/my Sansa brings out the higher quality, I'll go with the VBR option.

Thanks! I'm ready to rip some CDs!

---

### Post by Dmole on 2007-01-04
1) Don't bother with windows and use whatever audio file format.

if you are compressing with a lossful format then quality is not of concern to you.

lossless format:
[http://en.wikipedia.org/wiki/Lossless_data_compression#Audio_compression](http://en.wikipedia.org/wiki/Lossless_data_compression#Audio_compression)

lossful format:
[http://en.wikipedia.org/wiki/Lossy_data_compression#Music_compression](http://en.wikipedia.org/wiki/Lossy_data_compression#Music_compression)


2) VBR is often not compatible but give it a try as it will reduce file size.

3) ID3 version normally makes no difference you can stuff more stuff into v2 lyrics ect

4) tags in Grip? no idea never used sorry. try the Grip help?

---

### Post by MetalMusicAddict on 2007-01-04
> **Dmole said:**
> 1)2) VBR is often not compatible but give it a try as it will reduce file size.

Since when? 5 years ago? :)

Give the link I posted above a try. ;)

---

### Post by Dmole on 2007-01-05
> **MetalMusicAddict said:**
> Since when? 5 years ago? :)

Give the link I posted above a try. ;)

i assume you are referencing compatibility not smaller file size?

your right i should have said "sometimes" not "often".
I use a Sharp 903 and it gets all quiet like when i feed it a VBR.

---

### Post by radiant chains on 2007-01-05
If you want VBR that is more comparable in size to a 128kbps mp3, I recommend trying *-V 5 --vbr-new*.

---

### Post by Disa on 2007-01-11
> **DeathOnJuice said:**
> Last question: how should I configure ID3 tags in Grip? Should it be v1 or v2?

Thanks so much!
I'd say go for v1.  It doesn't have a lot of the extra fluff that v2 has (more fields to add data in, and higher character limits for fields), but is far more cross-compatible between a variety of mp3-playing devices.

---

### Post by blackened on 2007-01-12
ID3v2 offers more fields of entry, but really it's a matter of taste.  Either way if you choose one, then stick with it. It's a ginormous (no that's not a real word) undertaking to go back and manually edit 2 or 3 thousand incorrectly tagged files, especially if you're nit-picky about following a tagging standard.

If there's a single Windows app that I miss it would be EAC with a lame backend. I just haven't found anything comparable for mp3s that can match it in quality. Maybe it's a personal shortcoming.

---

