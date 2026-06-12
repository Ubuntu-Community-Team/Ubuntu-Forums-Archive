---
title: "Music Sequencing and Soundfont Woes..."
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by Hygelac on 2006-01-15
Hi.  I'm not sure if this belongs here; but I'm fairly new to Linux and also don't know where else it would go.  So:

I've been trying to get a music sequencer running.  I decided to try Rosegarden, but found out that I'd have to get MIDI running first.  This has turned out to be a problem because I don't think my soundcard supports soundfonts (they all seem to be for SoundBlaster or some other thing I don't have.  KInfo, under sound>audio_devices says "0: ATI IXP AC97 (DUPLEX)" which as far as I can tell is not a SoundBlaster or any other compatible card name I have encountered.  For reference, my computer is an HP zv6000 notebook running 64-bit Kubuntu Breezy).  However, I can playback MIDI files with Timidity ("$ timidity -ia /filepath"), which I think just converts to .wav to playback files.  The consequence of this partial-Timidity is that I can boot Rosegarden and run it, except that I cannot play back any sounds in it (because I'm missing soundfonts I suspect).  It would not even load initially, but reciting the following incantation seems to fix that (setting up a soundserver or somesuch):
	sudo modprobe snd-seq-device
	sudo modprobe snd-seq-midi
	sudo modprobe snd-seq-oss
	sudo modprobe snd-seq-midi-event
	sudo modprobe snd-seq
	sudo timidity -iA -B2,8 -Os1l -s 44100

I also tried Bristol (because what I really want to do here is simulate vintage synths ;)) but it has a problem with my MIDI too, which I assume is due to the lack of soundfonts.

If someone miraculously knew how to resolve the soundfont issue that would be cool, but (realistically) what I'm looking for now is a (free & Linux) non-MIDI music sequencer or somesuch.  If anyone knows of any I would be very interested to know of it/them too.  I am looking around myself but any help would be greatly appreciated.

---

