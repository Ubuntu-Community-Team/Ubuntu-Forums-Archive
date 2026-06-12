---
title: "Problem downloading packages"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by Lasastard on 2006-03-03
Hello everyone,

I wasnt able to find an answer to this particular problem / so probably one of you can help me out...

Whenever I try to install certain packages (i.e. german language support files) I keep running into the same problem (with both synaptic and apt-get)

Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

I updated the server-list and so on, but it keeps asking for a cd - instead of downloading the stuff from a web server. I was able to install other packages via apt-get just fine (i.e. perl-tk) - but for others I keep getting this message...


Any Ideas?

---

### Post by eriefisher on 2006-03-03
Can you comment(#) out the line with cdrom.
What happen if you put the disc in?

eriefisher

---

### Post by jamyskis on 2006-03-03
Did you not get the Ubuntu CD? The most important packages (including some German language support) are found on the CD and you just have to insert it and click OK.

I have a sneaking suspicion that if you go under Settings (Einstellungen), then Package Sources, and then uncheck CD Ubuntu 5.10 as a source, click OK and then try again, it might try to download the packages from the Ubuntu repositories. I can't try that here though at the moment as I already have German installed.

---

### Post by Lasastard on 2006-03-03
well maybe I should have added that I am using ubuntu virtual appliance from
[http://www.vmware.com/vmtn/appliances/ubuntu.html](http://www.vmware.com/vmtn/appliances/ubuntu.html)

Which means : no I dont have a cd

---

### Post by Lasastard on 2006-03-03
removing  cdrom from the sourcelist seems to work, thx :-k

---

### Post by jamyskis on 2006-03-03
Ahhhhhh right!

In that case just go into Synaptic, uncheck the CD source and try again - it should be alright then. Viel Glück!

---

