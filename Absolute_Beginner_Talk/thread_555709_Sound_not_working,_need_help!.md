---
title: "Sound not working, need help!"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by andsmi on 2007-09-20
Hi! I've installed the alpha gutsy tribe 5. The sound is not working, and I've tried to download alsa and such. Nothing works. Now I got the problem that says "No volume control GStreamer plugins and/or devices found." What can I do to fix this? I have Intel HDA Soundcard. 

Thnx

---

### Post by wolfen69 on 2007-09-20
try this: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards)

---

### Post by maryjanua on 2007-09-20
i had a problem with intel hda sound and this fixed it in feisty
[http://ubuntuforums.org/showthread.php?p=3395708#post3395708](http://ubuntuforums.org/showthread.php?p=3395708#post3395708)
about page 11. it also gave me a no gstreamer and/or device found
:):)
mj

---

### Post by andsmi on 2007-09-20
thnx, I'll try it out now.

---

### Post by maryjanua on 2007-09-20
no prbs hope it helps lemme know if it does:)

---

### Post by andsmi on 2007-09-20
> **maryjanua said:**
> no prbs hope it helps lemme know if it does:)

uhm, nope. it did not help much:S did what It said. But still there is no sound detected. Ubuntu finds the sound card, but not in installed drivers. is there anyone else with the same problem? Im using a Zepto Znote 6224W and I've seen many other people having the same problems, but no one that I've seen has been able to fix them. After installing gutsy tribe the only problem that remained was that there was no sound. I turned everythin to its max using alsamixer in terminal, but it was still not working.
Is it possible that when gutsy tribe is launched(in october or so) that the soundcard Intel HDA is functional?
:-k

---

### Post by maryjanua on 2007-09-20
mine is functional now tho it took a lot to make it so and iv only bn usin linux for a week
sorry i cldnt help ya

---

### Post by andsmi on 2007-09-20
heh... Where did you get those realtek-linux-audiopack-4.06b.tar.bz2 and alsa-driver-rt20070820.tar.bz2 files from?

---

### Post by maryjanua on 2007-09-20
i went to realtek directly and downloaded it to my desktop same with the alsa driver

---

### Post by maryjanua on 2007-09-20
try this link thats how i got mine running
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
:)

---

### Post by andsmi on 2007-09-20
> **maryjanua said:**
> try this link thats how i got mine running
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
:)

I followed that instruction... then I got this problem.
"andy@andy-laptop:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
cp: cannot stat `/home/andy/downloads/alsa*': No such file or directory"
What do I have to do to get it to find that downloads/alsa?

---

### Post by mali2297 on 2007-09-20
> **andsmi said:**
> I followed that instruction... then I got this problem.
"andy@andy-laptop:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
cp: cannot stat `/home/andy/downloads/alsa*': No such file or directory"
What do I have to do to get it to find that downloads/alsa?

It is where you downloaded the three files. Run
```

locate alsa-driver-*

```
You probably have them on your desktop, then change "downloads" to "Desktop".

---

### Post by maryjanua on 2007-09-20
see mali im even tryin to help other folk :lolflag:
not as well as u tho!

---

### Post by andsmi on 2007-09-20
andy@andy-laptop:~$ sudo apt-get install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r

Thats another error I'm getting

I tried to ignore this error and build the alsa files
no errors happened, so I rebooted.
After reboot I wrote "cat /proc/asound/card0/codec#* | grep Codec"
then I got this: "cat: /proc/asound/card0/codec#*: No such file or directory"

---

### Post by maryjanua on 2007-09-20
have u downloaded the appropriate drivers to your desktop?
 have you done the alsa drivers yet?

---

### Post by Tavathlon on 2007-09-21
I managed to get sound working on my Zepto 6625WD (same soundcard as 6224, I think) by doing as the excellent guide in post #14 in this thread suggests: [http://ubuntuforums.org/showthread.php?t=545318&page=2](http://ubuntuforums.org/showthread.php?t=545318&page=2)

Hope it helps!

Oh, btw..  some time when I have time, I will post a thread somewhere about my experiences with Znote 6625WD so far.  =)

---

### Post by mali2297 on 2007-09-21
> **andsmi said:**
> andy@andy-laptop:~$ sudo apt-get install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r


If you want to fix this, try first to run *uname -r*. Then run
```

sudo apt-get install linux-headers-OUTPUT

```
where OUTPUT should be the output from the previous command (without any quotes).

It might be better to follow Tavathlon's tip however.

---

### Post by andsmi on 2007-09-21
When I click on that sound icon on the menubar, it says that I dont have the right GStream installed or that it just cannot detect my soundcard... where do I find the right GStream? oh, and "sudo apt-get install linux-headers-'uname -r' " followed by "sudo apt-get install linux-headers-OUTPUT" did not work either:S same error.

---

### Post by mali2297 on 2007-09-21
> **andsmi said:**
> When I click on that sound icon on the menubar, it says that I dont have the right GStream installed or that it just cannot detect my soundcard... where do I find the right GStream? oh, and "sudo apt-get install linux-headers-'uname -r' " followed by "sudo apt-get install linux-headers-OUTPUT" did not work either:S same error.

What is the output of *uname -r*?

You didn't type *sudo apt-get install linux-headers-OUTPUT* exactly, did you?
*OUTPUT* should be changed to the version number of your linux kernel.

---

### Post by andsmi on 2007-09-21
oh, lol! Is there any other way to find out what kernel I have beside rebooting? Like typing something into terminal?

---

### Post by mali2297 on 2007-09-21
> **andsmi said:**
> oh:P lol, is there any other way to find out what kernel I have beside rebooting? Like typing something into terminal?

Yes. :-)
```

uname -r

```

---

### Post by andsmi on 2007-09-21
nvm. Found it out. But that didn't do anything. It just said that I allready had the newest version of kernel 2.6.22-11.

Do anyone know how to reinstall the GStream for the sound controller?

---

### Post by mali2297 on 2007-09-21
> **andsmi said:**
> nvm. Found it out. But that didn't do anything. It just said that I allready had the newest version of kernel 2.6.22-11.

Do anyone know how to reinstall the GStream for the sound controller?

First of all, check if your sound card is working. Run this command in the terminal:
```

aplay -vv /usr/share/firefox/res/samples/test.wav

```
Do you hear anything?

If not, post the output of these commands (copy and paste):
```

uname -a
aplay -l
lspci | grep audio

```

---

### Post by andsmi on 2007-09-21
did that, but still no sound. I got that sound controll to work. Nothing is muted. I have build those Alsa drivers and such. What do I do now?

---

### Post by andsmi on 2007-09-21
aww. Now it sais that there was no sound card detected:cry:
andy@andy-laptop:~$ aplay -l
aplay: device_list:205: no soundcards found...
andy@andy-laptop:~$ uname -a
Linux andy-laptop 2.6.22-12-generic #1 SMP Thu Sep 20 18:51:18 GMT 2007 i686 GNU/Linux
andy@andy-laptop:~$ aplay -l
aplay: device_list:205: no soundcards found...
andy@andy-laptop:~$ lspci | grep audio

---

### Post by mali2297 on 2007-09-22
> **andsmi said:**
> aww. **Now** it sais that there was no sound card detected
Was the sound card detected **before**? (...or is it just that you haven't checked before?)

It seems that the presence of your card hasn't been detected. But just in case, run
```

lspci -v

```
and look through the output to see if there's something that resembles your sound card.



Provide some further information that might be useful:
[LIST=1]
[*]What is the **full** name of your sound card?
[*]Do you have Windows or any other OS installed on the same machine? If so, does sound work in that OS?
[*] Have you tried this? > If your soundcard is an onboard sound card, then it might be disabled in the system's BIOS. You will have to reboot and hit the key that lets you enter into the BIOS (usually Delete, F2, or F8 ).
[/LIST]

---

### Post by andsmi on 2007-09-22
This is the message I get of the soundcard in terminal using: "lspci -v"

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Inventec Corporation Unknown device 0040
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

It worked on my windows xp, but not on the ubuntu. It never has.

---

### Post by mali2297 on 2007-09-22
Alright, try again to follow this [guide]("https://help.ubuntu.com/community/HdaIntelSoundHowto") to compile the latest alsa drivers.

Start with 
```

sudo apt-get install linux-headers-`uname -r`

```
Note: Use **`** not **'**, my bad earlier. Just copy/paste the above into the terminal.

Then continue with the instructions in the guide until you receives errors, post the error messages in that case. Otherwise, check your sound after reboot.

---

### Post by andsmi on 2007-09-22
I didn't get any errors, but still no sound. The sound crontroll now works, but the sound still don't work.

---

### Post by Pumalite on 2007-09-22
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by mali2297 on 2007-09-22
> **andsmi said:**
> I didn't get any errors, but still no sound. The sound crontroll now works, but the sound still don't work.

Post output of
```

cat /proc/asound/card0/codec\#*
aplay -l

```

Also, when checking sound it might be best to use something like
```

aplay -vv /usr/share/firefox/res/samples/test.wav

```
so that it's not a codecs problem.

---

### Post by Pumalite on 2007-09-22
Read carefully the link I gave you. It has the answers to many things.

---

### Post by mali2297 on 2007-09-22
I think the [link]("http://ubuntuforums.org/showthread.php?t=545318&page=2") Tavathlon gave you holds the key, since it concerns the same computer model as yours. You need the 1.0.15rc2 version of the drivers instead of 1.0.14. Follow the instructions in [post 14]("http://ubuntuforums.org/showpost.php?p=3374613&postcount=14"). It's pretty much the same procedure, but also note that you should run
```

gksudo gedit /etc/modprobe.d/alsa-base

```
and add the line
```

options snd-hda-intel model=toshiba

```
at the end of the file.

If it still doesn' t work, try some of the other suggestions in the same thread like [post 16]("http://ubuntuforums.org/showpost.php?p=3392900&postcount=16").

---

### Post by andsmi on 2007-09-22
I have done what it said in post 14, then the soundcard was not detected. Then I did what it said in post 16 and it is now detected, but still no sound.

---

### Post by mali2297 on 2007-09-22
> **andsmi said:**
> I have done what it said in post 14, then the soundcard was not detected. Then I did what it said in post 16 and it is now detected, but still no sound.

What do you mean by *detected*? Post the output of
```

cat /proc/asound/card0/codec\#*
aplay -l

```

EDIT:
If *aplay -l* now shows your sound card, check that every sound channel is unmuted (or at least the main ones). You can do this in the terminal with
```
alsamixer
```

---

### Post by andsmi on 2007-09-22
andy@andy-laptop:~$ cat /proc/asound/card0/codec\#*
Codec: Realtek ALC268
Address: 0
Vendor Id: 0x10ec0268
Subsystem Id: 0x11700040
Revision Id: 0x100003
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Node 0x02 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x34 0x34]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x1d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x2d 0x2d]
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x05 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x100111: Stereo
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x100111: Stereo
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0a [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0c [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0d [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x0e [Audio Mixer] wcaps 0x20010a: Mono Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00]
  Connection: 1
     0x02
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x02 0x1d
Node 0x10 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80]
  Connection: 3
     0x03 0x1d 0x02
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x00:
Node 0x13 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x00:
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x081003c: IN OUT HP EAPD Detect
  Pin Default 0x99130110: [Fixed] Speaker at Int ATAPI
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x0f
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x081003c: IN OUT HP EAPD Detect
  Pin Default 0x0121401f: [Jack] HP Out at Ext Rear
    Conn = 1/8, Color = Green
  Pin-ctls: 0xc0: OUT HP
  Connection: 1
     0x10
Node 0x16 [Pin Complex] wcaps 0x40010c: Mono Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80]
  Pincap 0x0810: OUT
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x00:
  Connection: 1
     0x0e
Node 0x17 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083734: IN OUT Detect
  Pin Default 0x01a19820: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
  Pin-ctls: 0x24: IN
  Connection: 1
     0x02
Node 0x19 [Pin Complex] wcaps 0x40008b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals: 
  Pincap 0x083724: IN Detect
  Pin Default 0x99a3092e: [Fixed] Mic at Int ATAPI
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x24: IN
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x02, stepsize=0x4f, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x083734: IN OUT Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
  Connection: 1
     0x02
Node 0x1b [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
  Pin-ctls: 0x20: IN
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x0820: IN
  Pin Default 0x4005822d: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = Purple
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400380: Mono Digital
  Pincap 0x0810: OUT
  Pin Default 0x01451130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Black
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x23 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1b 0x1b]
  Connection: 7
     0x18 0x19 0x1a 0x1c 0x14 0x15* 0x12
Node 0x24 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x01 0x01]
  Connection: 7
     0x18 0x19 0x1a 0x1c 0x14* 0x15 0x13
Codec: Motorola Si3054
Address: 1
Vendor Id: 0x10573055
Subsystem Id: 0x10573055
Revision Id: 0x100700
Modem Function Group: 0x1
andy@andy-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thats the output.

---

### Post by mali2297 on 2007-09-23
Well, that's progress at least. It should be working now. :-?

You could try some of the advices from this site (the *Basic troubleshooting* part):
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

Also, as I said earlier, test sound with
```

aplay -vv somefile.wav

```
where *somefile.wav* can be any wav file that you have. For example, /usr/share/firefox/res/samples/test.wav.

Sorry, but I'm running out of ideas.

---

### Post by andsmi on 2007-09-23
those advices did not help, but in BIOS I cannot find any sound devices for for eksample disabling it or enabling it.

thanks for your help. Maybe this sound problem will be fixed when the Gutsy Tribe is released and im finnished using the beta?

---

