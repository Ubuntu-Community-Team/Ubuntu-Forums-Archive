---
title: "Updating via EasyUbuntu"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Laalitha on 2006-10-25
I tried to get the codecs and the NVIDIA driver for my Dell Precision M60 laptop using EasyUbuntu. But it gave the following WARNING.

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

Plus an ERROR dialog box saying "Could not apply changes!Fix broken packages first."

Then I tried only to install the flash plugin and the nvidia driver. It went fine but in the end it gave a terminal that has a title bar saying "easyubuntu.in" saying,

automatic installation failed due to network problems or upstream changes
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.


I have ubuntu 6.06 installed.

What do I do?

Thank you

---

### Post by Sarah13 on 2006-10-25
I'm a self-identified noob, so take this with a grain of salt. I had the same exact problem that you had in the beginning, with the NO_PUBKEY [Here]("http://www.ubuntuforums.org/showthread.php?t=283103") is exactly what happened, and the advice I was given. 

What I basically decided to do was try to repair the broken package through Synaptic, but when that didn't work, I decided to remove EasyUbuntu ```
sudo apt-get remove easyubuntu
``` then installed Automatix2 instead. I'm still having trouble with the flash player, but I don't think that's Automatix's fault because everything else has worked wonderfully (including the NVidia driver).

Just from my experience, and the options I was given with Automatix2 in comparison with EasyUbuntu, I definitely recommend Automatix2. You can find it [here]("http://www.getautomatix.com/"), if you're willing to switch.

Hope that helps! And welcome to the forum! I think you'll find that everyone is really helpful here, they've really helped me with Ubuntu.

---

### Post by Laalitha on 2006-10-25
Thank you 

I installed Automatix and I have everything working now

Thanks again Sarah

---

### Post by HandGrenade on 2006-10-25
I had the same problem with EasyUbuntu. After seeing this thread and taking your advice by using Automatix2, everything is working perfectly. Thanks! :mrgreen:

---

### Post by barkej on 2006-10-25
I used to like EasyUbuntu, that is until I tried Automatix2.

---

