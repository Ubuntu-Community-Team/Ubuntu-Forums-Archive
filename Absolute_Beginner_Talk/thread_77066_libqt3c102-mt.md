---
title: "libqt3c102-mt"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-10-16
Hi

Seems that libqt3c102-mt is still not available in Synaptics. I read that it would be by the time Breezy came about. But i'm in Breezy and it still is not available.

Is that true for other people? 
Can i go and download it somewhere else?


thank you

--
sophtpaw

---

### Post by r0nin on 2005-10-16
I'm wondering about this too: Skype needs it if you use the repo.

---

### Post by sophtpaw on 2005-10-16
[QUOTE=r0nin]I'm wondering about this too: Skype needs it if you use the repo.[/QUOTE]

Exactly! 

Who to ask the question? No one seems to know?

--
sophtpaw

---

### Post by rwabel on 2005-10-17
it will never! ubuntu uses another version. There are several threads about that already. Either skype changes their version dependency or you use a debianized rpm (with alien) or you follow the steps here:
[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

---

### Post by Pablo_Escobar on 2005-10-17
You can always try the earlier skype deb - it has been posted around the forum. It works like a charm for me. No need for a bleeding edge in Skype :)

---

### Post by r0nin on 2005-10-17
I just used the static deb from the Skype Webpage, works too. I was just wondering as Opera (and other QT apps I suppose) depends on it too!

---

### Post by pauljwells on 2005-10-24
[http://packages.ubuntu.com/hoary/libs/libqt3c102-mt](http://packages.ubuntu.com/hoary/libs/libqt3c102-mt)

sudo dpkg -i <name of .deb file you just downloaded>

hth

---

### Post by paddy2706 on 2005-11-07
or you just download my repackaged deb from the original deb, with just changed dependencies: [http://www.patrick-brueckner.de/?download=skype_1.2.0.18-1_i386-libqt3-mt.deb](http://www.patrick-brueckner.de/?download=skype_1.2.0.18-1_i386-libqt3-mt.deb)

---

