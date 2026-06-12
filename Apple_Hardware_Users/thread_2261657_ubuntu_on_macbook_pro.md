---
title: "ubuntu on macbook pro?"
date: 2015-01-20
forum: Apple Hardware Users
---

### Post by hmiersch on 2015-01-20
hi.
at the moment i run ubuntu in a virtualbox VM on OSX. but i'd like to boot into ubuntu directly, without OSX. So I took my .iso file, created a bootable USB stick from it and installed it on an external HD. a whole disk, not just a partition. actually, in the installer i created a small partition as swap space and a big one to boot from.
as far as i can tell, the installation went well. the only problem is that the mac can't find the ubuntu partitions on that HD. that means i can't boot into ubuntu. is that why i need rEFInd?
I tried to install rEFInd, but it keeps giving me an error: no EFI volume found, or something like that.

so what can i do to make it work?

just had an idea: i'm gonna boot from my backup disk and try to install it there. if it works, i'll restore back to my internal disk, and that should be that. dont know if it's gonna work but i'm gonna try.

---

### Post by slickymaster on 2015-01-20
*Moved to the ***Apple Hardware Users*** sub-forum*

---

### Post by hmiersch on 2015-01-21
> **hmiersch said:**
>  just had an idea: i'm gonna boot from my backup disk and try to install it there. if it works, i'll restore back to my internal disk, and that should be that. dont know if it's gonna work but i'm gonna try.  ok, i tried that, and at least i could install rEFInd this way. but when i try to boot from my linux disk, sooner or later the screen goes black, and then nothing happens. do I have to re-install?

---

### Post by este.el.paz on 2015-01-21
> **hmiersch said:**
> ok, i tried that, and at least i could install rEFInd this way. but when i try to boot from my linux disk, sooner or later the screen goes black, and then nothing happens. do I have to re-install?

Yes.  This time create a small, 10 MB or so, partition labeled as "bios_grub" . . . in front of the 'buntu home, and after the OSX partition--then run the install again.

e.e.p.

---

### Post by hmiersch on 2015-01-22
> **este.el.paz said:**
> Yes.  This time create a small, 10 MB or so, partition labeled as "bios_grub" . . . in front of the 'buntu home, and after the OSX partition--then run the install again.

e.e.p.

Actually OSX is on the internal HD and I've reserved a 250GB external HD for Ubuntu. 
So I need 3 partitions, one bios_grub, one for swap space (what size would you recommend? That machine has 16GB RAM) and one to boot from, correct?

---

### Post by este.el.paz on 2015-01-22
> **hmiersch said:**
> Actually OSX is on the internal HD and I've reserved a 250GB external HD for Ubuntu. 
So I need 3 partitions, one bios_grub, one for swap space (what size would you recommend? That machine has 16GB RAM) and one to boot from, correct?

3 partitions is what has worked for my MBPro so that GRUB shows up and the linux system boots.  Swap is supposed to be 1 - 2x RAM, but since you have so much RAM possibly 16 G or possibly less, might be enough?  Depends if you do processor intense work?  You could search the web for various recommends.

But, caveat, I tried to do an install of Lu or U-MATE PPC through my iBook to an ext HD partition and the installer seemed to spread the install across int & ext HDs . . . so I'm not sure what happened; possibly because I already had a linux install on the int HD and that "confused" the installer???  OSX was not harmed.

Another thing to pay attention to is the "Mactel" sticky at the top of this page, concerning fan control/heat issues for Intel Macs . . . one of the reasons why running in VM might be the "better" choice . . . .
e
.e.p.

---

### Post by hmiersch on 2015-01-24
> **este.el.paz said:**
>  one of the reasons why running in VM might be the "better" choice . . . . e .e.p.  i dont want to use a VM because  - it is too small, only 40GB - it cant use the full 16GB RAM because some of it is required for OSX - i dont know how, but it bypasses the OSX firewall, so OSX doesnt give me any benefit there. - i want to get away from OSX. - occasional graphics issues (like when switching from full-screen to window mode and back)  stuff like that...

---

### Post by maclenin on 2015-01-24
**hmiersch!**

Take a peek [here]("http://ubuntuforums.org/showthread.php?t=2259849") - the thread was originally marked **[COLOR="#008000"][all variants][/COLOR]** because I believe the general install process should work for most intel-based macbooks / pros and flavors of (*)buntu - give it a whirl.

Good luck!

---

### Post by hmiersch on 2015-01-26
Ok, I finally managed to get the mac to boot from that HD. Thanks for the help.  Now that's out of the way, I can go back to wondering what software to install. But that's for another thread...

---

