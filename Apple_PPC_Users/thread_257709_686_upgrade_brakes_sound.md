---
title: "686 upgrade brakes sound"
date: 2006-09-14
forum: Apple PPC Users
---

### Post by rscow on 2006-09-14
Like a fool, I elected to use the automatic update feature, and updated my kernel (currently using  2.6.15-26-686 #1 SMP) to the .47 version.

Now my sound is broken.

How do I fix?  I'm triple booting my MacBook and boot via LILO.  Is there a key combination to use when starting LILO that will allow me to select the old kernel image?

ROger

---

### Post by hajk on 2006-09-15
As far as I know, the 47-image upgrade replaced the previous one in the /boot directory, so there is no LILO choice here.
Apart from trying to fix sound with this new version, you could always downgrade to the previous 46-image, it may be in your /var/cache/apt/archives directory, or you may download it from the repositories.

---

### Post by moore.bryan on 2006-09-15
*reinstalling alsa seems to have worked for some...*

---

### Post by jfmbp on 2006-09-15
For me (Macbook pro 15.4) this upgrade breaks cpu frequency scaling too ... (speedstep_centrino module fail to load).

Sep 15 21:28:36 localhost kernel: [17179590.776000] speedstep_centrino: Unknown symbol cpu_data
Sep 15 21:41:36 localhost kernel: [17179591.948000] speedstep_centrino: Unknown symbol cpu_data
Sep 15 21:49:16 localhost kernel: [17180053.336000] speedstep_centrino: disagrees about version of symbol cpu_data



I had to downgrade to the previous 46-image ;-(

---

### Post by rscow on 2006-09-15
Well, a reinstall of ALSA didn't work.  I do have the 46 image package receipt thing in my /var/cache/apt/archives.  Apt won't let me install since it isn't the latest.  Neither will Synaptic.  I will have to look at man apt I guess for help...unless some guru out there knows the right commands.

Thanks, Hajk

> **hajk said:**
> As far as I know, the 47-image upgrade replaced the previous one in the /boot directory, so there is no LILO choice here.
Apart from trying to fix sound with this new version, you could always downgrade to the previous 46-image, it may be in your /var/cache/apt/archives directory, or you may download it from the repositories.

---

### Post by rscow on 2006-09-15
I got my .46 image back.

What I did was use dpkg -i and point toward the package in /var/cache/apt/archives

This successfully downgraded my kernel image.

The automatic update app wants me to go back to .47.  Not today.

In Synaptic, I clicked the "lock" pull down.  I don't know if this causes a problem, but I don't want to update until I know more about what the changes will do.

Thanks, again, Hajk

---

### Post by spacefizzicist on 2006-09-17
Sound in my Latitude D610 is broken too! Aaargh, it's a pain in the rear end when you have to deal with such issues after an "UP"grade! Will this be fixed and a new release (kernel image/restricted-modules whatever) will be out soon? Besides, is there a place to check what are the changes in the upgrade and the possible side effects after such an upgrade? I don't know what to do. If it is going to be fixed, I don't mind waiting for a day... But I can't listen to the sound of silence for long! Any "uber" package developers/users/whoever out there, please let me know!
```
$dpkg --list linux-image* 
ii  linux-image-2.6.15-26-686 2.6.15-26.47              Linux kernel image for version 2.6.15 on PPro/Celeron/PII/PIII/PIV


```

the sound card is:

```

$lspci|grep audio

0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

```
and the modules loaded are:
```

$lsmod |grep snd

snd_intel8x0           35772  3
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  2 snd_pcm
snd                    60004  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm

```  
---
Is downgrading the image to version 46, my only option? I did a
```
$ sudo apt-get install --reinstall alsa 
```

and didn't solve anything. Please help/let me know what to do. I don't want to spend lots of time which btw, I don't have for debugging/compiling packages and such - for now.. Thanks in advance.

---

### Post by frigaut on 2006-09-17
rscow: thanks for the suggestion. I also had sound and frequency scaling broken by 47.
I downgraded to the 46 image (using 686, with smp enabled as a lilo parameter).

Shouldn't we also have to downgrade other packages? like the linux-header or the restricted drivers?

Added: forgot to mention this downgrade fixed the frequency scaling, but somehow not the sound. I re-installed alsa in between. That probably explains it.

---

### Post by jfmbp on 2006-09-17
to downgrade :

> cd /var/cache/apt/archives/
sudo dpkg -i linux-restricted-modules-2.6.15-26-686_2.6.15.11-3_i386.deb 
sudo dpkg -i linux-headers-2.6.15-26-686_2.6.15-26.46_i386.deb 
sudo dpkg -i linux-image-2.6.15-26-686_2.6.15-26.46_i386.deb

---

### Post by spacefizzicist on 2006-09-18
Well, FWIW, I could get sound to work with the latest kernel upgrade which was causing problems.. i.e.,  with linux-restricted-modules-2.6.15-26-686_2.6.15.11-4_i386.deb, linux-headers-2.6.15-26_2.6.15-26.47_i386.deb, and linux-image-2.6.15-26-686_2.6.15-26.47_i386.deb

Version 46 was not available in my /var/cache/apt/archives and I don't remember doing apt-get clean either.. anyways, I couldn't find the older (46) versions of these packages in security.ubuntu.org/<path to the location of i386 deb files> So I figured I'd wait for the next upgrade and was playing around with alsamixer..

 All I did was to turn the "PCM Out" option in alsamixer to post 3D (3D sound) and now I could get sound working and that too much better quality (3D)..WEIRD! :o Dunno if it's Inel ICH6 AC'97 card specific or whether the kernel upgrade turned off/on any previous settings..I like cooking my own kernel, but for lack of time.. anyways, for those who had the same experience I thought maybe this might be worth a try..YMMV..Goodluck!

---

### Post by rscow on 2006-09-18
I'll take a peek at Alsa-Mixer settings.  I've already downgraded, and supposedly a new update is in the works, but it doesn't hurt to improve the sound quality.  Mine is kind of quiet and flat.

RDS

---

