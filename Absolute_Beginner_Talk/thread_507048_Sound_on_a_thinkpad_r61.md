---
title: "Sound on a thinkpad r61"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by wfsswmr7285 on 2007-07-22
I'm a new Ubuntu user, just having switched after having used macs for over ten years. I have a new Lenovo thinkpad r61 and I've been tinkering around on it for a few days. I have it installed and running, but I have a few problems. I've searched online for solutions, but I have not found a solution I could readily understand or properly run. My main concern is the lack of sound. I've tried everything I could find on the web -  turning on the modem in bios, updating the alsa and much more, but to no avail. Please please help me.

Also, if someone could teach me how to move the menubar from each window to the top of the screen, like on macs, I would appreciate that also.

---

### Post by wfsswmr7285 on 2007-07-22
bump....

---

### Post by annda on 2007-07-22
sorry, not many ideas about sound, you seem to have done everything, probably unmuting everything in alsamixer too...

is the hardware even recognized? what is the output of
```
sudo lshw -class multimedia
```

as to mac-like behavior of menubars, you need kde for that, i think gnome doesn't do it at all.

---

### Post by Tobba25 on 2007-07-22
I have an R61 as well. With sound problems. Here are my output of that command:

```
    description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: iomemory:fe020000-fe023fff irq:21

```

---

### Post by wfsswmr7285 on 2007-07-22
that's the same as mine. i've looked online and found that the latest intel sound card supported by the latest release of alsa is the ICH7 family. There have been others online who've bypassed that but nothing for me.

---

### Post by wfsswmr7285 on 2007-07-22
[http://ubuntuforums.org/showthread.php?t=503233&highlight=r61&page=2](http://ubuntuforums.org/showthread.php?t=503233&highlight=r61&page=2)

this makes it work!!!

now i've got another problem. When I press the volume up/down buttons, the computer pops up the thing that shows the volume bar going up and down, but the volume doesn't change. 

ARGHH!!!

also the wireless on this thing keeps bugging out and i have to turn it on and off a couple times before i can get it to work.... any suggestions?

---

### Post by wfsswmr7285 on 2007-07-22
sound issue was quickly fixed by right clicking on the sound icon in the upper right and changing from microphone to pcm!!!

---

### Post by wfsswmr7285 on 2007-07-22
and now it doesn't work again... the volume control that is. everytime i try to use it, it affects only the microphone volume. even when set to pcm

---

### Post by Tobba25 on 2007-07-23
My wireless is a little buggy as well. But mostly it works pretty good!

I think I'll wait for 7.10 before before I start tinkering too much with these bothering issues. Dell has recently launched Ubuntu-hardware with the same specs as our machines. So I guess it'll be sorted out :-)

But I'll try that sound thing. Is feisty fawn = 7.04? (I hate it when ppl use those funky names instead of numbers)

Anyway, lets keep in touch! We R61 folks should hold together. Lets even start a dedicated thread to all R61 specific issues :-)

---

### Post by Tobba25 on 2007-07-23
Yeah that solutions does not work for me. Unexpected errors with the tar command and stuff.

:(

---

### Post by wfsswmr7285 on 2007-07-23
i had the same problem at first. remember to put all the tar files in your user folder or else move to whatever folder the tar files are in while working in the terminal.

---

### Post by Tobba25 on 2007-07-23
Ok I did, and I got a little bit further. When typing the command "sudo ./configure && sudo make", i got this:

```
[1] 15128
make all-deps
make[1]: Entering directory `/home/torbjorn/alsa-driver-1.0.14'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/torbjorn/alsa-driver-1.0.14'

Please, run the configure script as first...

torbjorn@Tobbanovo:~/alsa-driver-1.0.14$ checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

[1]+  Exit 77                 sudo ./configure


```

---

### Post by Tobba25 on 2007-07-23
Ok, forget all of the above :-D

Ive been thru all the steps, still no sound... Dang..:confused:

---

### Post by wfsswmr7285 on 2007-07-24
did you reboot and remember to unmute everything in the alsamixer pressing m while selecting the speaker and headphone options?

---

### Post by Tobba25 on 2007-07-24
Woho!!

It works! Fun stuff :guitar: :popcorn:

Now lets get that fingerprint reader to work ;) OOH! Wouldn't it be fun to log in with your finger only, and upon the fingerwipe, the computer totally freaks out in future-ish SGI 3-d effects as in hollywoodflicks when acknowledging your login!? :-D

---

### Post by wfsswmr7285 on 2007-07-24
do the volume buttons on your computer work properly? mine dont....:confused:

---

### Post by Tobba25 on 2007-07-24
No they dont. But I find that taking it all the way down reduces some disturbance sound that i can hear when I am using my headphones.

---

### Post by wfsswmr7285 on 2007-07-24
mine did that too.... i found that the volume buttons change the settings of the microphone... idk why, but i think that's why there's that noise when i raise the "volume" all the way up - because that turns up the microphone causing feedback.

anyone know how to fix this?

also anyone know how to fix the wireless? mine's very very buggy

---

### Post by wfsswmr7285 on 2007-07-24
Found the answer to the sound bit: 
"Maybe you (the submitter) already knows this, but you can control what volume (PCM, Master, etc) the keyboard buttons change by selecting the required one under "Default Mixer Tracks" in Sound Preferences (System -> Preferences -> Sound). If your bug goes beyond this, then excuse this message :)"

Source:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/97530](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/97530)

---

### Post by wfsswmr7285 on 2007-07-24
Now that the sound is all fixed, does anyone know how to get the wireless working properly and how to put 3d drivers for the integrated Intel X3100 video chip?

---

### Post by Tobba25 on 2007-07-25
I've got no s-video out. Thats a bit irritating, as I quite often connected my mac to my tv set and watched movies.

Is it possible to do something of the same via the connection on the right of my machine, the normal vga thing?

---

### Post by wfsswmr7285 on 2007-07-26
you can buy vga to svideo converter cables online

---

### Post by smbm on 2007-08-05
Is anyone else having trouble with USB devices not automounting?

---

### Post by Tobba25 on 2007-08-05
No, I have tried both externat harddisks and USB pens, they have all working... What kind of devices have you tried?

---

