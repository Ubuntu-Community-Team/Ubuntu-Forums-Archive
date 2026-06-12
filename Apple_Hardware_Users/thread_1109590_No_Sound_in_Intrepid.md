---
title: "No Sound in Intrepid"
date: 2009-03-28
forum: Apple Hardware Users
---

### Post by hirnsaege on 2009-03-28
Hello!

After running into some problems during the installation process I finally managed to get Xubuntu-Intrepid finally up and running. After compiling a new kernel, everything went pretty smooth.

Well, the problem I've run into now is that I can't get sound on my Powerbook Titanium to work. 

The google results pointed me towards loading the snd_powermac kernel module, which is loaded. Alsamixer also detects the sound device as "Powermac Snapper", yet no sounds are being heard. Another link said to maximize the DRC level in alsamixer, which I can't. It's stuck at zero and won't go up.
The XFCE mixer only detects the sound device as default and shows no available channels.
I also tried sudo alsa reload, when I do that, the speakers give me some crackling sound as if they were being activated, just like when loading snd_powermac, yet it doesn't do anything.

Some output that might be needed:
```
felix@finnegan:/proc$ cat /proc/cpuinfo
processor	: 0
cpu		: 7455, altivec supported
clock		: 800.000000MHz
revision	: 2.1 (pvr 8001 0201)
bogomips	: 79.83
timebase	: 33331610
platform	: PowerMac
model		: PowerBook3,4
machine		: PowerBook3,4
motherboard	: PowerBook3,4 MacRISC2 MacRISC Power Macintosh
detected as	: 73 (PowerBook Titanium III)
pmac flags	: 0000001b
L2 cache	: 256K unified
pmac-generation	: NewWorld
Memory		: 512 MB
```

```
felix@finnegan:/proc$ uname -r
2.6.29
```

Thanks for your help,
felix

---

### Post by jamesey on 2009-03-29
I haven't used a power pc but is it possible you might need to edit your etc/modprobe.d/alsabase and options file? Someone with more experience might be able to answer that for you.

---

### Post by sms0611 on 2009-03-29
I'm not running Intrepid but what I did to solve my sound problem with my powerpc running Hardy was to download and install the latest version of alsa.

Hardy package manager has alsa version 1.0.16 as the latest version (in fact it is 1.0.15 according to alsa) so I got the latest version (1.0.19) from alsa project installed it ran alsaconf and hey presto sound.

hope this helps.

---

### Post by hirnsaege on 2009-03-29
Some updates:

More or less by accident I stumbled upon /etc/pbbuttonsd.conf, and i noticed, that it had the parameter [I]ALSA_CARD = default
[/I], so I took some time to find out what the name of the sound card the system recognizes is, exactly:

```
felix@finnegan:/dev/snd$ asoundconf list
Names of available sound cards:
Snapper
felix@finnegan:/dev/snd$ cat /proc/asound/cards
 0 [Snapper        ]: PMac Snapper - PowerMac Snapper
                      PowerMac Snapper (Dev 26) Sub-frame 0
```
```

felix@finnegan:/dev/snd$ asoundconf list
Names of available sound cards:
Snapper
```

If I change the value of ALSA_CARD to Snapper, I get this:
```
felix@finnegan:/etc/default$ sudo /etc/init.d/pbbuttonsd restart
 * Restarting pbbuttonsd                                                        ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL Snapper
FEHLER: Kann Card 'Snapper' nicht hinzufügen: No such file or directory.
pbbuttonsd 0.7.9: PowerBook G4 Titanium III (Apr 2002) - PMU version: 12
                                                                         [ OK ]
```

I just wanted to see if there was a way around installing the new ALSA modules, but I guess I'll try that next.

---

### Post by sms0611 on 2009-03-29
I messed around with a lot of different settings before upgrading the alsa version in the end this was the only thing that worked.

If you are worried about the procedure have a look at this

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Don't forget to run alsaconf after upgrading.

Have you looked at the following?

system->preferences->sound
   All of the options should be set to ALSA
   And the default mixer tracks device set to (in your case)
      Snapper (Alsa Mixer)

GNOME ALSA mixer->Edit->Sound Card Properties
   All of the options you need should be checked.

   If you think you are missing options have a look at
/etc/asound.state

   Also in /etc/rc.local I have the following

amixer sset 'Auto Mute' off
amixer sset 'PC Speaker' on

---

### Post by hirnsaege on 2009-03-29
The problem I was worried about when compiling the new alsa drivers was 
about Synaptic going berserk, mixed up file versions and so on, but it 
all went flawlessly.

So, when booting, I hear the sound the WM makes when being loaded.
After that, it doesn't work anymore.
I think I've traced the problem down further: my regular user account 
doesn't have sufficient rights to use, or even register a sound card:

```

felix@finnegan:/var/lib/alsa$ aplay /home/felix/test.wav
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function 
snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat 
returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer 
returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or 
directory
ALSA lib pcm.c:2202:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:590: Fehler beim Öffnen des Audiogerätes: No such file or 
directory
```

Whereas as root, sound works great:
```
felix@finnegan:/var/lib/alsa$ sudo aplay /home/felix/test.wav
Wiedergabe Wave 
'/home/felix/Desktop/gkismet-0.0.10/sound/junk_traffic.wav' : Signed 16 
bit Little Endian, Samplingrate: 11025 Hz, Mono
```

So, I changed the rights on /dev/mixer and /dev/snd/* from 660 to 666. 
Won't you look at that, sound works for my regular user, from console as 
well as out of XFCE. The graphical mixer also works, such as setting the volume for device "default" affects the setting for Snapper.

The chmod settings don't persist after a reboot, however. I was thinking of writing a startup script for this, I don't know where to put it, tough. Is there such a thing as rc.conf in Ubuntu? Or can you think of a neater solution to this problem?


And another thing: I still get some error messages at boot, at least some things that are failing to initialize and so on.
Typing dmesg in console still doesn't give me those messages, however. How can I review the messages passed to me on boot?

---

### Post by sms0611 on 2009-03-29
So far so good.

You could put your chmod into /etc/rc.local if you really need to but I don't understand quite why this should be necessary. I had no problem with it. Is it possible that this is a specific Intrepid problem?

Are you sure you followed these instructions exactly?

Short Alsa-Upgrade script install instructions:
1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.x-rev-1.16.tar
4. sudo ./AlsaUpgrade-1.0.x-rev-1.16.sh

It may be worth looking at the sh script to see exactly what is happening or looking into the log file to see what it did.

One thought, I am not a very experienced Ubuntu user but do you not need to do the chmod as sudo chmod as per the alsa quick install instructions.

---

### Post by sms0611 on 2009-03-29
As to logging your boot messages have a look here

[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

hope this helps.

---

### Post by hirnsaege on 2009-03-29
I didn't install the ALSA update using the script you provided, I read your post after I was already done. I simply compiled the packages provided from the ALSA website from source.

Of course I did sudo chmod, it doesn't work any other way in /dev anyway. 
It's definitely a rights problem. I'll try rc.local and report back.

---

### Post by sms0611 on 2009-03-29
If I was you I think I would uninstall what you have done and run the script. It may be a hammer to crack a nut but may save a lot of time in the long run.

---

### Post by hirnsaege on 2009-03-30
Hey!

So, I tried running the script a few times and it always failed while compiling, because of [this]("http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg60310.html") bug. 

I also tried to export KERNELPATH since the file's there in the kernel sources, just not in the headers. Didn't work, however, so now I'm back at where I was before, running the modules compiled by hand. Having chmod 666 /dev/snd/* in rc.local works fine for me, even after rebooting.


Thanks for the link about boot logging. It doesn't work, however, I'm going to have to look further into that.

One problem solved, a few to go. I still have problems with the screen being distorted (at random, it seems), a simple reboot often does the trick for that. Also, waking up from Suspension needs about 5 minutes due to a "kernel badness". I'll try to solve these things, but I guess I might come here again if I'm stuck. 

Thank you for your help.

---

### Post by stream303 on 2009-03-31
Does loading the alsa module as the **last module** you load help?

I've had to do this on other distros to get alsa to work properly - not sure with ubuntu however.

---

### Post by sms0611 on 2009-03-31
It doesn't seem to matter when ALSA loads, at least I don't think so, I certainly made no special provisions for load order. It rather seems to be a known bug which was fixed in version 1.0.16rc (whatever that means) anyway as the latest version is 1.0.19 that's the one I'm using and it's all working just find (apart from the system sounds for which I've not yet found a solution)

---

