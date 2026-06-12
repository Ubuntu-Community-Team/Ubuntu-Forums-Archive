---
title: "Why is my sound so low?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by happyxix on 2007-10-12
I have just installed the RC of Gutsy and so far everything is working fine. However the Maximum sound I get is still quite low. I set everything up to their highest in the ALSA mixer and volume control.

It worked fine in Feisty except when I first installed it. But after a reboot it fixed itself. This time with Gutsy however even after I reboot the sound is low. Any help? Thanks

---

### Post by jnorthr on 2007-10-12
Is there a speaker symbol on your menu bar ? If you can right-click that, there may be an additional volume control slider that is set too low.

---

### Post by happyxix on 2007-10-12
I've tried the volume control already and they are all at its maxed =\

---

### Post by obiwan on 2007-10-14
I'm having that same problem in a toshiba satellite. All sliders in the volume control are already set to the maxium. In feisty I never had problems with sound. Any solution to this?

---

### Post by happyxix on 2007-10-14
Surprisingly I'm also using aToshiba Satellite... and Still having this problem..

---

### Post by aktiwers on 2007-10-14
What if you type:
```
alsamixer
```in terminal? And turn up "Master M" and "PCM"

Edit:
Oh sorry.. just reread your post..  just ignore this then..

---

### Post by obiwan on 2007-10-14
[This solution]("http://ubuntuforums.org/showpost.php?p=2397488&postcount=9") worked great for me.

Just add to the file /etc/modprobe.d/alsa-base this:

```
options snd-hda-intel model=3stack
```

Then restart.

---

### Post by happyxix on 2007-10-14
> **aktiwers said:**
> What if you type:
```
alsamixer
```in terminal? And turn up "Master M" and "PCM"

Edit:
Oh sorry.. just reread your post..  just ignore this then..

Actually. My master is at 00 and shaded in red as in this screenshot

[IMG]http://i53.photobucket.com/albums/g77/happyxix/Screenshot-6.png[/IMG]

Hod would I turn that up? I can't find it in the volume controls

And I dont have the folder

/etc/modprobe.d/alsa-base

Should I just make it or am I missing something...

---

### Post by obiwan on 2007-10-14
/etc/modprobe.d/alsa-base is a file, not a folder.

try this on a terminal:

```

sudo gedit /etc/modprobe.d/alsa-base

```

At the end of the file add this line: 
```

options snd-hda-intel model=3stack

```

Save the file and restart. Sound should work normally now :).

---

### Post by happyxix on 2007-10-14
Ahhh I reallized that after i made the post haha. And I tried it and it work perfectly. Thanks!

---

### Post by klml on 2007-10-19
> **obiwan said:**
> [This solution]("http://ubuntuforums.org/showpost.php?p=2397488&postcount=9") worked great for me.

Just add to the file /etc/modprobe.d/alsa-base this:

```
options snd-hda-intel model=3stack
```

Then restart.

wow, this works great, it changes the default mode of my ALC880 sound card from 8 Channel to 2 Channel which is what i wanted since i'm using altec lansing ACS45.1 speaker

thanks a million.

---

### Post by spellvexit on 2007-10-20
I'm afraid I tried the edit at the bottom of my alsa-base file and it had little difference.  Even with my sound jacked up to the maximum, it's only just listenable and I fear that if I ever flop over to my Windows side it'll blow out my lousy speakers.

Isn't there any sort of base value I can just add to amplify the output?  Any numbers/values in the file that I can tweak?

I've got a Realtek onboard card for an nVidia 590 chipset.  The sound should be HDA, so I had high hopes that the addition of "options snd-hda-intel model=3stack" would have an effect.

Sound is a really *really* basic need on a system.  Mine is working -- why is getting it to perceptible levels so hard?

---

