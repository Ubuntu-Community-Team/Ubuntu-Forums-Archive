---
title: "WD Passport USB disk write rights?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by see on 2007-06-23
My windows xp installation has corrupted up and i need to reformat my computer, but all my files are still here. I booted up with my Ubuntu liveCD and attached my WD Passport 80gb eksternal HD (vfat system) and ubuntu automounted it. But the problem is, i cant seem to get writing rights, i only get reading rights.
I've tried googling around abit, but found nothing that worked.
Tried sudo chmod a+w WD Passpord/ , but then it only says unrecognised command.
Isn't it possible to change since im only on the liveCD?

All suggestions are welcome, but im not familiar with Ubuntu so please try to explain step by step if possible.

---

### Post by jpkotta on 2007-06-23
You can't chmod because vfat doesn't support Unix permissions.  All permissions are set at mount time.

You should be able to write files as root.
```
sudo -i
```

---

### Post by see on 2007-06-23
ah well, guess thats why it didn't work.
But lets say i got a folder i want to copy over to the UBS HD. What will the command be?

---

### Post by logos34 on 2007-06-23
> But lets say i got a folder i want to copy over to the UBS HD. What will the command be?

sudo cp <folder> /media/WDPassport  (or whatever the mount point and name)

---

### Post by see on 2007-06-23
When i try that i just get:

```
ubuntu@ubuntu:~$ sudo cp /media/disk/Bilder /media/WD Passport
cp: target `Passport' is not a directory
```

---

### Post by logos34 on 2007-06-23
> /media/WD Passport

if there's supposed to be a space there, try " ":

/media/"WD Passport"

---

### Post by see on 2007-06-23
that gives me:
```
ubuntu@ubuntu:~$ sudo cp /media/disk/Bilder /media/"WD Passport"
cp: omitting directory `/media/disk/Bilder'
```

still nothing on the USB HD. and what does omitting dir mean?

---

### Post by logos34 on 2007-06-23
> cp: omitting directory `/media/disk/Bilder'

I get that when I specify it to copy a parent dir but not subdirectories

sudo cp /mount/dir**/***

it comes back indcating the subdirectory being ignored by the '/*' symbol

not sure what the deal is in your case.  Try copying something else, see if your can write to "WD Passport"

---

### Post by see on 2007-06-23
As impatient as i am, i decided to move a little part at a time on my 512mb mp3player. So now im almost done and ready to format the PC.
But thanks to everyone for trying to help me, its appreciated.

---

### Post by jpkotta on 2007-06-23
For reference, use the -a option to cp when copying directories:
```
sudo cp -a /dir/to/copy /place/to/copy/to
```
You can learn all there is to know about cp (or just about any command) with 
```
man cp
```
(man == manual page)

---

### Post by Inxsible on 2007-06-23
> **see said:**
> My windows xp installation has corrupted up and i need to reformat my computer, but all my files are still here. I booted up with my Ubuntu liveCD and attached my WD Passport 80gb eksternal HD (vfat system) and ubuntu automounted it. But the problem is, i cant seem to get writing rights, i only get reading rights.
I've tried googling around abit, but found nothing that worked.
Tried sudo chmod a+w WD Passpord/ , but then it only says unrecognised command.
Isn't it possible to change since im only on the liveCD?

All suggestions are welcome, but im not familiar with Ubuntu so please try to explain step by step if possible.


Since you are on the LiveCD, which I think you are, you wont be able to change anything on the hard drives. LiveCD do NOT allow write permissions for the very fact that you dont mess up your existing OS and can still try out Linux to check it out

---

