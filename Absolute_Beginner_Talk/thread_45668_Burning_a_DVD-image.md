---
title: "Burning a DVD-image"
date: 2005-07-01
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-07-01
Hey, I've installed GnomeBaker and graveman now (like graveman the best I think, better interface) but when trying to burn a DVD-image using the "Burn CD-image"-function it seem to be complaining about me not using a CD, but a DVD as destination.
1. Shouldn't a CD-image fit to a DVD as well? Meaning it should just burn away like it never burned before.
2. If it only burns CD-R images with this function, how do I burn a DVD-image?

In graveman it first started looking for a CD, it told me to put one in my DVD-RW, wich I had selected as destination. After a while it still told me to insert a CD but had the text "Currently: DVDR" under.

---

### Post by emmet on 2005-07-01
I think they are different fish.

I'm not sure if you *can* burn a CD image to a DVD.

You can burn a DVD image to a DVD - I've definitely done that before, and actually all I did was right-mouse click on the .iso file and select the "burn image" option.

I realise that this isn't a really helpful answer. 

You could try to mount the .iso file (there's help in the ubuntuguide), open it as if it were a standard drive and then use graveman to burn these files to a DVD (as if you were just copying the files from a hard drive).

Good luck, and hopefully someone will be able to tell if there is a definitive answer regarding CD.iso to DVD.iso compatibility.

Cheers

Emmet

---

### Post by Trojan1313 on 2005-07-01
The rightclick and Burn image option worked, it started burning it with CD/DVD Creator (no idea what the real name is, it's not GnomeBaker nor graveman anyway). But the fact that is doesn't work in GnomeBaker or graveman is ridicilous. =/

---

### Post by sapo on 2005-07-01
i would recommend you install k3b.. for me is far better than gnome baker or graveman

sudo apt-get install k3b

it requires a few kde libs.. but is a very good program  :grin:

---

### Post by poofyhairguy on 2005-07-01
[QUOTE=sapo]i would recommend you install k3b.. for me is far better than gnome baker or graveman

sudo apt-get install k3b

it requires a few kde libs.. but is a very good program  :grin:[/QUOTE]


I second that. I only use k3b.

start it with this command one installed:

> gksudo k3b

---

