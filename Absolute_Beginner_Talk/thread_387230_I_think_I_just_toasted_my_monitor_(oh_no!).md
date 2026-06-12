---
title: "I think I just toasted my monitor (oh no!)"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-03-18
Hey guys,

I had a fresh install of Ubuntu 6.06 i386 last night. I installed the latest nvidia video drivers by doing:

```
sudo apt-get install nvidia-glx
```

but hadn't run "sudo apt-get install nvidia-common-*something*" yet....cause the nvidia-glx thing was taking too long to download. Anyways, I didn't do much with it...just left it there, but later I noticed(its hard NOT to notice it anyways), that the screen was stretched very wide..and all he windows(e.g. firefox) were squashed in from the sides... ??? :(

So I tried installing the nvidia-kernel-common then or something, and I can't recall whether that installed or not. I checked the xorg thingy, and the "nv" was already changed to "nvidia"(though I didn't change it). and I couldn't run "glx-gears" ether...said some problem with the RGB settings (sorry if I can't give an accurate description...I'm typing this from me laptop...as I can't access me Ubuntu box at the moment, due to said problem :(

Then while trying to figure out the problem, the screen just went black..and even the monitor "power light" wasn't on. and i couldn't get it back on. The cable wasn't loose or anything, cause I tried checking that too....is it realli gone? :( Does anybody have any suggestion as to what caused it?

Cheers, and thanks in advance.
Kinson

---

### Post by AtrejuT on 2007-03-18
well does the monitor stay off if you reboot? can you just attach it to your laptop and see if it works there? To have the biggest worries out of the way...

to install nvidia drivers I would recommend a script called envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

good luck

atreju

---

### Post by kinson on 2007-03-18
> **AtrejuT said:**
> well does the monitor stay off if you reboot? can you just attach it to your laptop and see if it works there? To have the biggest worries out of the way...

to install nvidia drivers I would recommend a script called envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

good luck

atreju

No :( I even tried connecting it to my laptop via the analog connection...no go. I think its realli toast...dang it :(

Thanks for the suggestion with the Envy script, I can give it at try. But do you have any idea why  my monitor toasted? I'm currently using my spare monitor, but i sure as hell don't want this to get toasted to :(

Btw, is there any way for me to boot into Ubuntu with safe(lower) graphics mode, so that I can download and apply this patch, without toasting me spare monitor :( If not I'll have to reinstall

Cheers,
Kinson.

---

### Post by AtrejuT on 2007-03-18
the thing with your monitor seems really strange to me - never heard that before.
is it a CRT or a flatscreen?
You can boot into single user mode from your boot menu (there should be an entry recovery mode) and you can see if there are any backups of your /etc/X11/xorg.conf file which you can restore.

sorry about your monitor.
atreju

---

### Post by kinson on 2007-03-18
> **AtrejuT said:**
> the thing with your monitor seems really strange to me - never heard that before.
is it a CRT or a flatscreen?
You can boot into single user mode from your boot menu (there should be an entry recovery mode) and you can see if there are any backups of your /etc/X11/xorg.conf file which you can restore.

sorry about your monitor.
atreju

I suppose i hit F8 like windows to get into that boot menu?

I'm using a 4 year old CRT.

I can resture my xorg.conf file..but I think the backup I had was also "nvidia" and not "nv"...not sure. Fortunately since its a fresh install, I could just reinstall the OS. Like I said, the main thing is I don't want it to happen again, so I'm busting me brains to find out what went wrong :(

I never had any of these problems(even those I recently posted in other threads) when I install ubuntu 6.06 AMD64. Weird... :(

Downloading Kubuntu 6.10 now, was thinking of giving it a try if I have to reinstall again, hehe :p

Cheers,
Kinson

---

### Post by scxtt on 2007-03-18
have you tried unplugging it, from the wall socket AND from the back of the monitor?

---

### Post by kinson on 2007-03-18
> **scxtt said:**
> have you tried unplugging it, from the wall socket AND from the back of the monitor?

I unplugged the whole thing, plugged it into a different wall socket, and into my laptop(a different computer), and its still no go :'(

I'm currently able to use another monitor for my Ubuntu pc(but booting from a live cd for fear or burning my last monitor), so it can't be the video card's problem. Definately just a configuration issue that killed it, IMHO :(

Kinson

---

### Post by h0ax on 2007-03-18
Hmm...
That sounds really odd.  A 4 year old CRT could have been on its way out without the "configuration issue"  -
I can't fathom how changing your video card's driver would render a monitor unusable.

I've had several monitors just die on me, personally I think it was a bad coincidence.

You can get another CRT monitor for less than $15 though, so I don't think it's a HUGE loss, albeit not something you want to have happen.

Sorry about that!

---

### Post by kinson on 2007-03-18
> **h0ax said:**
> Hmm...
That sounds really odd.  A 4 year old CRT could have been on its way out without the "configuration issue"  -
I can't fathom how changing your video card's driver would render a monitor unusable.

I've had several monitors just die on me, personally I think it was a bad coincidence.

You can get another CRT monitor for less than $15 though, so I don't think it's a HUGE loss, albeit not something you want to have happen.

Sorry about that!

I understand what you mean that it might've been its time. But the funny thing was that all the windows (as I mentioned before) were squashed in from the sides, kinda looked a bit like this ----> ) (

I know there's a monitor settings for that, but this only applied to windows I think.....and my desktop(taskbar and all) was stretched funnily.

15USD for a CRT monitor? Damn....Here the cheapest new 17inch CRT I could pick up would be at least RM350(give and take a bit), which is nearly my whole month's food+entertaintment expenses :( Fortunately I still have a backup monitor. Its no beauty, but it does the job. Like I mentioned before, my main worry is that if I buy a new monitor, I don't wanna toast it the moment I start using it :( At the moment I'm still too terrified to boot my ubuntu with the backup monitor, cause if that goes, I have no monitors left :(

I'm not blaming Ubuntu or anything, once I've determined WHY the monitor died, and how to avoid it again, I'll happily install Ubuntu again. Been using it for the past 6 months or so :) Just downloaded Kubuntu 6.10 earlier, gonna give it a try sometime soon :)

Cheers,
Kinson.

Cheers,
Kinson

---

