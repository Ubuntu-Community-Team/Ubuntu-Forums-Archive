---
title: "No sound!"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by diaz028 on 2008-03-01
I am on a Acer Aspire laptop, and I do not get soud at all. All volumes are maxed out. Running 7.10 gutsy fresh install.

Would automatix fix that? Or some gui software?

thanks

-D

---

### Post by PmDematagoda on 2008-03-01
I would not really recommend Automatix at the moment since it has a history of causing crashes and other problems on Ubuntu systems.

Could you please post the full specifications of your PC(Most specifically the sound card).

---

### Post by diaz028 on 2008-03-02
how do i find my sound card name?

-D

---

### Post by Straywolf on 2008-03-02
I got an acer aspire laptop as well and I had the same problem. I was able to fix it by right clicking on the volume icon and click "open volume control" I found that the settings were turned off. Hope this helps.

---

### Post by diaz028 on 2008-03-02
It is an Acer Aspire 7720 with Intal HDA sound. 

Cant get any sound at all!

-D

---

### Post by ferdostar on 2008-03-02
Can you please post the output of ```
sudo lshw -C sound
```

---

### Post by diaz028 on 2008-03-02
>   *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel


I installed the new 1.0.16 driver (alsa-driver) from alsa-project. compiled and installed, no sound still.
Also did the firmware

-D

---

### Post by ferdostar on 2008-03-02
Did you check if everything with the alsamixer is ok? Everything should be on? ```
alsamixer
```

---

### Post by diaz028 on 2008-03-02
EIC958 says MM

---

### Post by ferdostar on 2008-03-02
Check this [https://bugs.launchpad.net/ubuntu/+bug/122560](https://bugs.launchpad.net/ubuntu/+bug/122560) 
In fact you should install a script, go here [http://ubuntuforums.org/showthread.php?p=4349687](http://ubuntuforums.org/showthread.php?p=4349687)

---

### Post by diaz028 on 2008-03-02
Installed the script, didn't work. I'm at wit's end here... Thanks alot for support man! Any other ideas?

-D

---

### Post by ferdostar on 2008-03-02
In fact you can try to compiling the alsa-driver for your sound card
Otherwise you can take a look of others similar posts to see if someone else had the same problem as you:
[http://ubuntuforums.org/showthread.php?t=616846](http://ubuntuforums.org/showthread.php?t=616846)
[http://ubuntuforums.org/showthread.php?t=604084](http://ubuntuforums.org/showthread.php?t=604084)
[http://ubuntuforums.org/showthread.php?t=569280](http://ubuntuforums.org/showthread.php?t=569280)
[http://ubuntuforums.org/showthread.p...light=no+sound](http://ubuntuforums.org/showthread.p...light=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php...21&postcount=5](http://ubuntuforums.org/showpost.php...21&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.p...olutions+guide](http://ubuntuforums.org/showthread.p...olutions+guide)
[https://help.ubuntu.com/community/De...gSoundProblems](https://help.ubuntu.com/community/De...gSoundProblems)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://linuxtechie.wordpress.com/200...work-in-gutsy/](http://linuxtechie.wordpress.com/200...work-in-gutsy/)
[http://linuxtechie.wordpress.com/200...tsy/#comment-6](http://linuxtechie.wordpress.com/200...tsy/#comment-6)
[https://bugs.launchpad.net/ubuntu/+s...22/+bug/136469](https://bugs.launchpad.net/ubuntu/+s...22/+bug/136469)

On the other hand, not sure but you can try to 
1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above. :)

Post if you have an issue ;)

---

### Post by diaz028 on 2008-03-02
Tried running hardy 8.03a live and still nothing... 
Thanks for help!:)

-D

---

### Post by diaz028 on 2008-03-02
How do I access the file "alsa-base" with write permissions?

-D

---

### Post by bldgengineer on 2008-03-02
Try the instructions here:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

They really helped me out with the same issue. Read the instructions carefully and make sure you know which kernel you have. After you are done reboot and make sure your volume is up enough to hear sound.

---

### Post by diaz028 on 2008-03-02
> **bldgengineer said:**
> Try the instructions here:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

They really helped me out with the same issue. Read the instructions carefully and make sure you know which kernel you have. After you are done reboot and make sure your volume is up enough to hear sound.

Already tried, no go.. .thanks though!

-D

---

### Post by diaz028 on 2008-03-02
SOLVED:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

sudo gedit alsa-base

-> add

options snd-hda-intel model=acer

Everything works perfect now... 

-D

---

### Post by ferdostar on 2008-03-03
Great, just mark the thread as solved ;)

---

