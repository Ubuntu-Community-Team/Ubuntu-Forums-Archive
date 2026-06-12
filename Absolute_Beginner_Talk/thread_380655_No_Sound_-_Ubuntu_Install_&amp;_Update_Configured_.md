---
title: "No Sound - Ubuntu Install &amp; Update Configured Live! Card as Live! Platinum"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Dinadan on 2007-03-09
I installed Ubuntu 6.10 today as dual boot with Win98 on an old Gateway SB computer (upgraded).  I use this computer for backup and to feed music and video to a TV in my master bedroom.  After of a couple of false starts I got the added  nVidia geForce 6200LE working, including TV out.  Unfortunately I have not been able to get any sound even after trying to fix all of the obvious causes outlined in the docs and forums.

I am not sure how to do the neat "code" boxes that I see in some posts so I am just going to copy _excerpts_ from some of my attempts to get information through "terminal".
[COLOR="SeaGreen"]
**Actual Sound Card Hardware Info:**

~$ lspci -v
[COLOR="SeaGreen"]00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4760 SBLive![/COLOR]
        Flags: bus master, medium devsel, latency 64, IRQ 9
           I/O ports at e480 [size=32]
        Capabilities: <access denied>

00:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
        Subsystem: Creative Labs Gameport Joystick[/COLOR]
        Flags: bus master, medium devsel, latency 64
        I/O ports at ec00 [size=8]
        Capabilities: <access denied>

~$ lspci -nv
00:09.0 0401: 1102:0002 (rev 08)
        Subsystem: 1102:8040
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at e480 [size=32]
        Capabilities: <access denied>

00:09.1 0980: 1102:7002 (rev 08)
        Subsystem: 1102:0020
        Flags: bus master, medium devsel, latency 64
        I/O ports at ec00 [size=8]
        Capabilities: <access denied>

~$ tail -2 /proc/asound/oss/sndstat
Mixers:
0: SigmaTel STAC9721,23

**Installed Driver and Additional Info:**

~$ asoundconf list
Names of available sound cards:
Live

~$ modinfo snd-emu10k1
filename:       /lib/modules/2.6.17-11-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
author:         Jaroslav Kysela <perex@suse.cz>
description:    EMU10K1
license:        GPL
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        snd-pcm,snd-util-mem,snd-page-alloc,snd,snd-rawmidi,snd-timer,snd-hwdep,snd-ac97-codec,snd-seq-device
alias:          pci:v00001102d00000002sv*sd*bc*sc*i*
alias:          pci:v00001102d00000004sv*sd*bc*sc*i*
alias:          pci:v00001102d00000008sv*sd*bc*sc*i*
srcversion:     E3914E3E9325B9B7A3D4D82
parm:           subsystem:Force card subsystem model. (array of uint)
parm:           enable_ir:Enable IR. (array of bool)
parm:           max_buffer_size:Maximum sample buffer size in MB. (array of int)
parm:           max_synth_voices:Maximum number of voices for WaveTable. (array of int)
parm:           seq_ports:Allocated sequencer ports for internal synthesizer. (array of int)
parm:           extout:Available external outputs for FX8010. Zero=default. (array of int)
parm:           extin:Available external inputs for FX8010. Zero=default. (array of int)
parm:           enable:Enable the EMU10K1 soundcard. (array of bool)
parm:           id:ID string for the EMU10K1 soundcard. (array of charp)
parm:           index:Index value for the EMU10K1 soundcard. (array of int)

[COLOR="Red"]**Sound Card as Actually Installed by Ubuntu:**[/COLOR]

~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: Live [[COLOR="Red"]SBLive! Platinum [CT4760P][/COLOR]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
            [31 more lines incrementing by 1]
card 0: [COLOR="Red"]Live [SBLive! Platinum [CT4760P]][/COLOR], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
            [7 more lines incrementing by 1]
card 0: [COLOR="Red"]Live [SBLive! Platinum [CT4760P]][/COLOR], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**My Problem:**

I think that I need to get my actual Sound Blaster Live! card configured in place of the Sound Blaster Live! Platinum currently configured.  I am not sure how to do this.  
  1.  it seems from my reading that it takes more than changes to configuration text files!  of   my reading indicates that modprobe could be used, but I am unsure of the parameters needed. 
   2.  Do I need to somehow un-configure the Platinum card currently configured.  How?

Regards and thanks in advance for any help.

---

### Post by Dinadan on 2007-03-11
As I have had no response to this posting, I thought I would reply to myself with some additional info.  As an aside, I have asked the administrator for information needed to shift this thread to a more appropriate subsection (possibly the  multi media subsection).
 
I am a true Ubuntu/Linux Newbie (I started a Dual Boot  Personal Project with 3 computers all running some variant of Windows).  I therefore did my first problem post in the Ubuntu Forums Newbie Section.

The following is an abbreviated summary of the research sources  I used after encountering  a sound problem with Ubuntu installed as  Dual Boot with Windows 98SE on and old Gateway SB system with a Sound Blaster Live! Card (that works fine when I am in Windows).

[SIZE="3"]**Summary Information Sources Reviewed**[/SIZE]
**A whole lot of Google Searches**
    * A lot of Linux forums with not much useful information

**[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)**
    * Main Ubuntu Sound Page - used as starter to get to the following resources

[B][https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)
[/B]    * Resource used to get the system information in my original post - very helpful for that task
    * Not much help figuring out how to actually use the information gathered - seems to assume an implied level of Linux knowledge and experience that a newbie like me does not have
    * This is not a criticism of the author - I think this was the best resource to find out how to gather information
    * Unfortunately, after that, I found it very difficult to figure out how to use my gathered information to adapt the steps that followed to my situation.
     * After additional searches I am still not sure how to use it.
     *  My next step was to sign up to the Ubuntu Forums and post my problems in the Newbie section - No response to date

[B][http://www.alsa-project.org/](http://www.alsa-project.org/)
[/B]    * Main ALSA web site - good general information on Sound in Linux (no specific help for my problem)
[B]
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)[/B]
    * Used to verify the ALSA driver (emu10k1) required for my sound card (Sound Blaster Live!)

[SIZE="2"]**My Success To Date Resolving Problem**[/SIZE]
**None**
    * No response to date from Ubuntu Newbie Forum Posting
    * Perhaps I have Posted in the wrong forum
    *The forum rules discourage cross posting - can I move my one posting thread to a more appropriate sub-forum
    * Although I did a lot of research and reading before (and after) installing Ubuntu, I am really a Newbie to Linux
    *I am willing to contribute if I see that I am participating in a useful forum - at this point I am unsure
    * Yes, Its only been a couple of days, but that is a long time for someone trying to complete what should be a relatively simple task nowadays (getting sound out of a computer)****

---

### Post by frequenicity on 2007-03-11
I'm not sure if this helps, but I also have  a SoundBlaster card that was not working. The issue was resolved by going into my BIOS settings and disabling the on board/integrated sound (I am assuming that your sound card is a PCI card). Give that a try and see what happens.

---

### Post by Dinadan on 2007-03-11
When I booted into Ubuntu today I had a pleasant surprise - a beep came out of my speakers when the login screen appeared. I also received the Ubuntu start sounds and once in was able to play music.

I suspect that one of  the "fix the obvious" actions that I did when following instructions from the various docs and forums cleared the problem without me realizing it.  A first I was testing by getting VLC to play a music file.  Unfortunately, later on, I was using the Test Buttons in Preferences/Sound. I assumed this would return a sound but all it did was return a text window. It still does, even thought I have working sound.  The way I now interpret this is that a specific test button (e.g movie/music playback) returns a failure text message if any one of the other setup selections is not working/configured properly.  

To "frequenicity" - Thank you for your response.  My install is on an older computer with no on board sound capability. Therefore no BIOS sound adjustments are needed or possible.

Finally, the mismatch between asoundconf list and PCI identification of the card still exits.  It apparently does not matter since both Sound Blaster Live!, and Live! Platinum, use the same emu10k1 driver.   

Regards

---

### Post by Dinadan on 2007-03-16
**Sound Problem Came Back!**
Ubuntu 6.10 with Sound Blaster Live PCI Card

**No Sound Once Again - What Happened!**

I Did some updates and installs and suddenly I again have no sound (sound still works fine when I boot into Windows).  The key additions to my Ubuntu install (using Easy Ubuntu) included :

    * All available A/V codec packages
    * Flash Plug-in
    * Java Plug-in 

When I booted up the next day there were no system sounds and attempts to play Internet radio through Rythmbox resulted in silence (although I could see the artist/song information displayed).

Did something I installed break the sound again - how and why?

**Troubleshooting Actions Taken with no Success**

Verified that all playback options are unmuted

    * Opened Volume Control from the sound icon - ok, all unmuted
    * Opened Alsamixer from Terminal - same, all unmuted

**Implemented the solution given in the Edgy Unofficial Guide**

    * [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_sound_to_work_properly_in_GNOME)
    * Rebooted system and still no sound


Tomorrow I will repeat all of the steps given in my first post, but in the meantime I would appreciate any other insights or suggestions.

---

