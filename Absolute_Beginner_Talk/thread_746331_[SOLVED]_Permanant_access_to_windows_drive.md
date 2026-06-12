---
title: "[SOLVED] Permanant access to windows drive?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Mehashi on 2008-04-05
[color="#ff22ff"]Hey Guys![/color]

I currently have my ubuntu on a 40gb hard drive of its own, 60gb for windows on a partition of another drive and 100gb file storage (in ntfs) as the rest of that second hard drive.

I can access the file storage and windows partitions ok and seem to be able to watch films etc off them fine. What I would like to do is add the file storage partition to my desktop as a permanent shortcut, preferably without having to give permission all the time. (I have a friend I would like to allow to use the pc to watch movies but they should not be trusted with sudo password - ambitious novice!)

Any help appreciated!
^_^

---

### Post by TeoBigusGeekus on 2008-04-05
Go to Synaptic and make sure you have ntfs-3g and ntfs-config installed.
After that, go to Applications->System Tools->Ntfs Configuration Tool
Check your drive and check all the available boxes (enable support..) as well.

---

### Post by Mehashi on 2008-04-05
Thank you! 
I have tried this and it has worked for my windows partition, but does not see the file storage partition as a seperate drive (logically!). Would it work now that the windows drive is set, to change the mount point in the storage partitions properties manually? I'll try this as now that the windows drive is set,it doesnt give me detect drive option anymore!
Thank you!
^_^

---

### Post by Mehashi on 2008-04-12
[color="#ff22ff"]Kon'ban wa![/color]
Thank you for the help!
 
To keep you updated, after a full shutdown and restart, I detected the second partition (100gig) of the second drive by following the same steps again. All works fine now, and I dont have to give my friend (potentially dangerous) sudo access!
 
It seems strange that both partitions were not detected simultaneously, but rather one after the other, but with the system working I am not complaining!
 
[color="#ff22ff"]Arigato gozaimasu![/color]
Thank you!
 
^_^

---

