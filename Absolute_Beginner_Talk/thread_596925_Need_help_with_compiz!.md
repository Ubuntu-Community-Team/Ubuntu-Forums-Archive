---
title: "Need help with compiz!"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Pecster on 2007-10-30
i don't talk very much english but i hope i make myself clear :) 
i got my cpu upgraded to gg and i cant make compiz to work, i used to have feisty with beryl an it worked fine..
i search for answers but couldn't find any...

i went to my terminal and write compiz and i got this:

eduardo@eduardo:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 


my Nvidia card is an NV34M [GeForce FX Go5200 64M]

TY very much!!

greeting form Mexico!!  :)

---

### Post by mikewhatever on 2007-10-30
Have you installed the nvidia driver? What does glxinfo has to say?

---

### Post by Pecster on 2007-10-30
eduardo@eduardo:~$ glxinfo | grep direct
direct rendering: Yes

i that what you mean??
tankyou very much!

---

### Post by Pecster on 2007-10-30
i followed this wiki but it didn't work :( 
([http://phorolinux.com/how-to-install...sy-gibbon.html](http://phorolinux.com/how-to-install...sy-gibbon.html) ) 

yes i think i did install my nvidia driver..

---

