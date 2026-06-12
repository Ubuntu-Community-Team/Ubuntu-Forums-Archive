---
title: "iBook G4 8.04 Install Tip"
date: 2008-05-18
forum: Apple Hardware Users
---

### Post by mchladek on 2008-05-18
Hello All,

After updating my iBook G4 (model PowerBook 6,3; ATI Radeon Mobility 9200) from 7.04 to 8.04, my brightness controls and suspend would not work.  I messed around with config files for quite awhile until changing my yaboot.conf file to the following finally did the trick:

```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="nosplash [COLOR="Red"]video=radeonfb:1024x768-24@60[/COLOR]"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="nosplash [COLOR="Red"]video=radeonfb:1024x768-24@60[/COLOR]"
```

The "radeonfb" seemed to do the trick.  My brightness controls now work and my machine sleeps and wakes from sleep perfectly.

Just wanted to pass that info along to anyone having a similar issue.

---

### Post by Ariccanfly on 2008-05-25
I guess you never tried booting from the ppc 8.04 live disk eh?

It dosnt work on the g4 we have...

Hopfully that fb command will be the cheat code i need to boot this sucker,

cheers

---

### Post by Scientia on 2008-05-26
Does anyone know the command codes to enable to brightness buttons to function?
(On a iBook G3 PowerPC 700mhz)

Thanks.

---

### Post by jukoz on 2008-05-26
Hey!

I got an Ibook G4. The liveCD works ok, but I need a few conformations before I start installing 8.04LTS:

1.) Does suspend/hibernate work? I really need this.

2.) Does the wifi (airport extreme) work trough fw-cutter or ndiswrapper?

Ajt!

---

### Post by mchladek on 2008-05-26
> **Ariccanfly said:**
> I guess you never tried booting from the ppc 8.04 live disk eh?


Nope, I installed using the alternate iso, which went smoothly.  When I first booted after installing, I used ```
video=ofonly nosplash
``` This worked but sleep & brightness controls didn't work.

---

### Post by mchladek on 2008-05-26
> **jukoz said:**
> 
1.) Does suspend/hibernate work? I really need this.


I can't comment on hibernate, but suspend works.  I occasionally get an error when I wake from suspend saying that my computer did not correctly go into suspend mode.  However, I got that message after having my computer on suspend all night, and the battery usage was just as much as if it had suspended properly.

> **jukoz said:**
> 
2.) Does the wifi (airport extreme) work trough fw-cutter or ndiswrapper?


Yes, you have to use fw-cutter (ndiswrapper is not for PPC).  I followed the instructions in the PowerPC Wiki, and worked perfectly.

---

### Post by stream303 on 2008-05-26
> **mchladek said:**
> The "radeonfb" seemed to do the trick.  My brightness controls now work and my machine sleeps and wakes from sleep perfectly.

Thanks for posting this!

If you don't mind, could you post these results as well as your xorg.conf and lspci output to the following thread:
[http://ubuntuforums.org/showthread.php?t=802528](http://ubuntuforums.org/showthread.php?t=802528)

I'm trying to consolidate working xorg.conf and yaboot.conf along with lspci outputs for various models into one document sort of for succesful Hardy installs.

Nice job on the iBook!

---

### Post by jukoz on 2008-05-26
Thanks mchladek!
Now I just have to make back-ups...

Ajt!

---

### Post by mchladek on 2008-05-26
> **jukoz said:**
> 
1.) Does suspend/hibernate work? I really need this.


Update:  Hibernate doesn't work for me :( I haven't investigated it much so don't know what the hang up is, but at least suspend is working.

Thanks for the tip, stream.  I'll post over on that thread.

---

### Post by jukoz on 2008-05-27
Well, as long as one of the two work OK, that will do for me.

Ajt!

---

### Post by stream303 on 2008-05-27
I've always found sleep to be useful when it works, but hibernate was always a non-issue since it seems to take just as long to store and retrieve the setup as compared to just doing a shutdown and powerup. :)

It would be nice to have though.

---

### Post by Scientia on 2008-06-03
I tried the codes from the first post, and suspend is still not working, neither are the brightness controls on my iBook. (G3 700mhz,ATI Radeon Mobility M7 LW [Radeon Mobility 7500]). Any solutions? Thanks.

---

### Post by stream303 on 2008-06-03
If you edited your /etc/yaboot.conf with the custom kernel parmeters in the "append=" line, did you make sure that the system knows about the change with:

```
sudo ybin -v -C /etc/yaboot.conf
```

---

### Post by jukoz on 2008-06-03
My results:

With 8.04 I couldn't get the wifi working. It kept installing the fw, but newer installed it.
Also, no sleep of any kind.

With 7.10 the wifi is working. But the sleep doesn't.
The only option is suspend, the computer suspends but does not wake up. The screen is all weird.

If I try "/usr/lib/hal/hal-system-power-pmu sleep" in console, suspend works perfectly. But not in X.

I think I will work on the 7.10 for a while, to try to get suspend working. There are lots of forums regarding this, so I guess I have a chance.

Ajt!

---

### Post by lukerz8 on 2008-07-17
would someone mind giving me a link to where you all got an 8.04 version of ppc ubuntu? i can only seem to find the 7.10 version anywhere :(

---

### Post by luke.is.very.handsome on 2008-07-17
[HTML]http://cdimage.ubuntu.com/ports/releases/[/HTML]

It has the listing there for all the versions you might want.

---

### Post by luke.is.very.handsome on 2008-07-17
> **Scientia said:**
> Does anyone know the command codes to enable to brightness buttons to function?
(On a iBook G3 PowerPC 700mhz)

Thanks.

ctrl-f1, ctrl-f2?  Sorry if that wasn't what you meant, but its what I use.

---

### Post by Scientia on 2008-07-25
Nope, i think my keys are fn+f1, fn+f2. The thing is getting them to work.
Now when i press the buttons a bar(presumably brightness) appears but then nothing else is changed.

---

### Post by gabric098 on 2008-07-31
I modified yaboot.conf appending the line
> append="nosplash video=radeonfb:1024x768-24@60"

Brightness control and suspend function works perfecly for me. (using fn+f1 and fn+f2)
Hibernate doesn't work but I think it's not an ibook "native" feature.

Volume control doesn't work pretty smoothly: let's suppose that the volume is set to max (10), if i press 2 times fn+f4 the bar on the screen go to 0, but the real volume go to 8, not a big problem but annoyng.

G.

---

### Post by usererror on 2008-09-30
> **Scientia said:**
> Nope, i think my keys are fn+f1, fn+f2. The thing is getting them to work.
Now when i press the buttons a bar(presumably brightness) appears but then nothing else is changed.

Have you gotten your brightness FN+F1 / F2 keys to work?  I am looking for any help on this!

**EDIT - SOLVED!!!**:  I got mine working!  Just as the original poster stated:

```

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="[COLOR="Red"]nosplash video=radeonfb:1024x768-24@60[/COLOR]"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="[COLOR="Red"]nosplash video=radeonfb:1024x768-24@60[/COLOR]"

```


then you have to follow up with this command:

```
sudo ybin -v -C /etc/yaboot.conf
```

from this post: [http://ubuntuforums.org/showpost.php?p=5012035&postcount=1](http://ubuntuforums.org/showpost.php?p=5012035&postcount=1)

I am a Linux user, not a genius, and that post solidified the solution for me.  I am very grateful!

/proc/cpuinfo
```

processor       : 0
cpu             : 7447A, altivec supported
clock           : 1420.000000MHz
revision        : 0.5 (pvr 8003 0105)
bogomips        : 73.47
timebase        : 18432000
platform        : PowerMac
machine         : PowerBook6,7
motherboard     : PowerBook6,7 MacRISC3 Power Macintosh
detected as     : 287 (iBook G4)
pmac flags      : 0000001b
L2 cache        : 512K unified
pmac-generation : NewWorld

```
tag with: G4, ibook, contrast, brightness, controls

---

### Post by cyberdork33 on 2008-09-30
> **usererror said:**
> tag with: G4, ibook, contrast, brightness, controls

You should add the tags that you can...

---

### Post by usererror on 2008-10-02
> **cyberdork33 said:**
> You should add the tags that you can...

I JUST finally found the "edit tags" link.  wow I am blind (or it is hidden well. :D )

---

### Post by billyjmc on 2009-06-28
I had the same issues as the OP on my iBook G4 12" 1.33GHz (mid-2005) [PowerBook6,7] using Xubuntu 9.04. Hey, I have to put all that in there for Google, okay?! :)

Anyway, the above info fixed similar issues I was having, but the real boon here is that I was having problems viewing the virtual terminals. I could see *something* on the screen, but it just looked black on cursory glance. I thought I was having endian-ness problems with the framebuffer, and even rebuilding the kernel several times didn't fix it. I kept updating the symlinks for vmlinux, and never looked at yaboot's config after adjusting it shortly after my initial install. D'oh!

Now everything works like a champ, and I can actually make use of the virtual terminals in a non-trivial way. (I could always switch to them, login and execute commands blindly, which was useful for running killall occastionally, or forcing a reboot, but not much else.)

Anyway, to re-iterate, my I can now use the virtual terminals on my iBook, thanks to a quick modification in yaboot.conf which changes which framebuffer the kernel uses.

I was having problems with the splashscreen being strangely colored before, too. I'm going to have to do a reboot to see if that is also fixed. :) Will post my results here.

---

### Post by billyjmc on 2009-06-29
=D>

Yup! This little trick also corrected the startup logo/splashscreen. Before it looked like I was back on my Tandy 1000 with four colors and dithering, but now, my Mac is sexier than ever. I think I'm going to have to re-enable the splash screen permanently in yaboot.

Oh, and the computer sleeps like a baby, too. I left alone for two minutes and it was out like a light. =) I need to change those settings now, too.

I had read elsewhere that when building the kernel you can just build both the open firmware framebuffer as well as radeonfb, and the kernel would pick the appropriate one. I was really confused when it kept being mangled, but now I know I was forcing it to pick the wrong one (OF) the whole time! :oops:

My guess is that if I simply removed all of yaboot's constraints, the kernel would have worked perfectly from the get-go. I'll probably have to try that out, too....

(For those of you for whom this didn't work, check _[this link out]("http://ubuntuforums.org/archive/index.php/t-933189.html")_. They fixed the issue by modifying the resolution set in /etc/usplash.conf, which didn't work for me, as it was already set correctly by default.)

---

