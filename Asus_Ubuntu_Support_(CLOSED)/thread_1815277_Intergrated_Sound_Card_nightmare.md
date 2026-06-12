---
title: "Intergrated Sound Card nightmare"
date: 2011-07-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by cyberyaga on 2011-07-31
Hi... Please help the noob out :'(

I've been at this for two days straight. The wife is going to leave me.

Motherboard: Asus P5GC-MX
Soundcard: Realtek ALC883 7.1 Intergrated Soundcard.
Sound via toslink cable(optical).

I installed Ubuntu 11... Installed XBMC... Everything is perfect, except for one thing. I'm only getting stereo audio in my home theater.

After checking ALSA mixer, i see that there is no SPDIF output, and my soundcard is listed as a REALTEK ALC662 rev1.

So, I go to the realtek website and download the linux driver pack for my soundcard. The instructions are fairly simple: ```
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Complied source code
    a. cd alsa-driver-1.0.xx
    b. ./configure --with-cards=hda-intel
    c. make
    d. make install

Step 3. reboot your machine
```After I reboot *NO SOUND* =D>

I checked under [Sound Preferences] --> [Hardware]: now It's empty.](*,)

I've done lots of reading, but I find myself even more confused. Please someone help me in trying to figure this out. It's just a soundcard for crying out loud.

Thanks in advance :(

---

### Post by cyberyaga on 2011-08-01
Hey Guys... Thanks for all your help... 


Well... After pulling my hair for two days straight, I finally found the solution.

To get my sound back (after screwing it up), I had to re-install ubuntu. 

Once the install was done, and I had stereo sound, here is what I did to get DTS and AC3 sound.

Went to this link: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Went to the "Is ALSA using the correct model?" section. Followed it to the T.

In Short, I updated my /etc/modprobe.d/alsa-base.conf

and included options snd-hda-intel model=3stack-dig

Went to alsamixer and unmuted spdif, and XBMC started playing DTS and AC3 sound [IMG]http://forum.xbmc.org/images/smilies2/yes4lo.gif[/IMG]

Hope this helps someone... Again, couldn't do it without you guys ;)

---

