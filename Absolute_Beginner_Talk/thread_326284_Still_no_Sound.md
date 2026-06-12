---
title: "Still no Sound"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by JParkus on 2006-12-27
ive been trying for last few days to get sound im completely new to linux i have dapper on my    computer on board sound ive tried installing alsa with no luck and i keep getting the error

No volume control GStreamer plugins and/or devices found.

im assuming this means its not muted when i try installing alsa i get the following screen

parkus@parkus:~$ sudo apt-get install libasound2 alsa-utils alsa-oss
Reading package lists... Done
Building dependency tree... Done
libasound2 is already the newest version.
alsa-utils is already the newest version.
Package alsa-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package alsa-oss has no installation candidate
parkus@parkus:~$



what am i doing wrong?

---

### Post by dannyboy79 on 2006-12-27
when you type in alsamixer within a terminal, when the gui comes up, is there anyything that is muted? also, have you followed the sound troubleshooting guide within these forums? that'll help you figure it out!

---

### Post by JParkus on 2006-12-27
alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by logos34 on 2006-12-27
enable universe repository, then try alsa-oss again

---

### Post by dannyboy79 on 2006-12-27
Go to a shell and type: aplay -l 
Success - You will get a list of the all the soundcards installed on your system. Your sound just might be muted. See alsamixer section. 
Failure - You will get a message like aplay: device_list:221: no soundcard found... Move on to step 2. 
Type this into the shell: lspci -v 
Success - At this point, you should see your sound card listed. This is a positive sign because it means that Ubuntu is detecting the presence of your soundcard, but the drivers are not installed/running. Leave your shell running since you will need it. 
Failure - If it is not listed, then there are a few things that you can do. 
If your soundcard is an onboard sound card, then it might be disabled in the system's BIOS. You will have to reboot and hit the key that lets you enter into the BIOS (usually Delete, F2, or F8). 
If your soundcard is not onboard, make sure that it is properly seated in the PCI slot. If your card is working under Windows then this is not a problem. 
Check to see if the ALSA driver for your sound card exists. Go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and search for your sound card (chipset) manufacturer in the dropdown box. You'll be given a matrix of the sound cards made by the manufacturer. Try to match the chipset you found in step 2 with the driver(green hyperlink text). 
Success - You will have found the driver for your soundcard's chipset. 
Failure - You will have not found the driver for your soundcard chipset. (at the moment I cannot help you, but stay tuned!)

this is all found here: [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by OldTimeTech on 2006-12-27
I also noted this in your first post:
"No volume control GStreamer plugins and/or devices found."

You might go to synaptic and find Gstreamer and install it and all it's susequent packages it requires....might help.

---

### Post by dannyboy79 on 2006-12-27
that's not going to help if alsa can't find any devices. he needs to follow the comprehensive sound guide. it has step by step trouble shooting.

---

