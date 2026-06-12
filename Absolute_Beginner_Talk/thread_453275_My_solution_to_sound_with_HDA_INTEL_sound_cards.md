---
title: "My solution to sound with HDA INTEL sound cards"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by blop on 2007-05-24
Well im really suffering from this no sound issue and it has driven totally darn bonkers....so crazy that this morning i have installed VISTA on my computer......oh yes!

I now have sound....but thats not a solution to no sound in ubuntu...thats runnning away from the problem. But you see i did get sound working in ubuntu as i installed VMware and then made a virtual machine within it....so now i am running ubuntu in VMware on Vista.

Thank god i have a load of ram.

Hopefully devs will sort this sound issue soon... :popcorn:

---

### Post by n8bounds on 2007-05-25
what card do you have?

say ```
 lspci 
``` in a terminal, look for Audio Device, mine, for instance, is a:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by blop on 2007-05-25
hey..

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

i dont think much can be done....lots of peeps have tried to help me..
i think there is a known bug..

---

### Post by floke on 2007-05-25
Buy some speakers that plug into the headphone socket. They cost around £20 for a fairly decent set, and should do until the fix comes (if it ever does).

Better than using Vista anyway!

---

### Post by blop on 2007-05-25
that would be ok....if i had output from headphone socket.

which i dont!

the whole world is conspiring against me...

do u think i different distro will have the same problem..?

---

### Post by floke on 2007-05-25
Every single distro works the same for me: no sound except through headphones.
I think it's a kernel issue.

---

### Post by psionyk on 2007-05-25
> **blop said:**
> Well im really suffering from this no sound issue and it has driven totally darn bonkers....so crazy that this morning i have installed VISTA on my computer......oh yes!

I now have sound....but thats not a solution to no sound in ubuntu...thats runnning away from the problem. But you see i did get sound working in ubuntu as i installed VMware and then made a virtual machine within it....so now i am running ubuntu in VMware on Vista.

Thank god i have a load of ram.

Hopefully devs will sort this sound issue soon... :popcorn:

Are you by chance using S/PDIF output on your card? (digital output via optical cable to a surround sound system)

If you are, you need to select the ALSA drivers (which I believe should be in use by default), and then in the terminal, type

```
alsamixer
```

and on the settings screen that comes up, look for an entry that reads IEC958, and with it selected, hit 'm' to unmute the channel, at which point the 'MM' entry should change to '00' (don't worry about it saying zero volume, it will be controlled by the master output volume)

This will enable digital output via SPDIF, which doesn't show up for some reason on the normal GUI interface of the mixer.  I had the same problem, and was getting no sound until I actually enabled this in the mixer.  Hope this helps!! :)

---

### Post by afilonov on 2007-05-25
Try this solution. Helped me with system76 (Asus).

[https://bugs.launchpad.net/ubuntu/+bug/105582](https://bugs.launchpad.net/ubuntu/+bug/105582)

---

### Post by blop on 2007-05-26
hey guys thanks for your help but im sure nothing can be done until devs work some magic...

as the forum is full of ppl without sound... i have tried lots and lots of bug fixes 

and that post...those links did nothing for me...

ill just have to wait.

---

### Post by Sparkster185 on 2007-05-26
I have a Toshiba A135 series, but I believe our sound cards are very similar.  Here is a thread where I described how I fixed my problem:

[http://ubuntuforums.org/showthread.php?t=455266](http://ubuntuforums.org/showthread.php?t=455266)

I hope this works for you.  Best luck to you.

-Sparkster

EDIT:  It turns out we have identical sound cards, so that fix I linked you to just might work.

---

