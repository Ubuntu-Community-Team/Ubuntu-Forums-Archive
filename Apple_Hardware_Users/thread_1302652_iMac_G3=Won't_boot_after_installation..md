---
title: "iMac G3=Won't boot after installation."
date: 2009-10-27
forum: Apple Hardware Users
---

### Post by balebozb on 2009-10-27
Hi Guys,
I've installed 9.04 on a friend's iMac using my iMac via FireWire. Now I can't get it to boot up on my friend's iMac or mine via FireWire either one. It just brings the Stage 1 Grub menu that says something like l=GnuLinux; x=OSX; c=cdrom. It won't boot on any of them. Any help would be appreciated. 
Thanks,
Balebozb:(

---

### Post by eQuk on 2009-10-28
if you choose linux can you get to the second stage? if so at the second stage type 

Linux nosplash

---

### Post by balebozb on 2009-10-28
Well, yesterday I got it to where it was saying loading second stage, but it never got there even after 30 minutes. I just erased the partition and am going to start over. Any tips on how to install this via FireWire?

---

### Post by B_Free on 2009-10-28
Same thing happened to me. If it asks to start from l (as in Linux) or x (as in Mac OSX) you must have a version of  Mac OS on your machine. No matter what I did it would not boot. My only solution was to install [http://old-releases.ubuntu.com/releases/breezy/](http://old-releases.ubuntu.com/releases/breezy/) and then upgrade from there. If you go this route, only download the alternative CD because the live CD doesn't give you the option to install. It sounds old but this version was made around the same time as the machine you are installing it on.

---

