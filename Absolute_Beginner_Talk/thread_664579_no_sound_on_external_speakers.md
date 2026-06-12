---
title: "no sound on external speakers"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by erikw on 2008-01-11
I installed 7.10 on my acer extensa 5620z, but now I only have sound on the internal speakers from the notebook and not on the external speakers (they do work unther windows xp)
Also unther ALSA I only have buttons to regulate Master, PCM and Digital. I also installed 7.10 on a normal PC and there I have also buttons for speaker, .......etc and have sound on the external speakers there. What can I do or did I do wrong?

---

### Post by Arthur Archnix on 2008-01-11
It sounds like your line-out jack is not being detected properly. On my laptop the line-out jack does not disable the internal speakers by default when something is plugged in. Tweaks are often needed. You should post your audio card information and then we can search the forums to see if anyone else has the same card and has managed to solve your issue. You can find the sound card info by typing  in a terminal: ```
lspci | grep Audio
```

It would be helpful if you also posted the output of:
```
uname -r
```

---

### Post by erikw on 2008-01-12
I did as asked and found this on my system;

erik@erik-laptop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
erik@erik-laptop:~$ uname -r
2.6.22-14-generic
erik@erik-laptop:~$

---

### Post by doubleij on 2008-01-12
Hello,
I am running Gutsy 7.10 on my Acer 4315 and I have exactly the same issue. I checked my sound card and its identical to the one you described above. 

charity@charity-laptop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
charity@charity-laptop:~$ uname -r
2.6.22-14-generic

How can I fix this? I'm new to Ubuntu, but I played around with the sound mixer with no success.

---

### Post by Arthur Archnix on 2008-01-12
When I first got my laptop, Edgy had been out for a few months and getting sound to work was a pain. In Feisty it worked a treat right out of the box. You two happen to have a newer soundcard and support is just now getting built into ALSA. You can read about it here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130559](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/130559)

You'll find that people have been getting it working a few different ways. The first and simplest is just to enable the backports repository and use synaptic to install linux-backports-modules and then reboot. A second method is to add this to the end of /etc/modprobe.d/alsa-base.
```
options snd-hda-intel model=acer
```
Again, a reboot may be required. A third method is to install the latest ALSA drivers. A fellow called Richard gave some instructions on the link above. I've compiled and installed my own ALSA drivers before and it wasn't a fun time. I'd make sure you try the following thread before trying to build and install your own alsa drivers:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

The good news is that people are getting sound working with this audio card, the bad news is that a little extra work is required at this time. If you get involved with launchpad though and let people know what worked for you (if any of the above) that'll help make sure that things are fixed and working great right out of the box in time for hardy.

EDIT: A bit more detail...

**To enable backports in Gutsy**, in a terminal type:
```
gksudo gedit /etc/apt/sources.list
```
Then uncomment (remove the #) from the line that says
```
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```
You can see that I haven't uncommented mine, and that the location is a canadian server, but your's might be different. The important part is at the end, where it says gutsy-backports.

Save and close then do:
```
sudo apt-get update && sudo apt-get install linux-backports-modules

```Then reboot.

**To add sound options** to your setup do:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
Then add this to the bottom:
```
options snd-hda-intel model=acer
```
Save, close and reboot.

Better instructions on compiling Alsa can be found elsewhere, so I won't bother trying to duplicate that work.

---

### Post by Arthur Archnix on 2008-01-12
Stumbled across this and then thought of you two:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by nimbus2000 on 2008-01-13
I installed GG in an Acer Aspire recently. It didnt have sound eithre. I checked up on a post in this forum whioch told me to activiate sorround. now its working fine.

---

### Post by doubleij on 2008-01-13
Thanks Arthur Archnix,

I especially appreciate that you listed several ways to fix this issue. I don't mind doing small fixes on the computer (I didn't have a choice about which one I got, so I expected some out-of-the-box problems).

I need to ask some clarifying questions, though, since I'm new and I already was forced to do a fresh install (maybe I wasn't but I didn't know any other way to fix the problem) trying to implement the backports solution you mentioned here. In brief, importing the backports somehow disabled my soundcard and also destroyed my complicated wireless fix for my AR5006EG sound card.

See this thread for details on my crash and problems:
[http://ubuntuforums.org/showthread.php?t=665520](http://ubuntuforums.org/showthread.php?t=665520)

It's possible that I implemented the backports solution incorrectly (I followed a different how-to on some other thread) and that's what caused the problems. But even so, I would rather not implement a system-wide fix that could mess up my other fix for the wireless.

So based on this, a couple questions:

1. Is there any way that editing the modprobe.d/alsa file as you described would affect my wireless? I don't think so, since that file is specifically connected with the sound card. But I need to check, because after the backports fix I couldn't even reinstall the madwifi driver that I used to fix the wireless (as I recall, it gave me an error about not being able to access modprobe or something). That's when I decided I needed a fresh install.

2. I don't yet know how to back up my system in Ubuntu, and I want to learn to do that before I implement the solution, just in case! :) I've seen programs like Time Vault and Flyback talked about on the forums. Do you have a recommendation for a backup method? If so, could you point me to a good how-to for the method? I would need to be sure that the backup preserved my wireless fix (which is presumably in modprobe, though I don't have that computer in front of me).

Thanks in advance...

---

### Post by TheMouse on 2008-02-01
I'm also using an Acer 5620, same card as the above folks. This is my second time installing Ubuntu on this computer (this time, I've gotten rid of the Windows partition). I can't remember how I got my sound working last time.

I've tried the modprobe.d/alsa method and it didn't fix my sound. Not only that, but my wireless stopped working. Weird.

I already have the backport repositories up and going. No dice.

I can't remember how I got my sound working last time, but I can remember some details about it. When I open my volume control panel, there are only two slides, PCM and Master (same for opening alsamixer). The one detail that I recall is that the solution added a third sound control, one for the stereo jack. Anyone know how someone would do that?

---

### Post by doubleij on 2008-02-01
Hi TheMouse,
It sounds like you have the same problem I did on my Acer 4315. I think the wireless and sound must share some dependant files or something. I eventually solved the problem and posted the fix over here.
[http://ubuntuforums.org/showthread.php?t=665520](http://ubuntuforums.org/showthread.php?t=665520)
I hope it works for you!

---

### Post by TheMouse on 2008-02-02
Thank you, thank you. It worked like a charm.

---

