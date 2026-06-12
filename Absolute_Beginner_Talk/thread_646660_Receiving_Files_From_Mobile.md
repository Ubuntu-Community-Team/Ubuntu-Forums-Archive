---
title: "Receiving Files From Mobile"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by steve-shinn on 2007-12-21
Hi,

Does anyone know which KDE pogram I need to install (using Ubuntu 7.10) to allow me to send files from my mobile to the PC using bluetooth.

I am using KBTOBEXCLIENT successfuly to send files to my mobile, but since upgrading to 7.10 from 7.04, can't remember which program to install.


(I had it transferring successfuly on 7.04)

---

### Post by Lord_Dicranius on 2007-12-21
I think kbtobexclient is part of "kdebluetooth".

---

### Post by steve-shinn on 2007-12-21
> **Lord_Dicranius said:**
> I think kbtobexclient is part of "kdebluetooth".

Yep Im using that to send files, but I'm certain that there is another bluetooth program that allows me to receive file from my mobile

---

### Post by briguy on 2007-12-21
KDE has this built in with kdebluetooth, however it is broken on Gutsy (to receive anyways).  There is a fix here (ivoman's post):

[http://ubuntuforums.org/showthread.php?t=611481&highlight=bluetooth+transfer+kde](http://ubuntuforums.org/showthread.php?t=611481&highlight=bluetooth+transfer+kde)

---

### Post by True Rage on 2007-12-27
I had the exact same problem. Everything working fine in Kubuntu 7.04, upgraded to 7.10 and wasn't able anymore to send files via bluetooth to the computer.
First let me complain a bit: I'd like to suggest to the developers that the working features remain working in the most recent releases!

The fix suggested above just did not work for me.

I tried a simpler one which succeded. Briefly: I uninstalled the 7.10 bluetooth packages and installed the 7.04 ones. Now everything is working again!


A more detailed description of the procedure:
I taped "bluetooth" in Adept Manager and uninstalled the related packages:

bluez-utils
kdebluetooth
libbluetooth2
libkbluetooth0

Then I browsed in the ubuntu archives and downloaded the ones that worked in 7.04. In this case I'm picking packages for the i386 architecture:

[http://archive.ubuntu.com/ubuntu/pool/main/b/bluez-utils/bluez-utils_3.9-0ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bluez-utils/bluez-utils_3.9-0ubuntu4_i386.deb) 
[http://archive.ubuntu.com/ubuntu/pool/main/k/kdebluetooth/kdebluetooth_0.99+1.0beta2-1ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kdebluetooth/kdebluetooth_0.99+1.0beta2-1ubuntu5_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/k/kdebluetooth/qobex_0.99+1.0beta1-12ubuntu9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kdebluetooth/qobex_0.99+1.0beta1-12ubuntu9_i386.deb)
I don't remember the path :(, but downloaded also: libbluetooth2_3.9-0ubuntu1_i386.deb

I installed the above packages with gdebi in command line, cause didn't work with the graphic interface: another bug!

You owe me a drink if it works for you as well!
Byez

---

### Post by Biggy on 2007-12-27
search for Blueman is great app..

---

