---
title: "Lost sound"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by dckirba on 2007-02-06
Hello all,

I posted on the General Support forum regarding this [http://www.ubuntuforums.org/showthread.php?t=353895&highlight=undetected+sound+card]("http://www.ubuntuforums.org/showthread.php?t=353895&highlight=undetected+sound+card"), but haven't had a reply. Sorry to be cross-posting, haven't been able to find a solution.

Here's a quick summary.

1. Running Dapper
2. Installed new GDM theme, decided to logout and login to see what it looked like.
3. Sound control in system tray has x on it after login
4. Error saying no sound device
5. device listed under proc/asound/cards
6. no sound card listed under system>preferences>sound
7. startup sound works, login sound doesn't
8. sound works fine on windows - it's a dual boot

What I've tried:

1. reinstalling gstreamer and alsa
2. searching the forums and google :)

Help would be appreciated. I'm not exactly new, but I'm still taking baby steps here :)

Chhers,
David K

---

### Post by orb9220 on 2007-02-06
[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound)

---

### Post by dckirba on 2007-02-07
Hi Orb,

thanks, that was a useful guide. :)

However, I still can't get sound to work. :confused: I keep getting this error when i try and run alsamixer:

```
alsamixer: function snd_ctl_open failed for default: No such device
```

A google search gave me this:

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg13876.html]("http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg13876.html")

After changing permissions of /dev/snd/controlC0 as mentioned in the link, alsamixer started up, but no sound from xmms :(

So I tried rebooting, but on reboot, the permissions for the file were changed back, alsamixer gave me the same error, and there was still no sound!

Any more help would be greatly appreciated. Thanks a ton,

Cheers,
David K

---

### Post by ^rooker on 2007-02-07
Here's what usually fixes this problem:

-----------------------------
$ asoundconf list
Names of available sound cards:
I82801CAICH3

$ asoundconf set-default-card I82801CAICH3
----------------------------
(of course this will return different soundcard names on your system)

it's because "default" is not mapped properly to your sound device. I guess I've seen this problem 5 times since yesterday already. next time please do some search for the errormessage on the forum - you'll get lucky.

If problems with XMMS still persist afterwards, try setting the alsa-device directly to your soundcard (e.g. "hw,1:0")

---

### Post by dckirba on 2007-02-07
Thankyou for your reply rooker. I did search on the forums and on google and i did try every solution I found listed and nothing worked which is why I'm still asking.

I tried your suggestion and it still doesn't work. 

Cheers,
David K

---

### Post by ComplexNumber on 2007-02-07
some questions:

-do you have more than 1 sound card (ie an inbuilt one and an additioal one which you've bought and inserted?


-can you play music via applications such as amarok, quod libet, rhthmbox, banshee, etc?

-go to main menu -> system -> preferences -> sound. for 'music and movies' in the devices tab, which options does it give you for 'sound playback'? also, when you select and test them all, which ones don't make any sound?

---

### Post by dckirba on 2007-02-08
Hi, thanks for the reply.

to answer your questions:

1. No I haven't installed a new xound crad and there is only one in the system

2. No, none of the sound applications work (Banshee, xmms)

3. I went to system>preferences>sound and I couldn't find a devices tab. Maybe I'm looking in the wrong place...

Cheers,
David

---

### Post by ^rooker on 2007-02-08
hm..... puzzling.
Could you please post some diagnostic output of some programs?
Don't know... something like 

asoundconf -list
lspci
...
(there are some more things, but I forgot them right now)


What's alsamixer saying when you point it to the device directly, instead of going over the "default" alias?

<EDIT>
Stuff in **/proc/asound** is usually helpful in such cases, too.

you can list your alsa devices/subdevices like this:
cat /proc/asound/devices
</EDIT>

---

### Post by dckirba on 2007-02-09
Hiyya Rooker,

How are you doing? Here's everything I managed to get:

```
david@david:~$ cat /proc/asound/devices
 17: [0- 1]: digital audio playback
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
  1:       : sequencer
 33:       : timer
```

```
david@david:~$ asoundconf -list
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card CARD
asoundconf reset-default-card
```

```
david@david:~$ aplay -l
aplay: device_list:221: no soundcards found...
david@david:~$ cat /proc/asound/cards
0 [V8233A         ]: VIA8233A - VIA 8233A
                     VIA 8233A with ALC200,200P at 0xe400, irq 12

```

Alsamixer only works as root. I have added my username to the user group, but that doesn't help. I also changed file permissions of /dev/snd/controlC0 and that gets alsamixer running from normal user, but the permissions change back on reboot. Currently trying to run alsamixer as normal user gives me this:

```
david@david:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

I'm not sure how to point alsamixer directly to the device. Do I do this through alsactl?

I also tried this :

```
david@david:~$ sudo modprobe snd-via82xx 
david@david:~$ alsactl power
alsactl: power:147: No soundcards found...

```

I'm not sure if this is useful, but running lsmod gave me this:

```
david@david:~$ lsmod | grep snd
snd_seq_oss            34944  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                52496  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            28824  0
gameport               15496  2 analog,snd_via82xx
snd_ac97_codec         92064  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53792  0
snd_mixer_oss          18816  1 snd_pcm_oss
snd_pcm                89992  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10760  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
snd_rawmidi            25632  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8844  4 snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    56292  11 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd
```

edit: Hi again rooker, apparently to change the default card I have to edit /etc/asound.conf. However, apparnelty the file doesn't exist! :) 

Thanks for your help, cheers,
David K

---

### Post by dckirba on 2007-02-09
:D Got sound working atleast as root! Here's what I did. Since the /etc/asound.conf file was missing, I created one: (excerpts from my log)

> Created an /etc/asound.conf file and added card to default

```
david@david:~$ cat /etc/asound.conf
# use VIA as default device
# (from /proc/asound/cards)
#
#

pcm.!default {
    type hw
    card V8233A
}
ctl.!default {
    type hw
    card V8233A
}

```

Checked alsa version

```
david@david:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.10.
Compiled on Feb  7 2007 for kernel 2.6.15-27-386.
david@david:~$ cat /proc/asound/cards
0 [V8233A         ]: VIA8233A - VIA 8233A
                     VIA 8233A with ALC200,200P at 0xe400, irq 12

```

Tried playing a sound using asound, received the following error:

```

david@david:~$ aplay /Desktop/sound3.wav
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
aplay: main:544: audio open error: No such device

```

Tried asound as root, sound works.

Tried xmms as root, sound works

Now I just have to get it working as normal user. The group has me added as normal user...

EDIT:  I checked user groups again

```
david@david:~$ grep 'audio' /etc/group 
audio:x:29:root:david
```

But I decided to adduser again

```
david@david:~/Desktop$ sudo adduser david audio
Adding user `david' to group `audio'...
Done.
david@david:~/Desktop$ grep 'audio' /etc/group
audio:x:29:david
```

Now everything works except the tray icon which still shows an 'x' on it, but I'm hoping that'll disappear when I reboot.

Edit Edit: **All is well, reboot and everything works fine!** Now I just have to figure out how to get my boot splash back :) This is fun!

Thanks a lot for your help 
David K

---

### Post by dckirba on 2007-02-09
Hi all, here are some links that helped me solve this issue - 

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound]("http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound")

[http://alsa.opensrc.org/FAQ]("http://alsa.opensrc.org/FAQ")

[http://alsa.opensrc.org/FAQ026]("http://alsa.opensrc.org/FAQ026")

And ofcourse, everyone on the forum! Cheers rooker,

David K

---

### Post by ^rooker on 2007-02-09
Glad to hear that you "hear" something now, but I still have something to say:
1) There exists a "user" counterpart to /etc/asound.conf: 
~/.asoundrc
(and another file with a similar name right next to it, but I forgot...)

Just in case you need to configure something user-specific, then you would do it there.


2) sorry, it wasn't "asoundconf -list", but "asoundconf list" - you pasted the output of what "asoundconf" prints when it gets some unknown parameter. 
It should have returned the name of your soundcard(s).

e.g.: VIA8233A

Executing "asoundconf set-default-card VIA8233A" then, should have automatically configured your ~/.asoundrc to point "default" towards your VIA-soundcard.
Sorry. maybe I wasn't too clear about that in my first post.


3) off-topic:
Are you really living in Addis Ababa? I've been to Khartoum at the end of 2006 and on my way back, the KLM's flying to Adis Ababa first before flying back to Amsterdam. :) So this nice little "loop" added another 3 hours on my flight.... *grrrrr* - and I couldn't even get out of the plane and walk around there....

---

### Post by divali on 2007-02-10
> **^rooker said:**
> Here's what usually fixes this problem:

-----------------------------
$ asoundconf list
Names of available sound cards:
I82801CAICH3

$ asoundconf set-default-card I82801CAICH3
----------------------------
(of course this will return different soundcard names on your system)

it's because "default" is not mapped properly to your sound device. I guess I've seen this problem 5 times since yesterday already. next time please do some search for the errormessage on the forum - you'll get lucky.

If problems with XMMS still persist afterwards, try setting the alsa-device directly to your soundcard (e.g. "hw,1:0")

Well thanks ^rooker  that worked to repair my intermittant sound problem on Edgy

---

### Post by dckirba on 2007-02-10
> **^rooker said:**
> Glad to hear that you "hear" something now, but I still have something to say:
1) There exists a "user" counterpart to /etc/asound.conf: 
~/.asoundrc
(and another file with a similar name right next to it, but I forgot...)

Just in case you need to configure something user-specific, then you would do it there.


2) sorry, it wasn't "asoundconf -list", but "asoundconf list" - you pasted the output of what "asoundconf" prints when it gets some unknown parameter. 
It should have returned the name of your soundcard(s).



Thanks rooker, I'll keep that in mind next time I go around goofing my sound up! :)

> **^rooker said:**
> 
3) off-topic:
Are you really living in Addis Ababa? I've been to Khartoum at the end of 2006 and on my way back, the KLM's flying to Adis Ababa first before flying back to Amsterdam. :) So this nice little "loop" added another 3 hours on my flight.... *grrrrr* - and I couldn't even get out of the plane and walk around there....

Yup, live in Addis. If you're even flying by again I'd love to have a cup of coffee and chat at the airport if you can't get out :)

Cheers,
David K

---

