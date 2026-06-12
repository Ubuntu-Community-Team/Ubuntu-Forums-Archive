---
title: "Ejecting zip disk gives me error message but..."
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by SlappyPappy on 2008-04-12
On a whim and to see if Ubuntu can handle everything I throw at it I connected an old USB zip drive. I popped in a disk and it read it beautifully. Cute zip disk icon on the desktop and all. 

I copied some files to it and then ejected it. After it ejected a warning message came up telling me to not eject the disk as it was being written too. I put the disk back in and all the files were there and opened up fine. No harm, no foul.

Is this just a bug or should I worry about actually using a zip disk to backup some of my writing files?

Thanks for the help lads.  :)

---

### Post by Gen2ly on 2008-04-12
To some degree gnome-volume-manager tries to work intuitively.  It does this well for flash drives but I'm thinking it's functionality isn't as complete for zip (which is too bad it doesn't need to be.)  What gnome-volume-manager does is display a "Writing to Drive" if the information isn't done for transfer." Either the zip drive doesn't have a feedback to tell gnome-volume-manager when the transfer is down (or a stop to prevent it) or gvn doesn't have a proper check (probably the later).  Too bad too, I have a zip drive, and I liked it a lot.

---

### Post by SlappyPappy on 2008-04-12
Cool thanks for the help Dirk.

I just tried what you said with a USB key drive and you're right. 

Mind you I'm not complaining about erroneous error messages as I'm just glad my zip drive is recognized automagically.

Be safe on your side of the world dude.

---

### Post by Gen2ly on 2008-04-13
Thanks slappy.  :)

I found out that this is actually a behavior that can be turned off in nautilus.  It looks like Gnomes newvirtual filesystem (gvfs) has something to do with this and possibly not gnome volumemanager.

---

