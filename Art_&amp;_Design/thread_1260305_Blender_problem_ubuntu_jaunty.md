---
title: "Blender problem ubuntu jaunty"
date: 2009-09-07
forum: Art &amp; Design
---

### Post by Elcid247 on 2009-09-07
hi im having a problem with blender on ubuntu jaunty.

ive tried 3 versions, 2.48a (from repos) 2.49a and 2.49b and all of them gave me well not an error but a wrong display, ive attatched a screenshot. it is bugged on the top and the bottom.

ive also tried switching between compiz and metatcity and got same results in both, this never happened b4, on previous installations of jaunty or intrepid or hardy.

any ideas?

[IMG]http://i28.tinypic.com/2ros3f8.png[/IMG]

---

### Post by hessiess on 2009-09-07
> **Elcid247 said:**
> hi im having a problem with blender on ubuntu jaunty.

ive tried 3 versions, 2.48a (from repos) 2.49a and 2.49b and all of them gave me well not an error but a wrong display, ive attatched a screenshot. it is bugged on the top and the bottom.

ive also tried switching between compiz and metatcity and got same results in both, this never happened b4, on previous installations of jaunty or intrepid or hardy.

any ideas?

[IMG]http://i28.tinypic.com/2ros3f8.png[/IMG]

If you are using it, disable compiz, whats your graphics card?

---

### Post by meborc on 2009-09-08
try fullscreen mode also, see if that makes any difference

---

### Post by Danoz on 2009-09-08
Sounds like the graphics card. Try to reinstall your graphics card drivers, disable compiz, reinstall Blender and see if that helps...

---

### Post by Elcid247 on 2009-09-10
turns out its my driver it has a bug with version 2.6 of xorg

i found [here]("http://www.blender.org/forum/viewtopic.php?p=74614&sid=a56deca72b5990cdfaec2b2d821f1090") and [here]("http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/") that i had to revert back to 2.4

so i followed this [guide]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

sadly nothing changed at all even though i checked my PCI ID ([8086:2772] (rev 02)) and a similar 1 was reported to work fine by a tester and i added Option "AccelMethod" "xaa" in /etc/X11/xorg.conf as he suggested.

when i run ```
sudo apt-get install xserver-xorg-video-intel-2.4
```

says its already there and newest version even though it doesnt show in synaptic.

am i missing something?

---

### Post by pomalin on 2009-09-10
You can just download the tar.gz at blender.org, turn compiz off, and run the softwaregl version from the archive, and all will be allright.

---

### Post by Elcid247 on 2009-09-10
> **pomalin said:**
> You can just download the tar.gz at blender.org, turn compiz off, and run the softwaregl version from the archive, and all will be allright.

could try that, but i do want the old driver back since anything fullscreen isnt running anything close to smooth so i do wana fix this the driver way.

but thanks nice idea.

---

### Post by Elcid247 on 2009-09-10
> **Chauncellor said:**
> Are you using Intel graphics? Intel on Jaunty :: Audio on Hardy.

It just doesn't work

There's a solution floating around somewhere, and it involves updating Xorg packages via PPA, but I did that on an experimental computer and it essentially rendered my computer extremely unstable.

yes my vga is

Intel 82945G/GZ rev02

whats weird is that its the same as of the guy who posted in blender thread and the workaround is reported to work for this card.

i guess Intrepid was and is the best ubuntu version ever, it had everything working like magic. hope karmic does better.

ok this is turning into a driver issue so im marking it as solved since the archive suggestion by pomalin did the trick and creating a new thread in hardware section

EDIT: fixed b4 i made the thread, i followed this [guide]("http://ubuntuforums.org/showthread.php?t=1130582") the bleeding edge solution did the trick.

thanks all for ur help

---

### Post by hessiess on 2009-09-11
> **pomalin said:**
> You can just download the tar.gz at blender.org, turn compiz off, and run the softwaregl version from the archive, and all will be allright.

Running with software opengl would absolutely kill any performance, though I suppose you wouldn't get a high usable polygon count out of an integrated chip anyway.

---

### Post by pomalin on 2009-09-11
Softwaregl is not that bad in term of performance, and in waiting of karmic (with wich all work as expected)it's without tweaking the system the only good solution I found.

---

