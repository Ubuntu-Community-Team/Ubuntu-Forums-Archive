---
title: "Canon printer"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by pule on 2005-11-17
I'm an absolute beginner with Linux and Ubuntu, I've read some of the hints in this forum about installing a printer but I can't find my printer model in the list of the Canon devices supported. My model is a PIXMA IP1500: which driver should I choose? I'll be eternally grateful ( ;) ) to anyone who gives me help!

---

### Post by canadianwriterman on 2005-11-17
I Googled your printer and came across the following from the SUSE Linux Forum that I think will work for you:

[http://forums.suselinuxsupport.de/index.php?showtopic=22863](http://forums.suselinuxsupport.de/index.php?showtopic=22863)

---

### Post by canadianwriterman on 2005-11-17
I just noticed that the Canon files are RPMs. I'm not sure of a good way to convert the RMP files to DEBS. Can anyone else help with that?

---

### Post by Tiede on 2005-11-17
maybe [this one](http://software.canon-europe.com/software/canon_print_filter_for_linuxs22415.asp?model=)

---

### Post by matthewv on 2005-11-17
[QUOTE=canadianwriterman]I just noticed that the Canon files are RPMs. I'm not sure of a good way to convert the RMP files to DEBS. Can anyone else help with that?[/QUOTE]
To install RPMs do the following: 
install alien (from synaptic or sudo apt-get install alien)
then type ```

alien <file.rpm>
sudo dpkg -i <file.deb>

```
Alien will create a .deb that can be installed via dpkg.

---

### Post by pule on 2005-11-17
[QUOTE=canadianwriterman]I Googled your printer and came across the following from the SUSE Linux Forum that I think will work for you:

[http://forums.suselinuxsupport.de/index.php?showtopic=22863](http://forums.suselinuxsupport.de/index.php?showtopic=22863)[/QUOTE]
I also found this driver but I didn't know if it could be used under a different distribution...thank you! Then...I'm going to try it out, and wishing well!

---

### Post by pule on 2005-11-18
Damn! It still don't work...but maybe I'm wrong somewhere. Here's what I did: I followed matthewv's instructions to convert all the RPM packages I found in the link to DEB, then I installed them with DPKG. What am I doing next? It still does not recognize the printer model in the list of Canon devices...perhaps it's really a piece of cake, but keep in mind this is my first experience with Linux and Ubuntu...Please help me!

---

### Post by pule on 2005-11-20
OK!!! Now it works! Thank you all for your precious support!!

---

### Post by FireFoxx on 2005-11-20
I have the same printer as you I clicked the link and the site can't be found I was wndering if you might be able to e-mail the files to me please

thanks 

[email]matthew12396@yahoo.co.uk[/email]

---

