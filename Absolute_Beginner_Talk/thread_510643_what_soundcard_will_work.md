---
title: "what soundcard will work?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by the.phantom on 2007-07-26
i tried a post a few days ago
i just need a list of what cards alsa in 7.04 has??  (**32 bit NOT 64)**

i found a list from ms for vista

i need a sound card that will work with **vista64** basic
and Ubuntu!!!!

i have a strange sound card and the easy way is to replace it !

so if you dual boot with vista 64
what do you have for a sound card?

i still use the cheap default speakers and no recording !

i now i don't want a creative X anything
i just want a card that Ubuntu will know about and work!!!!

i just got a real cheap system and have played with the live cd for 7.04
and know i have to update my video card drivers but they are in the list in restricted so should be no problem

so all that is left is the sound card


HELP PLEASE

---

### Post by kyphi on 2007-07-26
The Creative Soundblaster Live works well in Ubuntu straight out of the box.  There is no reason why it would not work in Vista.

---

### Post by DBStevens on 2007-07-26
Alsa Wiki Sound card information

[http://bugtrack.alsa-project.org/main/index.php/Matrix:Main](http://bugtrack.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by the.phantom on 2007-07-26
the alsa shows the list right
BUT that is NOT the list that is in Ubuntu !!!!!!!!

several of them have to be re compiled and installed

and that is something i do not want to do as i have been reading up on that for a few days !

and the sb live and vista has problems !

a work around for 32 bit is to use XP drivers if you have them

so still hoping for help

does anyone have a list of what s in Ubuntu on alsa drivers?????

OR does any dual booters that can tell me what they use and if troubles ????

no guesses please
i already have a sound card that won't work in Ubuntu and i dont need a spare non working sound card ;-D

mitch

---

### Post by the.phantom on 2007-07-26
for anyone else with this problem

here is a list of what 7.04 shows for ALSA
usr.share.doc.alisabase.driver

Advanced Linux Sound Architecture  -  Supported SoundCards
	 ==========================================================

ID: SoundCard chipset/type
SC: SoundCard name
IF: Supported interfaces (MIXER,PCM,SYNTH,SYNTH_MIDI,SEQ,OPL,MIDI,EMUL,HWDEP)
MA: Maintainer
CO: Coder

This file is maintained by Jaroslav Kysela <perex@suse.cz>.
Note: OPL -> Raw (native) OPL
Note: MIDI -> external MIDI port
Note: EMUL -> MIDI emulation
Note: SYNTH -> yeah, well ?
Note: SYNTH_MIDI -> internal synth that handles MIDI data
Note: SEQ -> kernel client for ALSA sequencer
Note: HWDEP -> various hardware-dependent interfaces/devices
=====

ID: AMD InterWave
SC: Gravis UltraSound Plug & Play
SC: Dynasonic 3-D
SC: STB Sound Rage 32
SC: UltraSound 32-Pro (STB)
SC: MED3210
IF: MIXER,PCM,MIDI,SYNTH
MA: Jaroslav Kysela <perex@suse.cz>

ID: Gravis UltraSound MAX
IF: MIXER,PCM,MIDI,SYNTH
MA: Jaroslav Kysela <perex@suse.cz>

ID: Gravis UltraSound Extreme
SC: Synergy ViperMax
IF: MIXER,PCM,MIDI,SYNTH
MA: Jaroslav Kysela <perex@suse.cz>

ID: Gravis UltraSound Classic/ACE
IF: MIXER,PCM,SYNTH
MA: Jaroslav Kysela <perex@suse.cz>

ID: ESS AudioDrive ESx688
IF: MIXER,PCM,MIDI(1688)
MA: Jaroslav Kysela <perex@suse.cz>

ID: SoundBlaster 1.0/2.0/Pro
IF: MIXER (Pro only),PCM,MIDI
CO: Jaroslav Kysela <perex@suse.cz>
MA: Chris Butler <chrisb@sandy.force9.co.uk>

ID: SoundBlaster 16/AWE
IF: MIXER,PCM,MIDI
MA: Jaroslav Kysela <perex@suse.cz>

ID: Yamaha OPL3-SA2/SA3
IF: MIXER,PCM,MIDI
MA: Jaroslav Kysela <perex@suse.cz>

ID: S3 SonicVibes PCI
SC: Schubert 32 PCI (PINE)
IF: MIXER,PCM,MIDI
MA: Jaroslav Kysela <perex@suse.cz>

ID: Ensoniq AudioPCI (ES1370,ES1371)
SC: SoundBlaster PCI 64
SC: SoundBlaster PCI 128
IF: MIXER,PCM,MIDI
MA: Jaroslav Kysela <perex@suse.cz>

ID: Cirrus Logic / Crystal Semiconductors CS4232/CS4232A
IF: MIXER,PCM,MIDI
MA: Jaroslav Kysela <perex@suse.cz>

ID: Cirrus Logic / Crystal Semiconductors CS4235/CS4236/CS4236B/CS4237B/CS4238B/CS4239
SC: Turtle Beach Malibu
IF: MIXER,PCM,MIDI
MA: Jaroslav Kysela <perex@suse.cz>

ID: Cirrus Logic / Crystal Semiconductors CS4281
IF: MIXER,PCM,MIDI
MA: Jaroslav Kysela <perex@suse.cz>

ID: Cirrus Logic / Crystal Semiconductors CS4610/CS4612/CS4614/CS4615/CS4622/CS4624/CS4280
IF: MIXER,PCM,MIDI
MA: Jaroslav Kysela <perex@suse.cz>

ID: ESS Solo-1 ES1938
IF: MIXER,PCM
MA: Jaromir Koutek <miri@punknet.cz>

ID: ESS ES18XX
IF: MIXER,PCM,MIDI
MA: Abramo Bagnara <abramo@alsa-project.org>

ID: OPTi 82C9xx
SC: Audio 16 Pro  EPC-SOUN9301      (82C930 based)
SC: ExpertColor  MED-3931 v2.0      (82C931 based)
SC: ExpertMedia Sound 16  MED-1600  (82C928 based - AD1848)
SC: Mozart  S601206-G               (OTI601 based - CS4231)
SC: Sound Player S-928              (82C928 based - AD1848)
IF: MIXER,PCM,OPL,MIDI
MA: Massimo Piccioni <dafastidio@libero.it>

ID: Trident 4DWave DX/NX
SC: Best Union  Miss Melody 4DWave PCI
SC: HIS  4DWave PCI
SC: Warpspeed  ONSpeed 4DWave PCI
SC: AzTech  PCI 64-Q3D
SC: Addonics  SV 750
SC: CHIC  True Sound 4Dwave
SC: Shark  Predator4D-PCI
SC: Jaton  SonicWave 4D
SC: Hoontech SoundTrack Digital 4DWave NX
IF: MIXER,PCM,MIDI
MA: Jaroslav Kysela <perex@suse.cz>

ID: ForteMedia FM801
SC: DT-0398
IF: MIXER,PCM,MIDI
MA: [email]perex@suse.cz[/email]

ID: SGI Indy (HAL2)
IF: PCM
MA: Ulf Carlsson <ulfc@sgi.com>

ID: Turtle Beach WaveFront
SC: Tropez Plus (Tropez+)
SC: Tropez
SC: Maui (models with CS4232; others use OPTi 16 which is not handled)
IF: MIXER,PCM,MIDI,OPL,SYNTH_MIDI,HWDEP
CO: [email]pbd@op.net[/email]
MA: [email]pbd@op.net[/email]

ID: C-Media CMI8330
IF: MIXER,PCM
MA: George Talusan <gstalusan@uwaterloo.ca>

ID: C-Media CMI8338/8738
IF: MIXER,PCM,MIDI
MA: Takashi Iwai <tiwai@suse.de>

ID: Avance Logic ALS100/ALS120
IF: MIXER,PCM,MIDI
MA: Massimo Piccioni <dafastidio@libero.it>

ID: Diamond Technologies DT-019X
IF: MIXER,PCM,MIDI
MA: Massimo Piccioni <dafastidio@libero.it>

ID: Aztech Sound Galaxy
IF: MIXER,PCM,MIDI
MA: Christopher Butler <chrisb@sandy.force9.co.uk>

ID: Aztech AZF3328/PCI168
IF: MIXER,PCM,MIDI,OPL,SYNTH
MA: Andreas Mohr <hw7oshyuv3001@sneakemail.com>

ID: MOTU MidiTimePiece AV multiport MIDI interface
IF: MIDI
MA: Michael T. Mayers <tweakoz@pacbell.net>

ID: EMU10K1
SC: Sound Blaster Live!
SC: Sound Blaster PCI 512
SC: E-mu APS
IF: MIXER,PCM,MIDI,SYNTH_MIDI
MA: Jaroslav Kysela <perex@suse.cz>

ID: RME Digi9652 (Hammerfall, Hammerfall light)
IF: PCM
MA: Paul Barton-Davis <pbd@op.net>

ID: Intel i810/i820/i830/i840/MX440
IF: MIXER,PCM,MIDI
MA: Jaroslav Kysela <perex@suse.cz>

ID: ESS Maestro 1/2/2E
IF: MIXER,PCM
MA: Matze Braun <MatzeBraun@gmx.de>

ID: VIA 82C686A (South Bridge)
IF: MIXER,PCM,MIDI
MA: Jaroslav Kysela <perex@suse.cz>

---

### Post by DBStevens on 2007-07-26
Install the kernel sources and take a look.

Which is the only true way and even that tells you what was intended and not what actually works.

---

### Post by kyphi on 2007-07-27
You already have a list of the supported soundcards for Ubuntu.

Now you need the list of supported sound cards for Vista 64.

Then compare.

---

### Post by the.phantom on 2007-07-27
yep, and the windows site is IE only ;-( but did manage to get part of a list before i had troubles, so there is hope

what i didn't want to do was have to go through the long list for compiling the kernel and such

---

### Post by DBStevens on 2007-07-27
Change your browser agent to say it is IE ;-)  I belive there is a Firefox extension for that and that Konq and Opera both allow it from their configuration menus.

---

### Post by kyphi on 2007-07-27
[http://www.tomshardware.com/forum/232602-44-list-vista-supported-hardware-software](http://www.tomshardware.com/forum/232602-44-list-vista-supported-hardware-software)

---

