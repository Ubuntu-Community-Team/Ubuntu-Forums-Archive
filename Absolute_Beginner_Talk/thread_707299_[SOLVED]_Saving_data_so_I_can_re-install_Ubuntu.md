---
title: "[SOLVED] Saving data so I can re-install Ubuntu"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-02-25
I have a dual boot laptop. Ubuntu and XP. The XP needs to go... I can't stand having that particular malware on my system anymore. 

I have been running 6.06 LTS and it has become corrupted by an update, fubar I believe: my wireless card, ISA bridge, and modem show as 'unclaimed' when I ran lshw

Here is what I want to do: 
I am going to re-install Ubuntu, using the entire HD. I have documents that I have e-mailed to myself, so those are safe. I need to figure out how to save my firefox bookmarks and usernames/passwords.

Emailing files to myself is the only way I can save data. 
Does anyone know how i can do this?

The other option is to save my /home to the partition I will create by overwriting XP. I don't know how to go about this. My live cd is 5.10.

---

### Post by justleen on 2008-02-25
have i look i this guide i made: [http://ubuntuforums.org/showthread.php?t=701386](http://ubuntuforums.org/showthread.php?t=701386)

your best bet would be to create a new partition, and copy/tar everything you want to backup to this partition. You wouldnt need the live cd for creating the new partition, you could do that with gparted if you want to.

---

### Post by Papa-san on 2008-02-25
I don't know how to do that. my boot sector is in my windows partition. Will gparted know to save that out?

---

### Post by Papa-san on 2008-02-25
If I can figure out how to cleanly overwrite the XP partition, can I move my /home to it? 

In gparted, I'm ready to delete hda1. I just need to know if this is the right way to do it because of my boot sector...

---

### Post by Therion on 2008-02-25
You might want to have a look at [QuickBackup](http://ubuntuforums.org/showthread.php?t=613462) for backing up your data, and/or the [Foxmarks](http://www.foxmarks.com/) extension, which allows you to upload your bookmarks to a server for easy retrieval once your new install is complete.

---

### Post by justleen on 2008-02-25
your bootsector is outside any partition. there should be no need to worry about that.

once you have a new partition, you can copy the data to it. when you reisntall, point /home to this partition, and your good to go..

---

### Post by seventhc on 2008-02-25
your bookmarks can be exported in firefox. Bookmarks>Organize Bookmarks>File>Export
It will save them as an html page which you could save to a usb or email to yourself.
For usernames and password, at one of my jobs, the thing I used to do was go to
Edit>Preferences>Security...Show Passwords, then when that box opens click show passwords again, maximize the screen take  a screenshot and save it to my usb.
not saying it's the most secure thing in the world, but it works. Not sure if I would email that to myself though, fine on a usb which you have in your possession and can delete when your finished.

---

### Post by Papa-san on 2008-02-25
Thank you all!

I don't have a usb stick, so I pilfered my daughters mp3 player... Works like a charm! I now have my critical stuff backed up, and have verified it's presence in my wife's computer. (She has the XP virus on it.)
I verified the contents of my CD, and did a memory check... All is good, so I'm going to try my install!

How do I do the thank you thing?

---

### Post by seventhc on 2008-02-25
You can just say *thank you*, or click on the little yellow star.(sort of like a blue ribbon yellow star looking thing)
Good luck with the install. :)

---

