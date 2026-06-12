---
title: "Imac g3 Install Issues"
date: 2006-11-06
forum: Apple PPC Users
---

### Post by captcadwallader on 2006-11-06
I have a Imac g3.  500 MHZ with 512 memory.  I am trying to install Ubuntu 6.06 LTS or Xbunty 6.06 LTS.  I am having the same problem everyone else is haveing with Imac G3s.  I get past the sound and then a blank screen.  There appears to be a problem with the Xconf.  

I have tried the control option f1, then:

sudo vi /etc/X11/xorg.conf

with # in the load dri line and changing

HorizSync 60-60
VertRefresh 75-117 

Then sudo kill all gdm and then
sudo gdm start.

still doesn't work.

I think, but I may be wrong, that part of the problem may be that Apple 
changed from a PCI video interface to a AGP interface about the time of 
the 500  MHZ Imac's.  Then again I may be all wrong about this.

Has anyone got Ubuntu or Xbuntu to work on a G3 Imac and especially a 500 MHZ, and if so how?

I have tried Fedora Core 5 and it did not work and SUSE 10.1 and it did not work.

Maybe gentoo is next ro try.

All the best.

---

### Post by linear on 2006-11-06
Yes, I routinely run Ubuntu 6.06 on a 500MHz slot-loading iMac G3. All it took was the xorg.conf corrections you described.

Do you still get a blank screen after the edits, or is something else (not) happening?

---

### Post by bodycoach2 on 2006-11-06
Make sure you download and burn the 6.06.1 version. So far, 6.06 has never booted on any of my older iMacs (bondi version). Neither has 6.10.

Use the alternate install CD if your memory is under 256 meg. Probably should use the alternate install CD either way, just in case.

---

### Post by LorenzoM on 2006-11-14
6.10 worked for me using the xorg editing commands.  

However your problem may be that the 'sudo kill all gdm'  does not really work.  I had to manually kill -9 all the gdm processes (only two for me) and then restart gdm.

do a 'ps -a | grep gdm'  and kill all the process ids except the one that is X and has a parameter mentioning gdm.  Then 'sudo start gdm'

Seemed to be ok. Actually I'm still installing it now. Kinda slow but neat.



Larry

---

### Post by LorenzoM on 2006-11-14
I mean 'sudo gdm start'

---

### Post by Osiris23343 on 2006-11-14
Its kind of round about, but the way i got it to install is by using the old 5.10 cds that werent live, then i updated.  The problem is that the imacs are not powerful enough to run entirely off ramdisk.

---

### Post by samden on 2006-11-15
I'm also having issues with the iMac G3 500Mhz, just different issues (see my thread in this forum). But the idea of installing 5.10 then upgrading sounds great. Where do I download the 5.10 ppc install cd from? It doesn't appear particularly obvious in the download section of the ubuntu website.

---

