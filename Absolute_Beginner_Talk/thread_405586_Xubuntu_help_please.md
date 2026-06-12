---
title: "Xubuntu help please"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Melanie on 2007-04-09
Yesterday i installed Xubuntu on an old Compaq computer of mine and couldn't figure out how to access the floppy drive. Some of you suggested using the File Manager (Thunar) as there is supposed to be an icon on the left panel of this program that displays when a floppy is in the drive. I have a floppy in the drive but there is no icon in Thunar to represent it. I am lost for any other ideas. Please help. Oh I should mention that I rebooted with the floppy in the drive and the computer notified me that I was booting with a non-system disc so it does recognize that it's there. 

Next problem: no sound. Tried to play the files that were in the 'examples' folder in Thunar and they would not play. The program that plays music opened and displayed that it was playing but there was no sound. Don't know what to do about this. Yes I checked the connections and the volume.

---

### Post by WiseElben on 2007-04-10
For the sound problem: run alsamixer (type it in the terminal) and make sure everything is up. I once had this problem and what I had to do was turn on/off the "Analog/Digital Output Jack." Why? I have no idea.

---

### Post by Melanie on 2007-04-10
Thanks for your response. I've discovered that the problem is not that there is something not configured properly for the sound but that the program that is installed with Xubuntu doesn't work right. It opens with a wizard and it asks you to check your settings so you do that and they all check out ok then you click close and in about 1 second after the file starts playing the whole program just disappears! It closes without any reason. I tried to use it several times even after rebooting the system and it always does the same thing and it always opens the wizard even after you have already used it before. How do I fix this?

Still need help accessing the floppy drive too if anyone can answer this. Thanks.

---

### Post by pxwpxw on 2007-04-10
**Melanie**

for the floppy problem, use the filemanager to find and open the file /etc/fstab

and post the result.

It should have a line like this:
```

/dev/fd0           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by Melanie on 2007-04-10
I looked under File Manager and I found File System so I opened that and then media and then there were 2 floopy folders. One said Floppy0 and one said Floppy. I clicked on both of them and nothing happened. I took the floppy disc out, put it back in, and clicked on them both again and nothing happened. It wasn't showing anything in those folders.

---

### Post by Melanie on 2007-04-10
I have to write down what you say and run downstairs and try to do it and then back upstairs to tell you what happened on this computer with internet so it takes me a few minutes lol


I just tried to run a CD in the CD drive too and I can't get it to run either. There is nothing in the CD folder. I am so confused.

---

### Post by confused57 on 2007-04-10
I was able to get my floppy to mount in Xubuntu with:

```
sudo mount /media/floppy0
```

to unmount:
```
sudo umount /media/floppy0
```

---

### Post by Melanie on 2007-04-10
I tried this command and it doesn't work either. It says "command not found"

---

### Post by meborc on 2007-04-10
hmm... it should not say that... are you sure you typed ```
sudo mount /media/floppy0
```

you could just try ```
sudo mount -a
```to mount everything (all you have configured in the fstab file)

---

### Post by pxwpxw on 2007-04-10
> **Melanie said:**
> I tried this command and it doesn't work either. It says "command not found"

Could we have another try at /etc/fstab please.

This is a text file which allows the floppy to automount.

If you use thunar file manager to open 

File System

then

Etc

hen look through the file list and you will see the file fstab

Double click on fstab and wait for it to open and you should see a line:

/dev/fd0           /media/floppy0  auto    rw,user,noauto  0       0

Note whether all that is there.

In my install the fd0 was missing from /dev/fd0, I had to edit it in.

That comes next.

---

