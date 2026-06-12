---
title: "No sound at all on new Gutsy installation - please help"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by therudeboyd on 2007-12-28
Hello
I've just installed Gutsy, I'm new to Linux. It took me 3 days to get the wifi working, now it seems there is no sound. Please point me in the direction of some steps I can follow to get the sound working.

 I've run alsamixer at the command, It seems to be recognising the soundcard (Card HD NVidia, Chipset Realtek ID 268). It's not muted as I've checked

I've read a previous post about a seemingly similar problem, but no resolution.
Don't know if the following helps:

 sudo lshw -C sound
[sudo] password for ptthuyen:
  *-multimedia            
       description: Audio device
       product: MCP67 High Definition Audio
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
ptthuyen@ptthuyen:~$ sudo apt-get install ubuntu-restricted extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted


HELP! PLEASE! I need my tunes!
Thanks

---

### Post by JoshuaRL on 2007-12-28
You might try this page:

[https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29%7C%28reconfigure%29](https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28sound%29%7C%28reconfigure%29)

Sorry, I don't have much personal experience with sound issues.  Hope that helps.

---

### Post by Casual Fan on 2007-12-28
> **therudeboyd said:**
> ptthuyen@ptthuyen:~$ sudo apt-get install **ubuntu-restricted extras**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package [B]ubuntu-restricted
[/B]

HELP! PLEASE! I need my tunes!
Thanks

The help thread posted above is excellent, BUT, in looking at what you've posted, I see one glaring error: it's "ubuntu-restricted-extras." You need the extra dash between "restricted" and "extras." You'll see that it's looking for a package called "ubuntu-restricted" which doesn't exist. :)

---

