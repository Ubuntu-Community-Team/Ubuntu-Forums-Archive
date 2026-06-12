---
title: "No sound on fresh install"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by laix1234 on 2006-05-27
I'm using the newest download of Ubuntu and i cant get the sound to work.  The sound juicer and rythmbox both seem to be playing the songs (from a cd, then from the hard drive), but no sound comes out.  my speakers are plugged in, on medium volume, the system volume is at medium, nothing is muted (i checked with the mixer command thingy, not a technical term, i know...), anyone have any ideas?

intel pentium 4 2.8 ghz
soundblaster card of some sort, dont recall...

i checked the device manager but i couldnt make heads or tails of it...

and totem doesnt work, it says the video output is already inuse, but from what i've read that's a different issue...

---

### Post by nudnik on 2006-05-27
When you say the "newest download", do you mean Ubuntu 5.10 or 6.06?

In the meantime you might try this page: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

If none of that works, there is an issue with your hardware. You could try installing the Alsa Firmware Loaders from Synaptic.

---

### Post by catlett on 2006-05-27
I don't know if this will help but it couldn't hurt.[http://ubuntuguide.squarecows.com/doku.php?id=start#how_to_configure_sound_to_work_properly_in_gnome](http://ubuntuguide.squarecows.com/doku.php?id=start#how_to_configure_sound_to_work_properly_in_gnome)

---

### Post by laix1234 on 2006-05-27
catlett, i tried that and still no sound....

nudnik, i believe i mean 5.10, is there an easy way to tell?  i tried the restricted format stuff, but with no luck.  it did what it was supposed to do, but still no sound... 

based solely on what i've been reading, could it be a problem with my soundcard not being recognized, and if so how would i tell?




p.s.  thanks again for everyone's help, it's amazing how fast people who are under no obligation reply to help you on this forum...

---

### Post by nudnik on 2006-05-28
Yes, it sounds as if Breezy (5.10) doesnt like your sound card. ](*,)  A simple way to tell would be to check the device manager, but since it is difficult for you to make out, that really isnt an option. 

Ubuntu is on the verge of a major stable upgrade from 5.10 to 6xx series named "Dapper Drake". The final version will be released June 1st, but you can receive virtually all of the upgrades now via the internet by typing: gksudo "update-manager -d" after a terminal prompt. 

The new version may support your soundcard without problems. It is much more up to date than 5.10, which failed to recognize about half of my hardware. After I upgraded to Dapper, the OS now recognizes everything.

One, although certainly not the only, easy way to tell what version you are running  is to look at the default home page installed under Firefox. If you are running Breezy, the home page will reflect this in large print, and the same is true with Dapper. 

Similar information should also appear under the 'system' menu under "about".

Yes, this is a friendly forum. You can learn quickly about Linux and Ubuntu, one of the reasons I prefer this distribution.

---

### Post by catlett on 2006-05-28
This is the wiki for nudnik's instructions on upgrading [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

---

### Post by laix1234 on 2006-05-28
Ok, I updated to 6.06 dapper drake, but still no sound... is there some way I can check the config file or something to see if it is recognizing my sound card or not?  Could you tell me the command and I could paste the part you need to see here?  Or tell me what to look for....  not having sound is driving me nuts...

---

### Post by christhemonkey on 2006-05-28
Try doing a:

```
lspci 
```


If it lists anything like multimedia or sound device then alls well and good.
(if not, well, lets hope it is there)

If its there do a
```
lsmod | grep *insert module name here* 
```

To find the module name, im afraid your gonna need to know what card you have.
(The lspci command should say.)
Then go [here]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix") and find the correct module for your card and put it in the above command.

---

### Post by laix1234 on 2006-05-28
It says Creative Labs SB Audigy LS, but i couldnt find that on the list... there were audigy ones but not audigy ls, and there was a sound blaster ls, but without the audigy.... any ideas?  and what info from the list do i put in that command?

---

### Post by christhemonkey on 2006-05-28
I would try three different drivers, one by one.
SB0310
P17
emu10k2

You could also run the lsmod command withouth the "| grep" bit on the end.
And see what it says.


Could you post the outup of:
```
cat /proc/asound/cards
```
and
```
aplay -l 
```

---

### Post by laix1234 on 2006-05-28
how do I change those drivers, when i tried the lsmod | grep SB0310 before it didn't change the driver (as shown under System -> Administration -> Device Manager), even after reboot it still shows CA0106 as the driver for the SB Audigy LS device.

Without the | grep it says 

Usage: lsmod



cat /proc/asound/cards     yielded this:

0 [CA0106         ]: CA0106 - CA0106
                     Live! 7.1 24bit [SB0413] at 0xcda0 irq 217




aplay -l                              yielded this:

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

none of the lsmod commands with different driver numbers seemed to be changing the driver as seen under the device manager, do i need to reboot after changing it for it to take affect?

---

### Post by laix1234 on 2006-05-28
....... I hate myself..... 

sort of.  I fixed it.  I needed to right click on the volume button, open volume control
Edit -> Preferences

turn on/check all the options, then turn all the sliders up once they appear, for example analogue rear, side, etc.  that gave me sound.... thanks for all your help, and I'm sorry it turned out to be something stupid like that...

---

### Post by Sef on 2006-05-28
> turn on/check all the options, then turn all the sliders up once they appear, for example analogue rear, side, etc. that gave me sound.... thanks for all your help, and I'm sorry it turned out to be something stupid like that...

No problems.  I was just going to suggest that because I noticed that no one suggested that.  Often it is the easy things that are overlooked.  It has taken me a while to remember to think of those first.

---

