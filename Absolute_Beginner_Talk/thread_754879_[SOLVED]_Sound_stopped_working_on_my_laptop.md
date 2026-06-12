---
title: "[SOLVED] Sound stopped working on my laptop"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-04-14
I lost the sound on my Gateway 9300 laptop a few months ago running Feisty, and by checking the routine things I'm familiar with such as the ALSA mixer controls to ensure nothing is muted and that the volume is up, I could not get it to work. I believe my integrated sound card is the ESS ES1978 Maestro 2E. I've read around on the support forum archives, and the best HowTo I could find was this one: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449"). I tried to follow it, and am posting below the code output I got by entering its requests. Still don't have sound. Please help.

```
swarup@swarup-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: E2E [ESS ES1978 (Maestro 2E)], device 0: ESS Maestro [ESS Maestro]
  Subdevices: 2/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
```

```
swarup@swarup-laptop:~$ lspci -v

00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
        Subsystem: Gateway 2000 Unknown device 9300
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 1400 [size=256]
        Capabilities: <access denied>
```

```
swarup@swarup-laptop:~$ sudo modprobe snd-
Display all 151 possibilities? (y or n)
```

Upon clicking "y", 150 lines of code appeared. I selected and pasted below the ones that looked like they might be relevant. If anyone wants to see the rest, let me know and I can paste them here.

```
snd-maestro3  

snd-es1688        
snd-es1688-lib     
snd-es18xx         
snd-es1938  
snd-es1968          
snd-es968
```

If I am correct that my driver is es1978, then according to the direction in the above HowTo I tried to load the driver, because it is not listed in the code (just above) as being loaded (es1978 is not listed among the above "es" codes). So here below I tried to load it, and got the feedback that the module was not found:

```
swarup@swarup-laptop:~$ sudo modprobe snd-es1978
Password:
FATAL: Module snd_es1978 not found.
swarup@swarup-laptop:~$
```

I went to the ALSA website but could not find the place where the drivers are listed for download. Does my thinking so far seem like it may be correct, that my driver es1978 is missing and I need to download it from some website?

---

### Post by swarup on 2008-04-14
I have researched the matter further, and found out that the ALSA driver for my sound card, which is named ES1978 Maestro 2E, is **es1968**. And that driver I do have installed, as you will see in the code of the previous post. So my sound card is identified by Ubuntu, and its driver is installed and running. And in the ALSA mixer, nothing is muted and the volume of the speakers is up. So what is the next step?? Why don't I have sound?

What is the simplest way to test if I have sound or not? I have tried playing sound files using Audacious, Mplayer, and VLC Media Player, and Media Player. But no sound comes. Is that the best way to be confirmed that sound is indeed not working?

ADD: I've just opened Rhythmbox Music Player, selected "Internet Radio" (which I've never done before), and selected one of the default stations (Virgin Radio Classic Rock)-- and to my amazement, it started playing just fine! So now I know that the basic connections are fine, and it can produce sound when the radio is selected. But why can't I select a sound file I have and play it? Is there anything I can check to find out why it will play the internet radio, and not my own sound files?

ADD: I've just retested playing sound files, and it is playing everything!!! I can't believe it. And now only that, when I go on utube, that is now also working again. I have a feeling I know why. On that HowTo mentioned above, it said that it could be that one has the proper driver and everything, but the driver just isn't loading at boot time. And now I've manually loaded it by doing the above code. And the HowTo told how to then reinstall or reset the driver so that it loads properly at boot. I'll try that. With a little luck, that should solve the problem. Perhaps I've solved my own problem! :)

(1 hour later) ...YES! It worked. I added the module "snd-es1968" into etc/modules, then rebooted the computer and now sound is working perfectly. This was definitely the problem, that I had the right driver but it just wasn't loading at boot time. Now it is fine.

---

