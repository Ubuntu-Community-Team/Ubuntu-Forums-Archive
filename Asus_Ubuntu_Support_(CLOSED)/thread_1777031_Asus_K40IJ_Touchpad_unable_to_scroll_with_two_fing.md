---
title: "Asus K40IJ Touchpad unable to scroll with two fingers"
date: 2011-06-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by razzihaider on 2011-06-07
I am having problem with My touch Pad, i am unable to scroll up or down in a web page or in any window, however it was working in previous version of ubuntu. Now i am using **UBUNTU 11.04**
please help me to solve this issue.

Secondly, 2 of my NTFS file systems are not showing in computer, whereas 1 NTFS is visible and is mountable. Also guide me for this also, NTFS-3g is already installed.

previous version was better than this one, this has problems like i am having

Thanking you in advance

---

### Post by amitp85 on 2011-06-07
1. Go to System->Preferences->Mouse: On TouchPad tab Choose "Two-Finger Scrolling".


2. Open System->Administration->Disk Utilty: 
    1. Check the device name of your HDD partitions /dev/sdXX in disk utility.
    2. Create directories for your drives somewher in /home/<our-user> or in / e.g vol1, vol2 etc
    3. use mount command to mount your drive on new created directory. e.g sudo mount /dev/sda2 /vol2
    4. Edit your /etc/fstab to mount your drives at startup.

Regards
amitp

---

### Post by fi2 on 2011-06-11
Same problem with K53SV touchpad. I Use the multitouch on a Toshiba Satellite and 11.04, but so fur no luck with the Asus. Does anybody know where to get a decent multitouch driver?

---

