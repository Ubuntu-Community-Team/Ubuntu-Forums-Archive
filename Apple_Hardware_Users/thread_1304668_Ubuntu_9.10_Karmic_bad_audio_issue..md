---
title: "Ubuntu 9.10 Karmic bad audio issue."
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by maffix on 2009-10-29
The new release Ubuntu Karmic Koala have no good audio configuration!:(

First issue.
Frequently I hear a strange sound from speakers like a bump!

Second issue.

When there's no rumor near me, from speakers I hear 	
continuously rumors, but if I move volume switch the rumor stop for 5 second and then starts again.:(

Maybe the new alsa driver do not works well?
I have tried all alsamixer settings without succes!

---

### Post by hotstepperk on 2009-10-30
same problem. its killing me!!!!!]  (*,)](*,)](*,)

---

### Post by rmcellig on 2009-10-30
Same here. I have 9.10 running in VMware Fusion 3. No audio at all. When I launch 9.04, everything is fine. What's going on?

---

### Post by maffix on 2009-10-30
I have tried Sabayon 5 Gnome 64 bit, no bump sound, but the same problem about persistent rumor coming out of the speaker!:(

I think that new alsa driver do not works well with new kernel 2.6.31!

---

### Post by hanzomon4 on 2009-10-30
What is rumor?

---

### Post by rmcellig on 2009-10-30
I was wondering that too. What is rumor?

---

### Post by dharmagio on 2009-11-02
that static sound or rumour you refer
is because of the cd drive that is not muted
check for micro too.

because this new 9.10 lacks in having a decent
audio mixer there is no way to mute it at least far
as i know.

i wood like to know how can i mute it.
and by the way, this new sound mixer is very bad,
its confusing and lacks on options.
try to program and design simple and u get better
results, a simple horizontal sound mixer is what we need!

---

### Post by Leechow on 2009-11-02
try this:
from within **synaptic** specify *complete remove "PulseAudio"* with configuration files.

check this page: [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

it solves my problem while the music played on my system was quite noisy.

---

### Post by maffix on 2009-11-02
@rmcellig and hanzomon4

rumor=silence

I have partially solved the bump noise disabling theme sound on  Audio preferences.

---

### Post by ell02 on 2009-11-02
[http://ubuntuforums.org/showthread.php?p=8043003](http://ubuntuforums.org/showthread.php?p=8043003)

Look at this before removing pulse.

---

### Post by Leechow on 2009-11-02
yea, i notice that after remove "PulseAudio", the system sound disappear. and the volume adjust icon on the panel also missing. 

so problem still, if i reactive "PulseAudio" , when i play mp3 files with music player, the sounds becomes noisy. (when place cursor on mp3 file, the music plays well.)

:|

---

### Post by Gp. on 2009-11-02
Same issue here (I think).
FRUSTRATING!

They finally fixed the Softreset bug for my motherboard in 9.10 and now theres audio issues. Giving up on ubuntu AGAIN.

---

### Post by efes50cl on 2009-11-02
Same problem here some help pleaseeeee. It drives me nuts

---

### Post by ngine13 on 2009-11-02
Guys i had the same problem..

There are two ways to solve this :

1. Edit the file /etc/modprobe.d/alsa-base.conf and comment the last line :

#options snd-hda-intel power_save=10 power_save_controller=N


or you can 


2. set a much greater value for power_save like :

options snd-hda-intel power_save=900 power_save_controller=N


and you are done! ;)

---

### Post by Gp. on 2009-11-02
ngine13 is correct.

If you need further help, it's here: 
[http://ubuntuforums.org/showthread.php?p=8227911](http://ubuntuforums.org/showthread.php?p=8227911)

---

### Post by Leechow on 2009-11-03
> **ngine13 said:**
> 
1. Edit the file /etc/modprobe.d/alsa-base.conf and comment the last line :

#options snd-hda-intel power_save=10 power_save_controller=N



I'm running G4 which is not on intel processer, is it affect?
I made the change as you said, but problem still there...

---

### Post by crjackson on 2009-11-04
I spent an hour or so looking in to this tonight.  I found that if you install the proprietary modem driver, OFTEN (but not always) the modem grabs audio control before the sound chip.  Removing the driver will solve the issue if this is YOUR problem, however it may take a couple of COLD reboots (power off / on) before things start to work perfectly.

It disappoints me a little that I can't enable the modem, but I've never actually used it anyway and I can always dual boot to windows.

I REALLY hate to say this, BUT...  Windows is MUCH better at handling dial-up modems.  I'll probably get flamed, but it just is.

Any one who's had to STRUGGLE with WVDIAL would probably agree.  WVDIAL works great for some.  Others...  Not so much.

---

### Post by dharmagio on 2009-11-06
I have this problem with this static and noises i listen in my ubuntu 9.10
like i said before, i think if we can reach the mixer specifications
we can mute some inputs, like the cd drive input that always make some noise.

---

