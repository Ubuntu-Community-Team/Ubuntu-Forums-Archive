---
title: "help me install ubuntu without cd-rom"
date: 2006-11-12
forum: Apple PPC Users
---

### Post by midgetinabikini on 2006-11-12
i have an old laptop, powerbook G3 640mb sdram and 20g hardrive. 
the laptop doesnt have CDrom device in it.

im trying to install kubuntu 6.10 but without any luck. 

now im running osx 10.3.9

please help me :-(

---

### Post by TLE on 2006-11-12
How did you try to install it?
What options are there to get access to the laptop, floppy-drive, network?

---

### Post by midgetinabikini on 2006-11-12
i copied the 4 files in the menual to the root partation, and used the openfirmware to load it, but i got error message.

i have extarnel firewire hard-disk with some free space. no floppy and no network.

---

### Post by midgetinabikini on 2006-11-12
and i have 256mb disk on a key that i just found...

---

### Post by TLE on 2006-11-12
> i copied the 4 files in the menual to the root partation, and used the openfirmware to load it, but i got error message.
Please give a little more information. Did you do that as a part of some guide and if so please post the link!

Try and have a look [here]("https://help.ubuntu.com/community/Installation"). Under the advanced section there are some different guides on special installs but there does not seem to be one that exactly matches your problem. Could USB be an option?

---

### Post by midgetinabikini on 2006-11-12
this menual: 
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-drive-files.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-drive-files.html)

and how can i easly config usb device to do that? i found my old 256mb usb.

---

### Post by TLE on 2006-11-12
> **midgetinabikini said:**
> 
and how can i easly config usb device to do that? i found my old 256mb usb.
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by midgetinabikini on 2006-11-12
my usb stick is only 256mb...and the menual you gave me is for windows, im using osx 10.3

---

### Post by TLE on 2006-11-12
I don't think I have enough knowledge to be able to help you with this. I hope somebody else will fill in. Otherwise if no-one else replies after some time you will have to re-post. But if you do PLEASE include all the necessary information in the original post otherwise you wont get many replies

---

### Post by xfile087 on 2006-11-23
If anyone else reads this thread then I will just mention that I got the net boot to boot on my iBook G4 using Open Firmware and successfully installed Ubuntu 6.10 on it without the use of a CD drive so if anyone needs help - PM me.

---

### Post by yorklee70 on 2006-11-27
> **xfile087 said:**
> If anyone else reads this thread then I will just mention that I got the net boot to boot on my iBook G4 using Open Firmware and successfully installed Ubuntu 6.10 on it without the use of a CD drive so if anyone needs help - PM me.

I have a PowerBook G4, but the cd-rom was broken, network is ok. Now there is a Debian Linux on it. /boot on hda2, swap on hda3, / on hda4, /home on hda5. I want to replace Debian with Ubuntu 6.10., could you please show me how to do it? Thanks very much.

---

### Post by dpny on 2006-11-27
> **midgetinabikini said:**
> i copied the 4 files in the menual to the root partation, and used the openfirmware to load it, but i got error message.

I tried to do this when I was having problems installing. That method only works if the partition is formatted with HFS. Your partition is probably HFS+.

---

