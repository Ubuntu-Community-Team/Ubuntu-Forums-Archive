---
title: "Rhythmbox and mp3 player"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by jms392 on 2006-08-13
I have finally worked out how to get Rhythmbox to recognise my Zen Neeon mp3 player.  I was stoked, until I failed to work out how I could add music to the Zen using Rhythmbox (I'm not entirely sure that this is even possible).  It's great being able to get music from the Zen to my PC, but it would be even better if I could go the other way and transfer tracks from the PC to the player.  If anybody has any ideas, could you please let me know.  Thanks in advance.

PS For those who aren't sure, if Rhythmbox doesn't automatically detect your audio device, add an empty text file titled ".is_audio_player" (without the quotes) to the device.  I'm pretty sure this works with any device that is mass storage capable.

---

### Post by damianubuntu on 2006-08-13
With my mp3 player, when I plug it into the USB, ubuntu automounts the player as a disk.  After that its just a question of copy and paste from your music folder to the player 'disk' folder.
Can you see your player in Nautilus, Thunar or whatever you use as a file manager?

---

### Post by jms392 on 2006-08-13
Yeah, nautilus picks it up automatically, and copying and pasting works fine.  Just thought it'd be nice if I could sync my music using Rhythmbox.  Just used to Windows I guess!  I figured if Rhythmbox could pick it up, then maybe  there was a feature that would allow syncronization.

---

### Post by damianubuntu on 2006-08-13
There maybe....I don't know Rhythmbox really, just use Xfmedia myself, its so lightweight...good for my old machines!

---

### Post by jetrottie on 2006-08-13
I have a sony Psyc MP3 player. With Sony being so proprietary, will it work without the windows based sound forge loading software. I havent tried it yet?

---

### Post by damianubuntu on 2006-08-13
Jus have to plug it in and find out;-)

In my (limited) experience there are a number of things that have proprietary windows software, but that this is more to do with tools for manipulating the device, rather than inherent communicability.  I *think* that maybe most mp3 players work on a standard format and are just SCSI drives...

So suck it and see!, plug it into the usb and see whether you can find it automounted, if not go from there following threads on searching for hardware (e.g. try typing in terminal:  sudo lshw  and see if you can find your player under the USB section)

---

### Post by jms392 on 2006-08-13
If iPods work with Linux, I'm pretty sure Sony products will too.

---

### Post by jISh on 2006-08-13
Some mp3 players may also have different firmware types (although this isn't your case, I'd just like to point it out).

For example, my iRiver IFP originally came with firmware that required iRiver's transfer software. However, there is an an alternate firmware type on their website entitled UMS which allows the player to be treated as a hard disk.

---

### Post by doclivingston on 2006-08-13
> **jms392 said:**
> I have finally worked out how to get Rhythmbox to recognise my Zen Neeon mp3 player.  I was stoked, until I failed to work out how I could add music to the Zen using Rhythmbox (I'm not entirely sure that this is even possible).  It's great being able to get music from the Zen to my PC, but it would be even better if I could go the other way and transfer tracks from the PC to the player.  If anybody has any ideas, could you please let me know.  Thanks in advance.

Rhythmbox currently doesn't support copying to mp3 players, but it's being actively worked on ([http://bugzilla.gnome.org/show_bug.cgi?id=76528)](http://bugzilla.gnome.org/show_bug.cgi?id=76528)).

I'm not sure what the best thing for copying music to a Zen currently is, just using Nautilus may work.


> PS For those who aren't sure, if Rhythmbox doesn't automatically detect your audio device, add an empty text file titled ".is_audio_player" (without the quotes) to the device.  I'm pretty sure this works with any device that is mass storage capable.

Rhythmbox will automatically detect any device which HAL reports as having the "portable_audio_player" capability, but unfortunately it doesn't know about a lot of them. This workaround should work for anything which is mass storage (i.e. shows up in nautilus).

---

### Post by msak007 on 2006-08-13
The best app to use for Zens (and Creative devices in general) is Gnomad. My Samsung MP3 player automatically mounted as a USB drive and I was able to use Konqueror to transfer files, but my sister's Zen MicroPhoto requires Gnomad for transfers.

---

### Post by jms392 on 2006-08-14
> **msak007 said:**
> The best app to use for Zens (and Creative devices in general) is Gnomad. My Samsung MP3 player automatically mounted as a USB drive and I was able to use Konqueror to transfer files, but my sister's Zen MicroPhoto requires Gnomad for transfers.

Thanks, I tried using Gnomad2 but got an error reading: "No jukeboxes found on USB bus".  I also tried running Gnomad2 as root, but still no luck. Perhaps the Zen Neeon is unsupported?

---

### Post by msak007 on 2006-08-14
It's probably an MTP MP3 player (correct me if I'm wrong). Follow the link in my sig for the how-to on getting MTP Creative MP3 players working with Gnomad.

---

