---
title: "Two hard drives, one OS?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Whamola on 2007-09-26
Hi there everyone.  I recently came into possession several hard drives that were going to be thrown away (public auction leftovers).  After testing and finding out that only one of them worked, I decided to install it in my Fiesty computer.  Now me, in my infinite hope for things to just work with minimal effort assumed that the computer would say "Hey I found a new hard drive, you want me to reformat it for Linux?'  But, as I found out once I turned the computer on, getting that answer was just about as likely as it saying "Hey, I'm a dinosaur."  

I ended up installing a fresh Fiesty on it (after trying several other distros, which didn't create swap files like Ubuntu did, odd).  Now, my question is:  Is there any way for me to get my second hard drive integrated with my main partition without having to mount the hard drive every time at start up? 

I am fairly sure that I have the slave/master set up correct.  

Thanks

---

### Post by BrendanM on 2007-09-26
This is actually fairly simple to do. All you need to do is edit your /etc/fstab file to automatically mount the second hard drive when you boot. There's plenty of tutorials around explaining how to do this. This one might be helpful: [http://www.bradtrupp.com/id/unbuntu-add-hard-drive.html](http://www.bradtrupp.com/id/unbuntu-add-hard-drive.html)

---

### Post by Whamola on 2007-09-26
Alright, now i'm at a point where I have to add "/dev/sda1 /nas2 ext3 defaults 0 0" to "/etc/fstab"

And I'm staring at it like a monkey doing long division.

---

### Post by Whamola on 2007-09-26
Here's what I'm looking at.

---

### Post by Lord Illidan on 2007-09-26
Do you know what the device name? /dev/sda2 for example? 

EDIT : You can find out by typing this command : ```
blkid
``` Copy and paste the output here.

Does this step work for you?
>  Using the Places / Computer menu, you should see the new volume. Click on it to mount it onto the desktop (as /media/disk). At this point, you should be able to browse the disk but likely have no write access. Right-click and select "Unmount Volume" to unmount it. 
If it does, and you do know the device name, then open a terminal, and type these lines :

```
 sudo cp /etc/fstab /etc/fstab-backup
```That will backup the fstab, so if we run into probs, we can fix it easily.

Now, let's make a mountpoint for your drive. Let's make it /media/data for example.

```
sudo mkdir /media/data
```Now, all you have to do is type :

```
gksudo gedit /etc/fstab
```And type in this line at the end of the file :

```
 /dev/sdaX /media/data ext3 defaults 0 0
```Replace /dev/sdaX with your device name. 

Ok with me so far?

---

### Post by Whamola on 2007-09-26
Yeah, I'm with you so far, it was just something about seeing it in the terminal that made my mind melt a little.

---

