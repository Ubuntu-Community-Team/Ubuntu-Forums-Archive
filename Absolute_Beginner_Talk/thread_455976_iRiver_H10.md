---
title: "iRiver H10"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Kemical on 2007-05-27
I have a iRiver H10 20GB MP3Player. When I used windows, it required WMP10 to either sync the files or even recognize it as a USB device in My Computer. Well since WMP10 isn't on Ubuntu, is it still possible to put music to and from my iRiver?

---

### Post by Kobalt on 2007-05-27
It is likely yes. Have you tried already ? What happens if you plug it in ?
Is this device working like an iPod : does it uses its own folder management or is it like a regular MP3 player that uses a classical folder "tree structure" ? If it's the classical way then you can just drag'n'drop the folders and you're done...

---

### Post by Kemical on 2007-05-27
If I plug it in, nothing happens. It doesn't pick it up as a USB device, it's as if its not even plugged in. On windows if WMP10 was installed I could access it via My Computer >> iRiver HDD >> Music or I could transfer the files via WMP10. However, if WMP10 was not installed it couldn't do either of them.

---

### Post by mozetti on 2007-05-27
Check here: [http://ubuntuforums.org/showthread.php?p=2699057#post2699057](http://ubuntuforums.org/showthread.php?p=2699057#post2699057)

---

### Post by Kemical on 2007-05-27
I checked out MisticRiver, however, it did not help me, and I still haven't got it working. Is it possible to make it view the H10 as a USB device?

---

### Post by Kobalt on 2007-05-27
Please don't double post then Kemical...
When you plug it in and run *lsusb*, do you see it in the list ?

---

### Post by ntetreau on 2007-05-27
Your device is most likely a MTP device.  On feisty install libmtp, gnomad2 and amarok.  Gnomad2 using synaptic can be used my itself to create playlist, transfer files, etc.  In amarok, you can enable mtp transfer through the Device options.  Amarok can also do playlist, album art, music, etc.

Nic

---

### Post by Kemical on 2007-05-27
Is there any way of using it as a non MTP device or possible transferring via Rythm Box?

---

### Post by mozetti on 2007-05-27
I don't have an H10, but I'm pretty sure there is a "UMS trick" that is detailed on MisticRiver that basically changes it from MTP to UMS. I'm not sure if this is a temporary or permanent change. Also, I believe someone at MisticRiver wrote a program to sync/update the H10, but I don't know if it's Windows or Linux.

Go back to MisticRiver, do some searching and some browsing. I'm pretty sure the answer you need is in the forums there.

**EDIT**

I just realized that you're the same person we tried to help over at MisticRiver. From the thread there, it looks like you should have everything you need.

---

### Post by Kemical on 2007-05-27
Actually, the information given made my terminal crash and I needed a fresh install of Ubuntu 7.04. So I don't understand how it was useful.

---

### Post by DeadEyes on 2007-05-31
I don't know what was said in MisticRiver and I'm to lazy to search, but this is what I do:
Plug in the H10 and turn it on. I then hold down the O button and quickly pull out and plug back in the cable, this causes it to reboot in emergency mode keep the O button pressed till it's finished.
The player should now be mounted in UMS mode and files can be copied. Finally I use easyh10 to update the players db.
Probably not very helpful but at least you know it can be done.

This libmtp sounds interest, I must check it out later.

---

