---
title: "Desktop PC Just died (I think)"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Liet_Kynes on 2008-02-04
I was busy installing ubunty 7.04 from the live cd. At the part where it was installing the system somewhere after 74% the installer just disappeared and didn't give the message to restart the pc.

I ran top in a terminal to see if anything was still happening in the background but nothing. And then the system froze. When i tried to reboot I got garbled images in my boot screen (The bios one) After shutting down at the power and then restarting i'm trying to reinstall but now the same disc is giving me the error "unknown keyword in config file".

Occasionally it goes past this part but then hangs when it reaches the desktop.

Help please.

---

### Post by jaytek13 on 2008-02-04
It might be best to download the alternate cd and try that instead. Otherwise who knows what happened... How much RAM do you have?

---

### Post by Liet_Kynes on 2008-02-04
I have installed ubuntu on this pc from the same cd before.

I am running an AMD3200+ and 2G ram (ddr400)


PS: I just got back into the live cd desktop i did the following.

tail -f /var/log/messages

to see what was happening.

There seems to be a bad sector on the harddrive. Is there a utility i can use from the live system to fix since I don't have access to windows to run chkdsk as they tell me to.

---

### Post by mikeyphi on 2008-02-04
You could try - use Synaptic to download 'testdisk' - see what results you get.

---

### Post by dward526 on 2008-02-04
try 'fdisk' from the live cd, never used it but worth a shot.  Other wise you can use a DOS based boot disk and run 'fdisk' at command prompt.

---

### Post by aeiah on 2008-02-04
if you can get the livecd to run you could always check things with gparted or the command line partition manager. i think gparted can fix some bad bits, if its data corruption. the gparted livecd is always more up to date if you prefer trying that.

testdisk sounds like a good option though to check for mechanical/physical errors

---

### Post by Liet_Kynes on 2008-02-04
Any other utilities for fixing HDs from linux. testdisk is only checking the consistency of the partition table

---

