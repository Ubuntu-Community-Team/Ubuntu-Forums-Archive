---
title: "Installing New Nvidia Drivers after new install"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by sirspectre on 2008-02-12
Hello,

I just decided to make a dual boot of Ubuntu with my XP installation. Got Ubuntu installed without a problem. Now when I go to enable my graphics drivers through the restricted drivers, it gives me a

nvidia-glx-new
is not enabled.

Error. Ok, fine. Lets try Envy. Download..and "Error: Dependency is not satisfiable: xserver-xorg-dev"

Well *four letter word here*

Terminal time. Download Nvidia drivers from site. Followed the Sh filename command. Nothing. "command unknown" Ok...."sudo filename"  insert password..ok cool maybe...nope. After i enter a password..." command unknown." 

Im stuck. No idea what to do now.

---

### Post by jhenager on 2008-02-12
Try Add Remove.
sudo filename would just try to run 'filename' under the superuser profile, and unless you have a script called filename, I'd expect that error message.

---

### Post by jhenager on 2008-02-12
Or just System>Administration>Restricted Drivers Manager.

---

### Post by sirspectre on 2008-02-12
I just tried Add/Remove.  Every time I try to install the drivers there I get 
" The list of applications is not available: Click on 'Reload' to load it. To reload the list you need a working internet connection. "

I do this then I just get an endless loop of trying to install it and refreshing.

The Restricted drivers method does not work. I get an error when trying to enable it.

---

### Post by oldos2er on 2008-02-12
Go to System, Administration, Software Sources, and enable all the sources by checking the boxes.

---

### Post by sirspectre on 2008-02-12
I've been google-ing this for a while. I keep hearing about "Gutsy." Is this something i should look into? What is it?

---

### Post by DJiNN on 2008-02-12
> **sirspectre said:**
> I've been google-ing this for a while. I keep hearing about "Gutsy." Is this something i should look into? What is it?

Gutsy is the latest (7.10) version of Ubuntu, which i had assumed you were running? :) If not, what version of Ubuntu are you using, do you know?

---

### Post by FuturePilot on 2008-02-12
Go System&#8594;Administration&#8594;Software Sources. Check all of the boxes in the first tab there. Uncheck the CD-ROM if it happens to be checked. Then go to the Updates tab and check the first two and optionally the fourth. Click Close then Reload when prompted. Then try the Restricted Driver Manager again.

---

### Post by sirspectre on 2008-02-12
> **oldos2er said:**
> Go to System, Administration, Software Sources, and enable all the sources by checking the boxes.

That Did it. :popcorn: Thank you very much :)

---

