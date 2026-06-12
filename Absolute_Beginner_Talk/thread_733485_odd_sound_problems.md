---
title: "odd sound problems"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Wolfan on 2008-03-23
Okay so here's my newest sound issue.  A while back I posted this -> [http://ubuntuforums.org/showthread.php?t=718319](http://ubuntuforums.org/showthread.php?t=718319) which couldn't get solved...well I solved it by plugging my headphones and or speakers (both surround) into my into my microphone port.  (This actually happened by accident one day, since all three ports (Speak, Mic, Head) are all close to each other.)

At first this seemed like a good solution, until I noticed that the sound coming out of the microphone port is not very good, also when I go to adjust the volume it doesn't work, I could mute "Master" in alsamixer and sound would be just as loud instead I have to change "Front".  This just doesn't seem right to me, so one day I sat and fiddled with my mixer's options, changing everyone that seemed relevant and some that were obviously not relevant.  So now I'm stuck...and hoping that you can help.:confused::confused:

PS If you need it, I posted a few commands in that preceding post.

---

### Post by erginemr on 2008-03-24
The poster of this topic:
[http://ubuntuforums.org/showthread.php?t=729859](http://ubuntuforums.org/showthread.php?t=729859)
has a sound card almost identical to yours. So, I beileve it will work in your case, too.

Also, please refer to these posts:
[http://ubuntuforums.org/showpost.php?p=4453784&postcount=8](http://ubuntuforums.org/showpost.php?p=4453784&postcount=8)
[http://ubuntuforums.org/showpost.php?p=4574654&postcount=10](http://ubuntuforums.org/showpost.php?p=4574654&postcount=10)

where two possible methods have been suggested, one is identical to the one above and the other is to recompile ALSA kernel by the help of two very easy to use scripts.

---

### Post by Wolfan on 2008-03-25
Thank you very much for posting these, After trying the quicker of those to solutions (to no avail)  I ended up on [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) which seemed to summarize all of what the posts seemed to be suggesting doing.  I've been following along with that page and I got to the point where I'm supposed to find my Codec model and compare it to ALSA-Configuration.txt, my problem is the following output

```

vinnie@vinnie-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory

```

Which confused me, so I used lspci hoping it was the same thing, 
```
 00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
```
My sound card model according to that is ICH5 or ICH5R (if I'm reading it correctly), and the only entry that applies to me is: 

```

Module snd-intel8x0
  -------------------

    Module for AC'97 motherboards from Intel and compatibles.
			* Intel i810/810E, i815, i820, i830, i84x, MX440
				ICH5, ICH6, ICH7, ESB2
			* SiS 7012 (SiS 735)
			* NVidia NForce, NForce2, NForce3, MCP04, CK804
				 CK8, CK8S, MCP501
			* AMD AMD768, AMD8111
			* ALi m5455

    ac97_clock	  - AC'97 codec clock base (0 = auto-detect)
    ac97_quirk    - AC'97 workaround for strange hardware
		    See "AC97 Quirk Option" section below.
    buggy_irq     - Enable workaround for buggy interrupts on some
                    motherboards (default yes on nForce chips,
		    otherwise off)
    buggy_semaphore - Enable workaround for hardwares with buggy
		    semaphores (e.g. on some ASUS laptops)
		    (default off)
    spdif_aclink  - Use S/PDIF over AC-link instead of direct connection
		    from the controller chip
		    (0 = off, 1 = on, -1 = default)

    This module supports one chip and autoprobe.

    Note: the latest driver supports auto-detection of chip clock.
    if you still encounter too fast playback, specify the clock
    explicitly via the module option "ac97_clock=41194".

    Joystick/MIDI ports are not supported by this driver.  If your
    motherboard has these devices, use the ns558 or snd-mpu401
    modules, respectively.

    The power-management is supported.

```

So I went into /etc/modprobe.d/alsa-base and added the line 
```

options snd-hda-intel model=snd-intel8x0

```

Then when that didn't work changed the model to simply intel8x0

The problem hasn't changed at all.

I'm hoping that I'm just not following the directions correctly, or that if I am I've stirred someone to see something that I don't. Anyone know what's wrong?

--Thanks

---

