---
title: "No Sound - AC'97 Audio Controller"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by rlozano on 2006-11-08
[HTML]Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FR W (ICH6 Family) AC'97 Audio Controller (rev 04)[/HTML]

anybody using this type of embedded sound card? i would appreciate if you can share how you managed to make it work. ](*,) 

thanks in advance.

---

### Post by ReaderRat on 2006-11-08
This may help:
**[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**

---

### Post by Sef on 2006-11-08
Here's how I got mine sound working:

sudo gedit /etc/apt/sources.list

You should see something similar to this:

> # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

(There may be two more line added in Edgy.)

Then comment out the lines (both the one shown here and the two new ones in Edgy, and change the 2 to a 0 (zero).)

> # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
# options snd-intel8x0m index=-2
options snd-via82xx-modem index=-0

---

### Post by ReaderRat on 2006-11-08
Here is info on that audio controller, the kernel needed, and what to do.(Scroll down page to Alsa-sound configuration.)
**[[b][url]http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide]([b][url]http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**[/url][/b]


EDIT: Nevermind....Sef knows best...

---

### Post by rlozano on 2006-11-08
thanks so much guys. i will try this one by one.... :-k

---

