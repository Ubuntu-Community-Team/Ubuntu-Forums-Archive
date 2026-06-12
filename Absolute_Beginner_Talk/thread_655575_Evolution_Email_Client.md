---
title: "Evolution Email Client"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2008-01-01
Is there a way to store all of my mail folders for evolution in a external hard drive or usb stick, rather than using the default location (somewhere on my computer)? I would like to do the same with all of my contacts and calendar information.I want to be able to work with all my saved data from an USB stick or external hard drive. If anyone has done this or knows how to do this, I would appreciate the help.

---

### Post by dcstar on 2008-01-01
> **fmbugdadi said:**
> Is there a way to store all of my mail folders for evolution in a external hard drive or usb stick, rather than using the default location (somewhere on my computer)? I would like to do the same with all of my contacts and calendar information.I want to be able to work with all my saved data from an USB stick or external hard drive. If anyone has done this or knows how to do this, I would appreciate the help.

Create a soft link to the place you want the data to replace the .evolution default directory, or mount the external drive to that location - either should work.

---

### Post by fmbugdadi on 2008-01-01
oh, ok, those sound like good ideas, however, I am not sure how to go about them. I can mount the usb drive, but how do I find all the save locations? How would I go about creating a soft link? thanks for the help. sorry to ask these questions, but I am a newbie with linux...

---

### Post by dcstar on 2008-01-02
> **fmbugdadi said:**
> oh, ok, those sound like good ideas, however, I am not sure how to go about them. I can mount the usb drive, but how do I find all the save locations? How would I go about creating a soft link? thanks for the help. sorry to ask these questions, but I am a newbie with linux...

Shut down Evolution, plug in the USB drive, then in a terminal:
```
cd /media/*your-usb-drive*
mkdir evolution-data
cd ~
mv .evolution .evolution.save
ln -s /media/*your-usb-drive*/evolution-data .evolution
cp -r .evolution.save .evolution
```
Restart Evolution and it should now work saving the data to the new location.

Make sure there is enough room on the USB, and it is preferable that the USB is formatted EXT2/3 (or any other Linux filesystem).

---

### Post by fmbugdadi on 2008-01-02
Ok, thanks for the info. I will give this a shot, and get back to you, if I have any problems. 

thanks again....

---

### Post by fmbugdadi on 2008-01-02
Ok, it seems like, all those commands worked, and the data is now being saved on my usb drive. Except for the obvious ones, can you explain what those commands did? Is the  data  only being save in one spot now ( my usb drive only)? Thanks again, for understanding that I am really new at this...

---

### Post by dcstar on 2008-01-03
> **dcstar said:**
> 
```
cd /media/*your-usb-drive*
mkdir evolution-data
cd ~
mv .evolution .evolution.save
ln -s /media/*your-usb-drive*/evolution-data .evolution
cp -r .evolution.save .evolution
```
.

Change your terminal current directory to the location of your external USB;
Make a new directory;
Change back to your Home directory (~ is a shortcut to it);
Rename the original (hidden) Evolution data directory;
Make a soft link called .evolution linked to your new directory on your USB;
and copy (including all the sub-directories) of your existing Evolution data to your new location on the USB.

And yes, your data is now ONLY being updated on the USB drive.

If you want to back it up to the old place:
```
cp -r .evolution .evolution.save
```

You may encounter an issue in the future in that your USB may mount at a different **sdx** designation, you can avoid this by labelling the partition on the USB and then it will always mount using the partition name (do a forum search for renaming partitions, you should find lots of info).

---

