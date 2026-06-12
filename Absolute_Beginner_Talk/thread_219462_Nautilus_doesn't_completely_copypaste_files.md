---
title: "Nautilus doesn't completely copy/paste files?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Cherry Popper on 2006-07-20
Is it just me or is Nautilus skipping files during copy/paste operations? I've got about 10,000 images burned to DVD and I wanted to copy those images to a folder in /home, so what I did was -

1. Put DVD in drive
2. Edit->Select All->Copy
3. Paste in destination folder

After the copy operation is complete, I noticed (on the status bar) that the amount of images on the DVD is different from the destination folder, it was missing a few images.

Okaaay, let's try again, I delete everything, do the whole copy/paste thing and again some images are missing, different amount than before - seems like Nautilus is skipping files randomly. To make sure nothing is wrong with the DVD, I did the same copy/paste in Windows and all files copied over just fine. No error messages from Nautilus either.

:confused:

---

### Post by swamytk on 2006-07-20
did u try with shell prompt? (e.g.):

$ cp -R /media/dvd/* /home/pictures

we can confirm whether is it nautilus or some thing else?

---

### Post by Cherry Popper on 2006-07-20
I should have done a search first :oops: Looks like there is already a topic on this - [http://www.ubuntuforums.org/showthread.php?t=212148](http://www.ubuntuforums.org/showthread.php?t=212148)

I'll try copying with the shell prompt and see if everything copies over. Thanks for the reply. :)

---

