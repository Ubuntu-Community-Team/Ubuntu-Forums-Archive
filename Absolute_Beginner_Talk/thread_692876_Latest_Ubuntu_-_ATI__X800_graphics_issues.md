---
title: "Latest Ubuntu - ATI  X800 graphics issues"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-02-10
Downloaded and installed the latest (7.1 I think) Ubuntu last night on my AMD64 3200+ system with 1GB memory and a ATI X800 Pro graphics card.

As soon as Ubuntu loaded for the 1st time it asked me if I wished to use the "Special" ATI graphics drivers even though they were unsupported (or words to that effect)

Being a novice, but knowing graphics drivers are always good to get updated I said yes and followed the prompts.

The problems I'm having seem to be the following.

After a while I start getting green interference lines flickering in certain random areas of the screen.
Just after this the screen goes black, then comes back on, then goes black, then back on etc etc.

the periods of being black get longer and longer until I have no display at all.

Last night this happened. And even after shutting my PC down, and rebooting, I did not even get any screen display in my PC's BIOS as it booted up.

It was as though my ATI card was broken!

I powered down turned off at the mains and waited a few mins. Then all back on, and it was fine again (for a while) when the green interefence lines started to appear, to I shut Ubuntu down before I lost the screen again.

Using the fancy 3D effects (fusion?) I sometimes hear the fan on my graphics card kick into high gear which really only every happens duing an intense 3D game.

I almost feels like my graphics card is being overclocked, or REALLY worked hard which is making it display some green screen interference and eventually giving up.

I thought perhaps there may be some even later drivers from ATI, so I went to their web site and found the latest Jan 08 drivers.

Downloaded them to my desktop. Yet when I click on the file icon I downloaded. Rather than (what I assumed would happen) the drivers installing, it just opens up gedit and says it can't read the file!!!

So, I've no idea even how to install the new drivers.

Getting a bit frustrated as to why something so easy should be so hard :(

Anyone offer any advice?

thanks.

---

### Post by pedro_orange on 2008-02-11
Have you tried installing graphics drivers using Envy? : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I suspect that you xserver config needs a tweak to work properly. Envy will offer to alter your conf file automatically, which is nice.

However you can edit it yourself if you feel up to it. Or you can run something along the lines of:

```
sudo dpkg-reconfigure xserver-xorg
```

& follow the on-screen prompts. (It asks you for max resolutions for your monitor, what type of Kb/mouse you're using etc)

Good luck

---

### Post by PiggiePaul on 2008-02-11
> **pedro_orange said:**
> Have you tried installing graphics drivers using Envy? : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I suspect that you xserver config needs a tweak to work properly. Envy will offer to alter your conf file automatically, which is nice.

However you can edit it yourself if you feel up to it. Or you can run something along the lines of:

```
sudo dpkg-reconfigure xserver-xorg
```

& follow the on-screen prompts. (It asks you for max resolutions for your monitor, what type of Kb/mouse you're using etc)

Good luck


thanks for this advice.
I'm doing "Yet Another" clean Ubuntu install tonight, so will go down the route you suggested.

I guess I had/have a sneeky feeling that somehow some settings were overclocking my X800 card as the fault did just look like what you would expect if you overclocked it for a while and started to see screen faults appearing after a while.

If I could adjust/correct this (possible) overclocking than I'm sure all would be fine.

---

