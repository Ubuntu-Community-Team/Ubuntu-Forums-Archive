---
title: "No Sound on My Laptop"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by TemLeaf on 2007-10-14
Hello, sorry I have made a similar post under hardware/laptop support, im having such a hard time getting sound to work on my notebook

I have just loaded Xubuntu Fiesty Fawn onto my old Compaq Presario 1925.  Things are going well with it, I just can't seem to get my sound working no matter how many different guides I read through.

Here's some of the troubles I've come across:
- When I put an audio cd in, it doesnt automount and i get an error when I try to mount it.
- When I try to play an audio cd in Rhytmbox, Banshee, etc, the program just crashes with no response whatsoever.
- When I try to open up Gxine, i get the splash screen and then its just crashes.
- When I open up Mixer Settings it only lists "default" under Device and has no other options
- I type alsamixer in the terminal and get this:
alsamixer: funtion snd_ctl_open failed for default: No such device

when i type in lspci -vvnn i get this:

01:00.1 Multimedia audio controller [0401]:  Neomagic Corporation NM2200 [MagicMedia 256AV Audio] [10c8:8005] (rev 20)
Subsystem: Compaq Computer Corporation Unknown device [0ell:b0d1]
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B+
Status: Cap+ 66MHz- UDF- Fast B2b+ ParErr- DEVSEL=medium >TAbort- <MAbort- >SERR- <PERR-
Interrupt: pin B routed to IRQ 10
Region 0: Memory at f4800000 (32 bit, prefetchable) [size=4M]
Region 0: Memory at f4200000 (32 bit, non-prefetchable) [size=1M]
Capabilities: <access denied>

I installed VLC and was able to play some .mov files, however without sound

I would appreciate greatly anyone that could help me get this baby firing with sound!  I REALLY dont want to cross back to the dark side of Windows!! :grin:

cheers

---

### Post by runemaste644 on 2007-10-14
First make sure PCM isn't muted
If that doesn't work, set everything to full blast i guess...

---

### Post by TemLeaf on 2007-10-16
Ok I think I'm getting somewhere at a snail's pace...I was able (I think) to get ALSA driver/lib/utils installed, but that still hasnt gotten me anywhere.  When I type in *alsamixer *i get this:

alsamixer: function snd_ctl_open failed for default: No such device

But, I am able to enter root and run *alsaconf* and it says that installation was successful and have fun.......I wish!

here's some more commands that might provide more info:

*aplay -l*
aplay: device_list:204: no soundcards found...

*modprobe snd-*
snd-ac97-codec          snd-nm256              snd-pcm-oss      snd-seq-device          snd-timer
snd-bt-sco                  snd-page-alloc        snd-rtctimer       snd-seq-midi-event
snd-mixer-oss             snd-pcm                  snd-seq             snd-seq-oss

could this have something to do with a clash between OSS and ALSA?  i think i read somewhere that you should get rid of all OSS....how would i do that?

Somebody please help me out!  I need this thing running by the end of the month because Ill be sending my desktop away when i move, and will be relying on this little guy, would be nice to be able to listen to some music on it.

thanks for any help

---

### Post by xcafeus on 2007-10-16
i dont know if this is any help but I also did not have sound and it was because my user did not have sound rights. I run "sudo gnome-control-center", then went to users and checked the properties for my username. After reboot everything was fine.

---

### Post by TemLeaf on 2007-10-16
I typed your code *gnome-control-center* but it said *command not found*...i think i might have tried something similar thru the gui, i went to system>users and made sure the audio and cd rights were checked...but still no sound...i wonder why xubuntu detects my sound card but alsa cant..i followed the installation guide for Neomagic 256AV from the alsa website, i get all the way through, but get stuck at where the author says to run *alsamixer*, it just wont do it. thanks guys for your help, are there any super "pro's" who can walk me through getting it setup?  there must be other people out there who have installed the Neomagic 256AV soundcard?  any guidance would be helpful

---

### Post by greg.harvey on 2008-02-04
I have slammed in to the same issue. From my reading around the subject the simple answer seems to be "this sound card does not work with Linux..."

Unless you know different?

:(

---

