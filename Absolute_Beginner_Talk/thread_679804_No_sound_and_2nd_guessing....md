---
title: "No sound and 2nd guessing..."
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by jtbrookreson on 2008-01-27
I am running 6.10 on a G3 iBook 500 mhz and 278 ram. And for the most part, I am happy with everything, except that I have no sound. I originally had 6.06 on the machine, with sound, but when I upgraded it to 6.10 on someone's suggestion, I guess it didn't recognize the soundcard. How do I fix this. I am a bit of a noob, and a partial idiot.

But all that being said, am I running with the right system? After doing some reading I see people talking a Kabuntu, Xubuntu, or suggesting to other poeple with specs like mine to upgrade to 7.04...All I really want this machine to do is surf the internet, read and write email, and creating/reading documents/spreadsheets/databases/presentaions...and do it at a speed that isn't like waiting for Heinz ketchup somming out of a new bottle....

Again, I thank you for all of your help and suggestions...

-JTB

---

### Post by ~LoKe on 2008-01-27
Xubuntu and 7.10 might work best for you.  The newer the distribution, the more support for older hardware there will be.  Xubuntu is pretty light-weight, and as far as Ubuntu goes, it's probably your best option.

I'm no expert with sound, but let's get the ball rolling.  What's the output of this, in the terminal:
```
lsmod|grep snd
```

---

### Post by jtbrookreson on 2008-01-27
I am assuming you wanted me to type that command,

and this is what I got

snd_aoa_i2sbus         24516  0 
snd_pcm_oss            54048  0 
snd_mixer_oss          22144  1 snd_pcm_oss
snd_pcm                95556  2 snd_aoa_i2sbus,snd_pcm_oss
snd_timer              26980  1 snd_pcm
snd_page_alloc         11368  1 snd_pcm
snd                    69940  5 snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11396  1 snd
snd_aoa_soundbus        7972  1 snd_aoa_i2sbus
joshtyler@ubuntu:~$ 


what that means, I have no stinkin' clue....

Thanks for the help, by the way....

-JTB

---

### Post by ~LoKe on 2008-01-27
Basically that command lets us know which sound modules are loaded.  This should hopefully help others figure out what's wrong so they can help.  I'll do some digging, and if I find something I'll be back. =]

---

### Post by jtbrookreson on 2008-01-27
Thankyou....

By the way, does Xubuntu support Open Office? That is a must for me...

---

### Post by ~LoKe on 2008-01-27
> **jtbrookreson said:**
> Thankyou....

By the way, does Xubuntu support Open Office? That is a must for me...

Yes, all versions of Ubuntu should include OpenOffice by default.

---

### Post by dsplabs on 2008-01-27
looks like the audio device has been detected... whats the output of ```
ls -la /dev/snd
```???

have a read through [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound")
it should have some more answers for you...

---

### Post by jtbrookreson on 2008-01-27
total 0
drwxr-xr-x  2 root root      60 1904-01-01 00:01 .
drwxr-xr-x 12 root root   13340 2008-01-27 11:23 ..
crw-rw----  1 root audio 116, 2 1904-01-01 00:01 timer

---

### Post by jtbrookreson on 2008-01-27
have a read through [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound]("http://ubuntuforums.org/showthread.php?t=205449&highlight=sound")
it should have some more answers for you...[/QUOTE]

I have been reading through the pages suggested above, and I came down to this..

joshtyler@ubuntu:~$ aplay -l
aplay: device_list:222: no soundcards found...
joshtyler@ubuntu:~$ lspci -v
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea AGP
        Flags: bus master, 66MHz, medium devsel, latency 16
        Capabilities: <access denied>

0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Rage Mobility M3 AGP 2x
        Flags: bus master, stepping, 66MHz, medium devsel, latency 255, IRQ 48
        Memory at 94000000 (32-bit, prefetchable) [size=64M]
        I/O ports at f0000400 [size=256]
        Memory at 90000000 (32-bit, non-prefetchable) [size=16K]
        Expansion ROM at f1000000 [disabled] [size=128K]
        Capabilities: <access denied>

0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea PCI
        Flags: bus master, 66MHz, medium devsel, latency 16

0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Pangea Mac I/O
        Flags: bus master, medium devsel, latency 16
        Memory at 80000000 (32-bit, non-prefetchable) [size=512K]

0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 16, IRQ 27
        Memory at 80081000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 16, IRQ 28
        Memory at 80080000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea Internal PCI
        Flags: bus master, 66MHz, medium devsel, latency 16

0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth/Pangea FireWire (prog-if 10 [OHCI])
        Subsystem: Apple Computer Inc. UniNorth/Pangea FireWire
        Flags: bus master, 66MHz, medium devsel, latency 16, IRQ 40
        Memory at f5000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

0002:20:0f.0 Class ffff: Illegal Vendor ID Unknown device ffff (rev ff) (prog-if ff)
        !!! Unknown header type 7f

Now I am not sure where to go next. I know there is a sound card in here...But I don't really know if 6.10 is detecting it or not. Nor do I know what type of card it is...

I'm trying to fix this on my own, but being the Noob that I am, I feel like I am reading Greek at times...

Any suggestions? Thanks for your help.

-JTB

---

