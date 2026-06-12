---
title: "Trouble removing files from camera flash card."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-05-15
I'm running Feisty and have a flash card, in a card reader, in a USB port.

What I am trying to do is to remove some files ( .jpg )  from the flash card but I have been unable to find an option to do this.

When I right click on the file,  the ' Move to trash' option is not available.  If I try to drag the files to 'Trash', I get, "Cannot move items to trash, do you want to delete them immediately?"

If I take the default option I get, "Unable to move to trash: Read only file system."

Is there something simple I'm missing here?

---

### Post by oilchangeguy on 2007-05-15
don't have my card reader hooked up right now, so i can't check it. but can't you just delete the pics while the card is in the camera? or are there too many for this to be a fesible option?

---

### Post by Grungydan on 2007-05-15
It sounds like perhaps the card is formatted in NTFS or something.  You could try installing/enabling NTFS support in Ubuntu (you can find this in Add/Remove; apologies, I forget the exact package name).

Alternatively, you could launch a file browser as root (gksudo nautilus) and try to trash them from there.

---

### Post by L Campbell on 2007-05-15
> **oilchangeguy said:**
> don't have my card reader hooked up right now, so i can't check it. but can't you just delete the pics while the card is in the camera? or are there too many for this to be a fesible option?

Well, here's the story.

Its my girlfriend's camera and her card.  She was unable to delete the files, either in her camera or with Win XP.

Right away I saw my big opportunity and told her it would be a snap to do with Feisty.  That was yesterday and I still haven't got it done.   :-(

---

### Post by oilchangeguy on 2007-05-15
> **L Campbell said:**
> Well, here's the story.

Its my girlfriend's camera and her card.  She was unable to delete the files, either in her camera or with Win XP.

Right away I saw my big opportunity and told her it would be a snap to do with Feisty.  That was yesterday and I still haven't got it done.   :-(

sounds like a bad card. using windows, insert the card in the reader. open my computer, right click on whatever drive the card reader is, click on properties. if the card shows full (blue) it's probably no good.

---

### Post by L Campbell on 2007-05-15
> **Grungydan said:**
> It sounds like perhaps the card is formatted in NTFS or something.  You could try installing/enabling NTFS support in Ubuntu (you can find this in Add/Remove; apologies, I forget the exact package name).

Alternatively, you could launch a file browser as root (gksudo nautilus) and try to trash them from there.

Thanks.  

I think I must have done something wrong?

qwer@qwer-desktop:~$ gksudo nautilus
(nautilus:6640): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by netwerx on 2007-05-15
My camera works fine, as well as my card reader for these functions.

May I suggest the card itself may be faulty.  If you have another card, i suggest you try that.

Also wouldn't hurt to format the card in the camera to refresh the file structure.
(Make sure you grab the contents first.)

If your card was formatted NTFS (as someone suggested) i doubt it would function in the camera.

---

### Post by L Campbell on 2007-05-15
> **oilchangeguy said:**
> sounds like a bad card. using windows, insert the card in the reader. open my computer, right click on whatever drive the card reader is, click on properties. if the card shows full (blue) it's probably no good.

Great, I'm making some progress now. 

The card and reader work fine in my XP machine but when I try to delete a file, it tells me that the card is 'write protected'.

I'm not sure if I can fix that in my XP machine or if I need to get back into her camera to do it.

Kind regards.

---

### Post by lazyart on 2007-05-15
The card should have a little slider on one of the edges that is used to set write protect.

---

### Post by jhenager on 2007-05-15
> **lazyart said:**
> The card should have a little slider on one of the edges that is used to set write protect.

Doh! - another example of the simple solution getting overlooked.

---

### Post by L Campbell on 2007-05-15
> **lazyart said:**
> The card should have a little slider on one of the edges that is used to set write protect.

Thanks, thats a pretty tiny slider.   :-)

Anyway, I tried it in both positions, in both my XP machine and Feisty but still cannot delete anything.

---

