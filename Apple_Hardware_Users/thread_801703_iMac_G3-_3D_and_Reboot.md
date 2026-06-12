---
title: "iMac G3- 3D and Reboot"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by Phonan on 2008-05-20
I'm so far really liking this- I installed Xubuntu 7.10 on an old iMac G3 a while ago after trying Linux with another, self-made computer. I was having Internet problems so I reinstalled 7.10, then used my (now working) USB Wireless to upgrade to Xubuntu 8.0.4 PPC. Everything so far works, and I just have two more questions because I'm greedy.:)

First, I somehow have an endless reboot problem. Whenever I tell Xubuntu to shut down, it does so fine... and then starts up again. Normally I just unplug the iMac, but when the reboot does continue, the screen has crazy colors, inversions, grainy purple-ness, etc and so I try not to let it do so. It's been a long time since I've last used this, but I seem to remember that toward the end of its days with Mac OS 9 this may have occurred, so maybe its an artifact of age. However, if anyone does know how to help advice would be appreciated.

Second, and this is where the greed comes in, I'm loving all my software, but I remember, I believe, much better 3D on Mac OS 9. I've looked this up a bit, and it seems like 3D drivers for Ubuntu PPC do not grow on trees. I figured the forum would be a good place to look for help to see if I can get my 3D going, as it would be nice to say get to the level where a program like Scorched 3D for example is actually usable. Some specs if they help, pulled from lshw-
CPU- 400 MHz PPC
Memory- 192 MB SDRAM
Graphics- ATI Rage 128 RL/VR AGP
HD- 10 GB ATA
So if the drivers that Xubuntu loaded automatically are the best I can use, that's fine with me- like I said, I'm just being greedy here. But if I can squeeze any more 3D out that I've been missing, it'd be great if you could help.

Thanks.

---

### Post by stream303 on 2008-05-20
> **Phonan said:**
> Normally I just unplug the iMac, but when the reboot does continue, the screen has crazy colors, inversions, grainy purple-ness, etc and so I try not to let it do so.

I can't say for sure why the crazy reboots instead of a clean shutdown, but can you back out of x with ctrl-alt-backspace, and then try a clean shutdown from the terminal:

```
sudo shutdown -h now
```

It might be interesting to see if passing a kernel parameter at the second-stage boot: prompt helps to get rid of the funky splash screen and allow you to see the dmesg roll by instead:

At the second-stage of yaboot, hit -tab- to stop the countdown.  Then try:
```
Linux nosplash
```

If that works, you can make it permanent in yaboot.conf...

As for your machine, it looks to be a 2X AGP card, and there are a few tweaks you can make to your /etc/X11/xorg.conf file:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

Although with Hardy's autoconfigured X, you might want to look at your /var/log/Xorg.0.log file to see what it picked up, and if any mods you make to xorg.conf are being accepted.

Which machine are you running?  Seems to be four 400mhz iMacs..
[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Congrats on the upgrade.  You are the first person I have heard that has done this successfully from Gutsy.

---

### Post by Phonan on 2008-05-24
Thanks very much for the replies, and sorry for the long wait. 

First, the graphics card. Thank you very much for the 2X AGP advice- I read about modifying but had no idea about my AGP speed. I've made the changes in xorg.conf. One question, though. glxinfo shows me "direct rendering: off." Should this be happening on my machine? If not, how should I change it? By the way, the machine I'm runnning seems most like the first on the list you showed: [http://www.everymac.com/systems/apple/imac/stats/imac_dv_400.html](http://www.everymac.com/systems/apple/imac/stats/imac_dv_400.html)

Also, the rebooting advice. I just keep getting the feeling that this is something deep down- maybe hardware, it is a very old mac. I will try what you've suggested; however, even in yaboot, from the very start after I shut down, I get purple lines all over my screen. Strangely, this never happens when I call for a reboot- everything goes normally. I'll tell you how stuff goes without X- the main thing I'm trying to do here is get my computer to stay off when I shut it down- currently I have to wait until it "zombie reboots" and then pull the plug or hold the power button until it dies.

Thanks for the congratulations on Hardy. Unfortunately, I don't have too much advice or useful information to everyone else trying to upgrade (if there is much of an "everyone else.") I simply installed Gutsy from scratch (since it had been getting messed up earlier) and then went straight to Hardy after configuring wireless. I doubt that will help anyone, but a clean install of Gutsy, then an upgrade is what worked for me. Thank you very much, stream303 for the advice- I'm off to mess with rebooting.

---

### Post by stream303 on 2008-05-24
> **Phonan said:**
> One question, though. glxinfo shows me "direct rendering: off." Should this be happening on my machine?

I believe to operate properly, the G3 needs direct rendering dri off, which limits us to 2D, but definitely try all those tweaks in the powerpcfaq:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

> Also, the rebooting advice. I just keep getting the feeling that this is something deep down- maybe hardware, it is a very old mac.

Something is weird somewhere.  Have you updated yourself to the latest software either via synaptic, or at the commandline with

```
sudo apt-get update
then
sudo apt-get upgrade
```

> I have to wait until it "zombie reboots" and then pull the plug or hold the power button until it dies.

Thank goodness for journaling filesystems. :)  In the meantime, does backing out of X with CTRL-ALT-Backspace and then issuing a shutdown with

```
sudo shutdown -h now
```

still not shutdown cleanly?

Be sure to see this addition faq - especially in regards to the module section:
[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

> Unfortunately, I don't have too much advice or useful information to everyone else trying to upgrade (if there is much of an "everyone else.")

Think again. :)  There are plenty of lurkers probably going through exactly what you are going through right now and watching your progress with interest.  So what we do is not just for the active members in the forum, but the ppc community as a whole.  You may think you have nothing to contribute, but mere participation in the process at this point is good enough!

The biggest hurdle sometimes is not to get too frustrated.  Without a challenge, we might as well just go "shrink-wrap" and call it a day. :)

---

### Post by Phonan on 2008-05-25
> **stream303 said:**
> I believe to operate properly, the G3 needs direct rendering dri off, which limits us to 2D, but definitely try all those tweaks in the powerpcfaq:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)


All right, I think I've done all possible for the drivers; I'll now get working on this endless reboot thing. Quite honestly, I have the system working quite to my liking, so the reboot is all that's left. I'll try some shutting down and see if anything works.

---

### Post by stream303 on 2008-05-25
I once had a weird problem with gdm and reboots that was solved with

```
sudo dpkg-reconfigure gdm
```

But that's just me - can't say for sure that this would prove useful in your case.

Btw, you may want to download HTOP in either synaptic or a *sudo apt-get install htop* and take a peek at what the system is doing.  I really like running htop in a terminal after an install.

---

### Post by Phonan on 2008-05-31
I'm really sorry to suddenly make a change like this to make it even harder to help, but I wanted more speed on my system (which is hard to get with a 400 mHz processor) so I did a command-line install and used apt to install fvwm-crystal. I couldn't start x until I moved over my old Xorg.conf (thank goodness I installed my old system from 7.10; the new bulletproof X is killing me,) so I've got my graphical tweaks carried over. The problem that *still* remains, through reformat, reinstall, shutdown -h now, and everything is my strange zombie reboots. I will install this HTOP and try it out; now the GDM change won't work, as I have no GDM installed... If the reboot is all I have to live with, I will be okay with it. But in hopes that my experiences can help someone, I'll keep trying to fix this. Thanks.

and EDIT: Just tried HTOP, and man is it better than top (just caught that.) What sort of process do you think I should look for? I don't see anything taking abnormal amounts of CPU or memory (except Firefox!)

---

### Post by stream303 on 2008-05-31
Ok, do the zombie reboots only happen when you have X11 running, or does it happen randomly with just the commandline too?

Just for grins, maybe post your /etc/X11/xorg.conf file

I wonder if maybe you are driving the system with some weird resolution freqs making the system unstable just at the very edge..

While you're at the commandline, maybe treat yourself to the elinks web browser, (ubuntu forums are usable with a little practice!) and possibly vorbis-tools to get ogg123 going to listen to audio streams and see if you are still experiencing random reboots there as well.  Alsamixer will do nicely for volume control. (I usually put it into another virtual terminal, ala ctrl-alt-f2 for example)

Listen to some interesting audio:
```
ogg123 -b128 http://radio.hbr1.com:19800/ambient.ogg
```

Alsamixer for audio levels  (left-right, up-down, b for balance, m for mute/unmute, esc to quit

This might help track down the reboot problem to see if it only happens in the gui, or at the commandline too.  I wonder if you have 3rd-party ram that might not be quite up to apple specs....

---

### Post by Phonan on 2008-06-01
Well I've had the problem both when I used a Xubuntu install previously and now. Now, as I don't have GDM, KDM, or XDM installed, I have always been shutting off from the command line, and I have this same reboot cycle. I do have elinks on the command line, no audio tools or anything. Do you think I should hang out there a while, for an entire session on the computer and see what happens with power off? Also, xorg.conf is coming up in a bit. Thanks.

Oh and by the way, the ram is, as far as I know, same as when the computer came from Apple way back when. I'll make sure, but I believe this is Apple RAM (were they still ripping people off for memory back in the G3 era?)

---

### Post by stream303 on 2008-06-02
You might also try resetting the pmu (power management unit).  On the G3 iMac, I believe it is the S1 button just to the southwest corner of the lower ram chip.  From what I remember, I think you are warned to ONLY push it once, as any multiple pushes can confuse the chip.

You might have to reset the date or other variables.  Note that I have never done this myself, maybe search a bit for G3 iMac pmu reset.  Caveat emptor!

---

### Post by Phonan on 2008-06-03
I've been looking at resetting the PMU, haven't done it yet. I have zapped the PRAM and that did change something- I started getting the signature Apple "dah" at boot, something I hadn't noticed was missing. Didn't solve my problem, but it makes me think that some of my problems could be hardware-related and maybe that a PMU reset would help. Thanks, and I'll keep working.

---

### Post by stream303 on 2008-06-03
Btw, if the startup Apple "dah" sound drives you crazy, you can turn it off with

```
sudo nvsetvol 0
```

If you boot into OSX it will reset this back to normal again.

---

### Post by hpp3 on 2008-06-03
AFAIK, the strange purply lines are leftover gunk in the framebuffer that who knows where it goes or why it shows up... quite harmless, really.

For drivers,see here:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

Apparently, the open source driver is capable of 3D, just not as good.

---

### Post by Phonan on 2008-06-17
That's interesting advice about the framebuffer, maybe I should just let my bootup run its course and see if even in GUI I get this. 

Also, I do know that the open "radeon" driver can do 3d, but since my card is a Rage 128, I don't think that driver will work. I could give it a shot, though...

---

### Post by cyberdork33 on 2008-06-17
> **Phonan said:**
> Also, I do know that the open "radeon" driver can do 3d, but since my card is a Rage 128, I don't think that driver will work. I could give it a shot, though...
Reading the link:
> ATI Rage 128 users, make sure that the driver is specified as 'r128'.

---

