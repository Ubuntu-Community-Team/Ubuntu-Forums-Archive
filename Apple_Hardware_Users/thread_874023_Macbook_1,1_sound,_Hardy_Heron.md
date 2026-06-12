---
title: "Macbook 1,1 sound, Hardy Heron"
date: 2008-07-29
forum: Apple Hardware Users
---

### Post by baofeibo on 2008-07-29
First off, Hi! :)

I have a first generation Macbook. I double boot OSX and Ubuntu just to make the world a better place. I installed Ubuntu 7.10 and updated to 8.04 only to discover that my sound does not function in 8.04. 

I attempted the fix [here]("http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/"), even though it isn't for my generation, and, unsurprisingly, it didn't work. :shock:

How can I figure out what's wrong with my sound, and how can I fix it?

Thanks in advance!

---

### Post by cyberdork33 on 2008-07-29
> **baofeibo said:**
> First off, Hi! :)
Hello!

> **baofeibo said:**
> I have a first generation Macbook. I double boot OSX and Ubuntu just to make the world a better place. 
Then it really must be good, because I dual-boot too.

> **baofeibo said:**
> I installed Ubuntu 7.10 and updated to 8.04 only to discover that my sound does not function in 8.04. 

I attempted the fix [here]("http://zepsling.wordpress.com/2008/05/03/enable-macbook-sound-in-hardy/"), even though it isn't for my generation, and, unsurprisingly, it didn't work. :shock:

How can I figure out what's wrong with my sound, and how can I fix it?
First run 'alsamixer' in a terminal and make sure that all the channels are unmuted and turned up. If that doesn't work, then have a look here:
[https://help.ubuntu.com/community/MacBook#Sound](https://help.ubuntu.com/community/MacBook#Sound)

---

### Post by baofeibo on 2008-07-30
Many thanks for the response!

Alright, I know something is not entirely as it should be...

When I run "alsamixer" I am presented with two sliders and a number value, labeled Master, PC Speak and BaseFRQ. BaseFRQ is the number value (18643) and I can change it to it's double (37286), but that change does not seem to affect anything (no sound either way). Master I can move about as I wish, but it doesn't give me sound, PC Speak is at 00 and I can't move it. :cry:

Where did I go wrong?

I have this nagging feeling that it has something to do with ALSA displaying 'pcsp' as my sound card, but I'm too much of a n00b to really know. (I'm pretty sure I have ALSA 1.0.16 drivers, but I'll try reinstalling them, just for kicks.)

EDIT: Actually, alsamixer displays itself as being 1.0.15, so I must have botched the driver install somehow...

---

### Post by cyberdork33 on 2008-07-30
yea you should have many more channels than that.

---

### Post by baofeibo on 2008-07-30
Apparently I am so inept that I can't even install ALSA. 

When I run the commands from the Macbook sound tutorial I get nothing, it says it's already installed... but my alsamixer still tells me that it's version 1.0.15. :confused:

I'm not a terminal wizard (far from it), so I'm just taking the instructions step by step. I'm on my fifth try now (maybe it rolls a twenty sided die in order to decide if the drivers will install)...

So, here's what I'm doing... make sure my alsa source is updated (that IS what this bit does, right?)

```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
```

"alsa-source is already the newest version." is part of the output, so yeah, mission accomplished, I think...

So then I do:

```
sudo dpkg-reconfigure alsa-source
```

Gives me a prompt "Build ALSA drivers with ISA PnP support?"

Sure, sure, PnP support (whatever that is)... ISA, whatever. I choose YES.

Another Prompt "Build ALSA drivers with debugging code?"

Yah, I was a code guru in another life, hit me with it. I choose YES.

And then I see this "Please select the ALSA sound card drivers that should be included in alsa-modules packages built from these sources. (line break) The following is a list of available sound card drivers along with short descriptions."

Peachy, sound card driver descriptions. Short ones.

I select <Ok> and continue to the next page...

Where I am confronted with "ALSA drivers to build: " and a long list of drivers, starting with an 'all' option, which is marked with an asterisk. Now, I can't seem to change the selection, nor can I get to <Ok> at the bottom of the dialogue (I can scroll to the last entry, but can't get to <Ok>). Ok then, I give up trying to change the selection and press my return key. And I'm back at my terminal. So I do this:

```
sudo module-assistant a-i alsa-source
```

And I get:```

Updated infos about 1 packages
Getting source for kernel version: 2.6.24-19-generic
Kernel headers available in /usr/src/linux-headers-2.6.24-19-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
unpack 
Extracting the package tarball, /usr/src/alsa-driver.tar.bz2, please wait...
Target package file 
/usr/src/alsa-modules-2.6.24-19-generic_1.0.16-0ubuntu4+2.6.24-19.36_i386.deb 
already exists, not rebuilding!
(however, you could use the -f switch to ignore it)
dpkg -Ei /usr/src/alsa-modules-2.6.24-19-generic_1.0.16-0ubuntu4+2.6.24-19.36_i386.deb 
Version 1.0.16-0ubuntu4+2.6.24-19.36 of alsa-modules-2.6.24-19-generic already installed, skipping.

```

Sorry to attach a novel and all, just want to spell out my actions so everyone can know how crazy nubly they are. I am not proud, please tell me how stupid I'm being. :)

---

### Post by cyberdork33 on 2008-07-30
> Version 1.0.16-0ubuntu4+2.6.24-19.36 of alsa-modules-2.6.24-19-generic already installedSo yea it's installed... but it is still loading an older driver for some reason.

Just to get things out of the way... You are rebooting after this right?

---

### Post by baofeibo on 2008-07-30
Yes, I have rebooted. (Thanks for putting up with me, by the way.) :)

alsamixer still shows my card as pcsp, nothing changed from post #3. Still shows AlsaMixer 1.0.15. chip = PC speaker. view = [Playback].

Sound works just dandy with my 7.10 LiveCD. :KS

---

### Post by cyberdork33 on 2008-07-31
Try loading the module manually:

```
sudo rmmod snd_hda_intel
sudo modprobe snd_hda_intel
```

---

### Post by baofeibo on 2008-07-31
There is probably something elementary I'm not doing, but when I do:
```

sudo rmmod snd_hda_intel

```

I get:```

ERROR: Module snd_hda_intel is in use

```

I wasn't running any other programs in the background.

---

