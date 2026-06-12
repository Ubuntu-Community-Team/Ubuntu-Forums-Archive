---
title: "Sound is very quiet"
date: 2007-05-19
forum: Apple Intel Users
---

### Post by wootwoot123 on 2007-05-19
The sound on my macbook is next to nothing. I have the volume all the way up and have it all the way up under System->Prefs->Sound but I can still  barely hear anything. I have no problems under OSX or XP but in linux the sound is very faint. What should I check?

---

### Post by Gen2ly on 2007-05-19
> **wootwoot123 said:**
> The sound on my macbook is next to nothing. I have the volume all the way up and have it all the way up under System->Prefs->Sound but I can still  barely hear anything. I have no problems under OSX or XP but in linux the sound is very faint. What should I check?

Hi there woot.  Dallying with alsamixer should fix it just type it in the command line.

---

### Post by ronocdh on 2007-05-19
> **Dirk.R.Gently said:**
> Hi there woot.  Dallying with alsamixer should fix it just type it in the command line.
This will probably fix it, but keep in mind that your system could be by default talking to the soundcard in the wrong way. I know that I had to change the settings in the Sound pref pane before my volume keys worked and such, so this means that moving the slider bar all the way up may not actually be increasing your volume any.

Anyway, please post back with your results with alsamixer. I think it should tidy you up nicely.

---

### Post by felixdzerzhinsky on 2007-05-20
I am having the same problem.

Alsamixer:

 Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ALC885                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Front [dB gain=0.00, 0.00] 

I notice there is nothing under PCM. Everything else has green '00's.

---

### Post by felixdzerzhinsky on 2007-05-20
In my case the sound works fine on my Ubuntu running in Parallels virtualisation. It is just this hard drive install that is problematic. Punk music just doesn't sound right when it is quiet!

---

### Post by felixdzerzhinsky on 2007-05-20
In my case the sound works fine on my Ubuntu running in Parallels virtualisation. It is just this hard drive install that is problematic. Punk and metal music just doesn't sound right when it is quiet! 

\m/


More info:


pjharper@reno:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

pjharper@reno:~$  lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Realtek Semiconductor Co., Ltd. Unknown device 0885
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at 4a400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by felixdzerzhinsky on 2007-05-20
The PCM doesn't have anything under it. Is that the problem?

---

### Post by nicfagn on 2007-05-20
> **felixdzerzhinsky said:**
> The PCM doesn't have anything under it. Is that the problem?

No. The problem is that your alsa version does not support the realtek ALC885 subsystem.
A patch for macpro models has been included in alsa-driver-1.0.14rc4 and with a little configuration can be used to get sound from speakers on an iMac 24'' (and probably on others iMac Core 2 Duo). Playing with alsamixer you can even record sound :)
You can find instructions on how to take advantage of this [here]("http://ubuntuforums.org/showpost.php?p=2549232&postcount=13").
If you want to track the official solution to the problem you can check:

[INDENT][https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/111511]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/111511")[/INDENT]

and:

[INDENT][https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2708]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2708")[/INDENT]
(login as guest)
By the way, version 1.0.14 rc4 of alsa drivers includes fixes for many Mac models (see [here]("http://www.alsa-project.org/changes/v1-0-14rc3--v1-0-14rc4.txt") and search for mac), so anyone having problem with sound can try to compile and install them.

Bye

---

### Post by wootwoot123 on 2007-05-20
> **nicfagn said:**
> No. The problem is that your alsa version does not support the realtek ALC885 subsystem.
A patch for macpro models has been included in alsa-driver-1.0.14rc4 and with a little configuration can be used to get sound from speakers on an iMac 24'' (and probably on others iMac Core 2 Duo). Playing with alsamixer you can even record sound :)
You can find instructions on how to take advantage of this [here]("http://ubuntuforums.org/showpost.php?p=2549232&postcount=13").
If you want to track the official solution to the problem you can check:

[INDENT][https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/111511]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/111511")[/INDENT]

and:

[INDENT][https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2708]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2708")[/INDENT]
(login as guest)
By the way, version 1.0.14 rc4 of alsa drivers includes fixes for many Mac models (see [here]("http://www.alsa-project.org/changes/v1-0-14rc3--v1-0-14rc4.txt") and search for mac), so anyone having problem with sound can try to compile and install them.

Bye

That is completely wrong. If there is nothing under PCM you will hear nothing. I appreciate the quick answers, my PCM was low so my volume was low. After I made the adjustment to PCM my volume got louder.

---

### Post by felixdzerzhinsky on 2007-05-20
What I don't understand is how I can have Dapper running in virtualisation (parellels) with the sound fully working.


It seems to have only happened when I installed Feisty to the hard drive.  Is this going to be a case where I just have to wait until a new kernel or alsa comes out?

---

### Post by nicfagn on 2007-05-21
> **felixdzerzhinsky said:**
> What I don't understand is how I can have Dapper running in virtualisation (parellels) with the sound fully working.


It seems to have only happened when I installed Feisty to the hard drive.  Is this going to be a case where I just have to wait until a new kernel or alsa comes out?

When you run Dapper on Paralles (or Fusion), the VM environment make it see a virtual sound card whose type is correctly detected. 
In contrast, when you run Dapper on bare metal it sees the physical sound card directly. That sound card is certainly different from the virtual one, hence the different behaviour if the physical card is not supported.
I had the same problem on a iMac 24'' with Feisty, and I hope that it will be supported by the alsa libraries delivered with Gutsy in October.
If you don't mind to get your hands dirty, you can do what I suggested in my previous post.

Good luck ;)

---

### Post by aldeluis on 2007-06-12
> **wootwoot123 said:**
> That is completely wrong. If there is nothing under PCM you will hear nothing. I appreciate the quick answers, my PCM was low so my volume was low. After I made the adjustment to PCM my volume got louder.

Hi wootwoot123,
how do you put something under PCM in alsamixer?

---

### Post by aCiD2 on 2008-01-06
I'd just like to add my 2 cents. While I did have both pcm and master set to 0dB, front was set to -17dB. Putting front back to 0dB seems to have fixed the problem (and position-fix=1 solved my crackling issues :))

---

