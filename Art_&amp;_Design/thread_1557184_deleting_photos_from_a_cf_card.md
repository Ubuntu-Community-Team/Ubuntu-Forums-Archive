---
title: "deleting photos from a cf card"
date: 2010-08-20
forum: Art &amp; Design
---

### Post by jsstn on 2010-08-20
hello. 
have any of you photographers out there ever tried deleting photos from a cf card with the camera? well it takes about half a minute if you have a houndred raw files (with my canon eos 350d). 
but with rm (and some bashing) it takes about a second.
now, i just want to ask, does any of you know if there are reasons not to use a computer to delete ones  images? because many of the books about photography i have read,  mentioning remote media, says not to write to the card (e.g. kevin ames and the horrible scott kelby).
maybe it's just windows explorer messing it up.

(if you are interested, i use the command to remove my photos:
```
for dir in $CFCARD; do for file in $dir/*; do rm -v $file; done; done
```this action times to 1.278 s., while the 'remove all' function of the camera times to 35.412 s.)

---

### Post by ajgreeny on 2010-08-20
Interesting point to hear, not for the first time, I must admit, but I use nautilus right click and "delete", the same as the rm command I think, many times on various camera cards, sdhc and xD, without a hint of a problem of any sort.

I wonder if you are correct about windows messing things up, but Linux doing it the correct way.  I shall watch this thread with great interest to find out if, and why, I should not do that again.  Maybe it simply comes down to the read/write speed of the camera compared with the computer.

---

### Post by earlycj5 on 2010-08-20
I always just copy photos off and format the card in-camera, or that's what I was taught to do rather than "delete".

I will "delete" in-camera from time to time, if I need to free space, but by in large, I format.

---

### Post by graphius on 2010-08-20
I use rapid-photo-downloader (from the repositories) to download my images. It has an option to delete after a successful copy, which moves the images to the .trash folder on the card.
After I confirm the download, I usually empty the trash folder, or, occasionally, format the card in the camera. Never have had any problems. However I do notice the .trash folder shows up if I mount the card on a windows machine. This might potentially cause problems if you have an auto-downloading program that pulls the "deleted" images from the trash...

---

### Post by ajgreeny on 2010-08-20
I can understand the presence of a trash folder on the card possibly causing problems, but using the **rm** command or my **right click ->Delete** does not use trash, and normally I ubderstand that now ubuntu asks you if you want to empty the trash, if there is a trash folder, from a usb drive when you unmount it

---

### Post by fraunthall on 2013-04-24
As an experienced photographer and a user of CF cards in Canon DSLRs (D5 Mk II), for example) I can vouch for the risk involved in deleting photos using the Camera's delete function.  Not long ago I deleted 6 or 7 photos from a card in camera while on a shoot and blew the entire day's pictures.  I learned my lesson and will not try that again.  Best to transfer the files for permanent archiving or safekeeping to some other reliable medium, then reformat the card or if you have a large capacity card, let it fill up, then delete the photos.  Selby and some of the well-known Photogs have also experienced similar problems.

---

### Post by howefield on 2013-04-24
Old thread closed.

---

