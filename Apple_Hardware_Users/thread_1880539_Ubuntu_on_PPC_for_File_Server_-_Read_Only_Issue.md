---
title: "Ubuntu on PPC for File Server - Read Only Issue"
date: 2011-11-13
forum: Apple Hardware Users
---

### Post by jbsmith05 on 2011-11-13
Hello,
I just re-installed 10.04 on an old PowerMac G4 to be used primarily as a file server.  The machine has a handful of drives which by default are not mounted upon boot.

I am sharing with other Mac's in the house... primarily a macbook pro running os x 10.7 lion.  On the Ubuntu box I have installed netatalk and have it configured correctly so the Ubuntu box shows up in the Finder on the Mac.

Being that I assume this machine will need to be rebooted from time to time, I wanted the drives to automatically mount - so I installed pysdm (Storage Device Manager) and configured those two drives.  After doing so on the Mac I am now only able to read the drives instead of read/write.

Is there something I am doing wrong?  Or a better way to automount disks that allow the mac's to read/write?  

Keep in mind I am very new to Ubuntu and Linux (like one day)!!

Thanks.

---

### Post by Hatsune Miku on 2011-11-14
> **jbsmith05 said:**
> Hello,
I just re-installed 10.04 on an old PowerMac G4 to be used primarily as a file server.  The machine has a handful of drives which by default are not mounted upon boot.

I am sharing with other Mac's in the house... primarily a macbook pro running os x 10.7 lion.  On the Ubuntu box I have installed netatalk and have it configured correctly so the Ubuntu box shows up in the Finder on the Mac.

Being that I assume this machine will need to be rebooted from time to time, I wanted the drives to automatically mount - so I installed pysdm (Storage Device Manager) and configured those two drives.  After doing so on the Mac I am now only able to read the drives instead of read/write.

Is there something I am doing wrong?  Or a better way to automount disks that allow the mac's to read/write?  

Keep in mind I am very new to Ubuntu and Linux (like one day)!!

Thanks.

Netatalk does not support OS X Lion yet, It is still in its early betas. I recommend installing Mac OS X and using that for the file server. If you really insist on using ubuntu, i recommend you learn to to use FTP instead of AFP.

---

### Post by jbsmith05 on 2011-11-14
> **Hatsune Miku said:**
> Netatalk does not support OS X Lion yet, It is still in its early betas. I recommend installing Mac OS X and using that for the file server. If you really insist on using ubuntu, i recommend you learn to to use FTP instead of AFP.

Actually it works just fine.  I got it working late last night after I reinstalled Ubuntu.  I am not sure what caused the read only issue but I can assure you that netatalk does work fine with osx 10.7. 

I am using Linux on a g4 because I had the tower and some empty hdd's...I didn't want to buy osx tiger or leopard, if Ubuntu would work for free.

---

### Post by Hatsune Miku on 2011-11-14
> **jbsmith05 said:**
> Actually it works just fine.  I got it working late last night after I reinstalled Ubuntu.  I am not sure what caused the read only issue but I can assure you that netatalk does work fine with osx 10.7. 

I am using Linux on a g4 because I had the tower and some empty hdd's...I didn't want to buy osx tiger or leopard, if Ubuntu would work for free.

Apple is basically throwing leopard out to PowerPC users. If you go to your apple store i think they will just give you a leopard disc man. :popcorn:

---

### Post by jbsmith05 on 2011-11-14
> **Hatsune Miku said:**
> Apple is basically throwing leopard out to PowerPC users. If you go to your apple store i think they will just give you a leopard disc man. :popcorn:
 
 
Really - first I have heard of that?  Why would they?  I'll give it a shot though.

---

### Post by Hatsune Miku on 2011-11-15
> **jbsmith05 said:**
> Really - first I have heard of that?  Why would they?  I'll give it a shot though.

Because they really cant make any money of leopard anymore :p

---

