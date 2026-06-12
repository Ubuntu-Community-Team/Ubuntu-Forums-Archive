---
title: "Rhythmbox Songs Dissapearing"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by uhoh_zombies on 2008-03-02
Hello.
I've got Rhythmbox 0.11.2 running in Gutsy 7.10, and for some reason, my songs end up disappearing. 
I cant explain this issue in much detail, but I uploaded from the folders, had everything in my library, and decided to open Rhythmbox today, and suddenly the songs drained [thats the best way to put it] themselves out of the player. I watched the song count go from 5000+ down to 0 in a matter of 30 seconds. 

I re-uploaded a folder of music after this happened, and after getting home, decided to open Rhythmbox again, and the same thing happened.

Is there any explanation or fix for this issue?

Other apps recognize that the files are there, I can find them all.

---

### Post by jeffus_il on 2008-03-02
Sounds like the library may be being loaded from a wrong folder, the speed they disappear at is quite similar to the time a directory scan may last. Check the library folder/s.

---

### Post by uhoh_zombies on 2008-03-02
Yeah. I was going to ask that next.

Could it be a communication/connection issue between the large partition where the music is stored and the smaller partition, on which Ubuntu is contained?

---

### Post by Ian Heathcote on 2008-06-05
Hello, 
     I have the same problem of my songs disappearing. How can I check the library folders. Any suggestions on what I can do to fix this annoying problem.  Cheers

---

### Post by erginemr on 2008-06-05
Can this problem be elated to the fact that in Hardy Heron, NTFS, FAT32, etc. Windows-centric drives are not mounted on boot, but are mounted on demand?

Are these music files dwelling on a Windows partition? If so, do they reappear when you open "Computer" from the Gnome menu and double-click on the drives in question to mount them manually?

---

### Post by Ian Heathcote on 2008-06-10
How do I access the Gnome menu to check this:  If "these music files dwelling on a Windows partition? If so, do they reappear when you open "Computer" from the Gnome menu and double-click on the drives in question to mount them manually?

Thanks

---

### Post by erginemr on 2008-06-10
You are welcome. Provided that your music files are located under an "ntfs" (windows) partition, you can have it auto-mounted by installing the package "ntts-config". From a terminal (Alt+F2 -> gnome-terminal):
```
asuo aptitude install ntfs-config
```
Then run the config tool with:
```
Alt+F2 -> gksu ntfs-config
```
Tick the check-boxes beside the two options, restart your computer and you should be all set. 

Enabling these options will allow the ntfs-config tool to put the corresponding lines in your "/etc/fstab" file and will auto-mount the ntfs drives, thus your music players will "see" the files in their libraries.

---

