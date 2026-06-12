---
title: "Transferring Files"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by CaptainMorgan on 2005-11-29
Howdy,

I have enormous quantities of files/folders/documents that over on Vindoze Xpee... mostly an assortment of .pdf, .doc, .xls, others that I can't think of at this time. How do I transfer over this stuff so I can work on it in Linux? I know they'll be opened with Linux's version of software for the type of file. I tried using an email to temporarily store a few and when I got back into LInux, I couldn't open any of the various files... it wouldn't even download. 

Thanks

---

### Post by cwaldbieser on 2005-11-29
[QUOTE=CaptainMorgan]Howdy,

I have enormous quantities of files/folders/documents that over on Vindoze Xpee... mostly an assortment of .pdf, .doc, .xls, others that I can't think of at this time. How do I transfer over this stuff so I can work on it in Linux? I know they'll be opened with Linux's version of software for the type of file. I tried using an email to temporarily store a few and when I got back into LInux, I couldn't open any of the various files... it wouldn't even download. 

Thanks[/QUOTE]
If WinXP is on the same PC, you can just mount the NTFS partition from Ubuntu and copy the files over.

If they are different PCs on the same network, you could ftp or scp the files over (it is pretty easy to get sshd up and running on Ubuntu).

---

### Post by CaptainMorgan on 2005-11-29
[QUOTE=cwaldbieser]If WinXP is on the same PC, you can just mount the NTFS partition from Ubuntu and copy the files over.

If they are different PCs on the same network, you could ftp or scp the files over (it is pretty easy to get sshd up and running on Ubuntu).[/QUOTE]


K, Ive heard of mounting drives, dvd players, cd's, etc.. but not a full NTFS partition... can you point me in the right direction? Is it that simple? You mount it and then they can be easily copied? 

thanks

---

### Post by somody on 2005-11-29
As simple as a mount command from the terminal ;).

---

### Post by CaptainMorgan on 2005-11-29
[QUOTE=somody]As simple as a mount command from the terminal ;).[/QUOTE]


any links you point me to ? 


thanks

---

### Post by akiro.yamamoto on 2005-11-29
Hey Cap :smile:
Try this link for any easy guide....(Not this guide is a bit dated but the relevant info is still useful)
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Hope this helps

---

### Post by akiro.yamamoto on 2005-11-29
He assumes that /dev/hda1 is the NTFS (Windows) partition...
The dev scheme for partitions goes something like this...... Hmmmm
Master Driver on the first IDE channel ====>HDA
1st partition Master IDE Drive =========> hda1
2nd part. Mast Dr. ================>hda2 ....etc..
2nd Drive =====================> HDB
1st part 2nd drive ================> hdb1 etc....
Hope this helps...

---

### Post by raghav_p on 2005-11-29
I believe this is the "new" guide:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions)

from here, you should be able to mount your NTFS partition correctly.

------
sorry.. was too late in posting ;-)

---

### Post by akiro.yamamoto on 2005-11-29
Thanks raghav_p didn't have that link bookmarked... :smile:
The one I posted is from memory :smile:
LOL

---

### Post by somody on 2005-11-29
my second hdd is recognized as "hdab" for some reason...but w/e

---

### Post by CaptainMorgan on 2005-11-30
Wow, that guide looks great... thank you.


It seemed simple enough.. however, after mounting, then navigating to the folder, most of my folders can't be seen and most files in visible folders aren't there.. are they hidden? or? 

Also, after mounting... do I ever need to unmount? or could I leave it as is? Im think maybe it unmounts automatically after shutting down? 

thanks folks

---

### Post by CaptainMorgan on 2005-11-30
Sorry..

I can access the files via a gui.. but I originally tried via the command line.. why can't I access them via command line?

btw, this is awesome!!

---

