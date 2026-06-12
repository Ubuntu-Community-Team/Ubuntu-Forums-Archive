---
title: "xorg.conf help needed on Lubuntu 12.10 G4 nVidia"
date: 2012-10-03
forum: Apple Hardware Users
---

### Post by wxl on 2012-10-03
So I have a PowerBook G4 12" 1.5" GHz I'm trying to get to work with Lubuntu 12.10. Here's info on the card:
```
$ lspci | grep VGA
0000:00:10.0 VGA compatible controller: NVIDIA Corporation NV34M [GeForce FX Go5200] (rev a1)
```

Whether or not I use a live cd or a whole install, X doesn't start and I get "no devices detected" from /var/log/Xorg.0.log (more [here]("http://paste.ubuntu.com/1254953/")) unless I turn off Kernel Mode Setting (KMS) à la nomodeset/nouveau.modeset=0 boot parameters which get me this really funky display (see [here]("http://imgur.com/ArhrV")).

So I'm trying to step back and RTFM manual for once. I'm going through the PowerPCFAQ and there's instructions to create an xorg.conf. I did the auto-configure, added a modeline, removed unnecessary bits, and got rid of the other outputs (found in /sys/class/drm) to reduce the likelihood of problems with phantom outputs.

The end result is I get a reasonable looking display. There's only one caveat: all of the windows are blank. The colors are right, but they're blank (see [here]("http://imagebin.org/230781") for a pic). I'm sure there's an easy fix to this but the FAQ doesn't necessarily steer me in the right direction and I had to go to bed before I could get through the xorg.conf man page :) So I'm hoping someone has an easy answer.

For reference, nouveau's output on dmesg, Xorg.0.log, and xorg.conf are all included [here]("http://paste.ubuntu.com/1258602/").

Thanks in advance!

wxl

---

### Post by rsavage on 2012-10-03
Wow that is one messed up display! I don't think it is a phantom output problem, but if you want to double check then you can also disable the other outputs you don't use at the yaboot prompt.
 
Have you tried disabling acceleration?
```

Linux nouveau.noaccel=1

```
 
Or you can do it in your xorg.conf.
```

Option     "NoAccel"      "true"

```
 
Or 
```

Option "EXANoComposite" "true"

```
 
Have you tried using the fbdev driver? Just replace the 
```

Driver      "nouveau"

```
with 
```

Driver "fbdev"

```
 
Btw, you shouldn't need that modeline that you've addded.

---

### Post by rsavage on 2012-10-03
Basically nouveau and your card seems to have been in a bad way for a while now according to this fedora bug report [https://bugzilla.redhat.com/show_bug.cgi?id=745202](https://bugzilla.redhat.com/show_bug.cgi?id=745202) . It seems it is worse in an 3d accelerated environment such as gnome-shell, so I'm not sure why you get it so bad in lubuntu. The bug report talks of blacklisting and I wonder if something like that has gone off in Ubuntu and that is why you have had to define your own xorg.conf to load nouveau.
 
EDIT: Unity blacklists your card too [https://bugs.launchpad.net/ubuntu/+source/nux/+bug/769402](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/769402) , but that (*I think*) doesn't explain why you had to define an xorg.conf.

---

### Post by wxl on 2012-10-04
you are the man!

turning 3rd acceleration off was on my list of things to try if no one got back to me and it did the trick, both from yaboot and from xorg.conf (I admit to not trying the EXA option, though). I also deleted the modeline, the input/output specifics, and anything else unnecessary. works great.

i did try fbdev with no similar or better results. can't recommend that.

i have a working battery monitor now that i added pmu_battery to /etc/modules.

i need to tweak my trackpad, but that's my own gripe. i'll figure it out after studying mousemu.

sound is not working but i have this sneaking little suspicion there may be something amiss with 12.10. arild posted to the lubuntu-qa mailing list and i was in the process of replying back my findings there about missing files and what not when i had my big problem.

this has been a problem i've had with every single ppc distro with the exception of mintppc. i tried to figure out why and frankly i couldn't. after reading the powerpcfaq clearly, maybe now i can get down to the bottom of this.

so i had xxxterm, sylpheed, and lxterminal (running tmux and within it ssh, and a couple bashes) running and the fan's running. no big surprise there. can tweak that. suddenly, shut down. so clearly, something needs to happen with regards to frequency scaling.  i can't think of any other explanation.

seems like, reading the faq, i have some more work to do to figure that out, but if you have any additional info to confer, i'm all ears!

meanwhile, thanks a ton for the help!

---

### Post by wxl on 2012-10-04
bug report to hopefully get xorg.conf in for next time; includes xorg.conf:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1061790](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1061790)

---

### Post by rsavage on 2012-10-04
Mintppc is just debian.  Please don't be fooled.  Debian still has the legacy framebuffers built in.  Last time I checked this was still the case even in wheezy.  So you probably wouldn't have booted into nouveau, but nv in debian squeeze or the fbdev driver in debian wheezy.
 
Sound has been a recurring problem for a while now, caused by somebody trying to be clever blacklisting modules.  See the FAQ, I'm sure the answer will be there, although sound modules did have changes in 12.10 (see powerpc kernel developers list).
 
I think there is something wrong with your computer regarding the heat/fan/frequency scaling problem.  If your fan is on then it is being cooled and so why would it shut-down through heat?  Makes no sense (unless the fan is at too low a speed), hence I think it is a fault with your actual computer.  Sorry.  I haven't heard of anybody else with your problem.  One of the biggest sources of heat can be the hard drive so you could try reducing the hdparm settings?

---

### Post by rsavage on 2012-10-04
Just to add about the battery module, you (lubuntu-qa) all moaned about it last time (12.04) and I wrote a patch to fix it.  I asked for testers to try it out (it was just a script to run) and not a single person did.  Hence, you have to add your battery module yourself.

---

### Post by wxl on 2012-10-04
oh don't sweat the battery. i just followed the instructions in the powerpcfaq. whoever put that together knew what they were talking about :)

can you say
```
echo "pmu_battery" | sudo tee -a /etc/modules
sudo modprobe pmu_battery
```
? :)

re: sound, i saw that. going to go through it and see what's going on.

re: heat/whatever, i can tell you i didn't have the problem with os x nor did i have the problem with mintppc (which i became interested mainly because i wanted to figure out what it was doing so not have that problem happen with lubuntu), nor did i have it a long time ago with archppc. or xubuntu. i think it's unlikely (but possible) the problem is with the machine.

anyways the notes above were just an fyi. when i have had a chance to go through the ppcfaq (which has been most helpful) i'll ask more directed questions as i have them.

thanks again for the help.

---

### Post by wxl on 2012-10-04
re: sound the problems continue. no device in lspci which is, as you know, bad news. 

until that's fixed, none of this is really very relevant but: snd-powermac is in /etc/modules. looked for /etc/modprobe.d/blacklist.local.conf and nothing but instead we have:
```
$ ls /etc/modprobe.d/
alsa-base.conf           blacklist-framebuffer.conf  blacklist-rare-network.conf 
blacklist-ath_pci.conf   blacklist.local.conf        blacklist-watchdog.conf 
blacklist.conf           blacklist-modem.conf        iwlwifi.conf
blacklist-firewire.conf  blacklist-oss.conf          libpisock9.conf 
```

i can't even find anywhere that lists what card it is to figure out whether or not it is supported or what driver is appropriate.

going to try a livecd and see if there's the same problems.

---

### Post by wxl on 2012-10-04
no luck with audio on the live cd. seems like we've got a much lower-level bug than previously thought:
[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1060452](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1060452)

---

### Post by rsavage on 2012-10-05
I don't mean to sound too rude, but lubuntu-qa have form for not reading documentation properly!!! I'm not pressing the panic button yet.
 
Snd_powermac is force loaded (twice) in /etc/modules so remove this is you don't have that kind of card. You do have a blacklist.local.conf file listed and I bet it contains sound modules so remove that file or the sound module contents.
 
There will be four possible combinations of sound modules. It is simply a case of researching if the sound module names have changed (look at the PowerPC kernel developers list as I know work has been done on them) and trying each combination if the autoloading is not working properly.

---

