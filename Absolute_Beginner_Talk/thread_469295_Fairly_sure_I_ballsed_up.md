---
title: "Fairly sure I ballsed up"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by FrenchyFungus on 2007-06-09
Right, so I planned to install Linux but with the partitionthing so I could still use XP, I went through the installation and when the partition option came up, I chose the default option (Guided something) thinking on the next page it would ask me how I wanted to partition it.

Anyway, I'm now fairly sure I've completely removed Windows and all my files etc. that I had before, as it says I have 80GB of free space whereas I had only 30 before.

That means I ballsed it up, yeah?

How easy is it to reinstall Windows XP so that I have both Windows and Linux?

Anyway, other problems I'm having:

Wireless internet just doesn't seem to want to work. I tried following all the instructions with ndiswrapper, but I couldn't even get it to install. I'm using a Compaq Presario v5000 laptop if that helps.

IRC chat, which client is most similar to mIRC? As that is what I've used for years.

Any and all help much appreciated

---

### Post by theredcross on 2007-06-09
If I remember correctly when you select "guided partitioning" there should be a slider, on the same page you select the partition option if I am remembering well enough. Assuming you've now got a grub boot option when you start up your computer, is there still an option to boot into windows?
Everytime I've had to reinstall XP (when I was still dual-booting) I invariably lost my linux partition, because of the Windows partition software not allowing me to do so.

---

### Post by FrenchyFungus on 2007-06-09
Well, since I haven't got Ubuntu properly set up yet, I'm not at all worried about losing it now if it means I get dual booting to work.

But when I start my laptop it just boots up linux automatically, no option to boot Windows anywhere I could see.

---

### Post by Bohlio on 2007-06-09
if you have grub installed and hit "esc" somewhere along in the boot process, A menu should pop up and allow you to choose what to boot, Try it to see if windows is still there.

---

### Post by theredcross on 2007-06-09
And just so I'm understanding, how large is your hard drive?
also, run gparted and see if there are any NTFS partitions left.

---

### Post by FrenchyFungus on 2007-06-10
> **Bohlio said:**
> if you have grub installed and hit "esc" somewhere along in the boot process, A menu should pop up and allow you to choose what to boot, Try it to see if windows is still there.
Did that, no Windows there.
[quote=theredcross]And just so I'm understanding, how large is your hard drive?
also, run gparted and see if there are any NTFS partitions left.[/quote]
100GB

Will do the gparted thing.

---

### Post by Bohlio on 2007-06-10
I think you may have completely lost your windows parititon :-(
Im assuming that you did do the guided partitioning, but you left the slider at %100 :-( Sorry man.

---

### Post by FrenchyFungus on 2007-06-10
> **Bohlio said:**
> I think you may have completely lost your windows parititon :-(
Im assuming that you did do the guided partitioning, but you left the slider at %100 :-( Sorry man.
That'd make sense, aye.

Oh well, I decided to just go back to Windows anyway, wasn't for me.

Now I've got a whole 'nother bundle of problems with getting Windows to recognise the audio, wireless devices etc.

Meh, I'll get it sorted out somehow.

---

