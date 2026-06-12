---
title: "a little help guys"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-02-13
first: i am an your village idiot when it comes to ubuntu.
i installed ubuntu about a week ago not bad i like it very much
video,printing,digital camera recognised ,installed automatix up-graded some programs with very happy with it so far except for my sound .at first i had no sound ,the volume icon was as if muted when cliking on it i got "no sound device detected..." this was an on board sound card (dell optiplex gx1 p3 600mhz 128 ram)
whent out and got a creative sound blaster sound card 24 bit from staples after installing it was recognised by ubuntu. in multimedia selector at first the only that would test was (esd) alsa, arts, oss got " could not create pipe line to....."
yesterday i forgot what i did but alsa tested ok. the only problem my sound i very weak and scratchy , noisy etc.... and only the left speaker works i tried 2 different speakers and head phones, out of the 4 jacks on the sound card only one works. my volume control says : ca 0106 (alsa mixer). in multimedia selector i selected alsa for both. i know that this question has been asked before i have read post suggesting to enter this and that code. where and how do i enter such codes?
sorry for being a bug but i really like ubuntu just need to get over this sound problem. should i get a different sound card ? does my system not support 24 bit?
 any way thank you.

---

### Post by Jedeye on 2006-02-13
Hi I'm new to linux and this is probably a simple solution that you have already tried but I will post it just in case. I have a sound blaster card as well, and after I first installed ubuntu the only thing I had to do was go to System>Preferences>Sound and change it from my on board device to the sound blaster device.

Sorry I don't have any more options, but thats all I know ;)

---

### Post by abu-fatu on 2006-02-13
thank you jedeye in sound preferences i only get one card :" ca 0106" the same as in volume control. in device manager in get under SB Audigy LS> advance> info.linux.driver  type= string.   value=CA0106
may the force be with us.

---

### Post by Jedeye on 2006-02-13
Hi again... I found this link and thought you may find some answers in it.
[http://alsa.opensrc.org/index.php?page=TroubleShooting]("http://alsa.opensrc.org/index.php?page=TroubleShooting")

This part in particular stood out:
> 10) Sound can be heard but it is distorted

    * Some cards, notably SB Live! ones, suffer from distortion if the volume on some subchannels is higher than 66%. Some suffer distortion if the Master volume is higher than 66%, for some others the threashold is 50%. Reduce all volume setting. If the distortion goes away, experiment until you determine which are the highest volume settings that don't trigger distortion.
    * Some cards, especially motherboard chipsets, have small limits on the fragment size (specified for example in the D Mix Plugin configuration). Many cards cannot handle fragment sizes greater than 4096 bytes, and if it is bigger the fragment seems to be truncated and the sound becomes choppy.
    * Some cards, especially recent ones, can only handle a fixed set of frequencies. Some can only handle a single frequency, usually 48000Hz. try to use the plug: plugin prefix when playing. If your card can only play a single fixed frequency you must ensure that the driver is told that (by the use of driver-specific option parameters), and the ALSA library is setup up to output sample only at that frequency. Usually this will involve using the plug plugin in /etc/asound.conf.


Once again good luck!

---

