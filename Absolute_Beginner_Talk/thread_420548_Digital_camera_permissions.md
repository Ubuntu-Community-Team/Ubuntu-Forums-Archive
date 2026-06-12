---
title: "Digital camera permissions"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by rebecca_b on 2007-04-23
Hi

I am an additional user on a Kubuntu 6.06lts installation. 

When I plug in my digital camera (which is also used by my boyfriend on his login with no issues) it will not mount on my login, saying "Could not enter folder /media/sdc1."

It appears as if i don;t have permissions, but I took the photos, and want to view them on my own login! 

Can anyone help me view my pics without logging into the other login?

Ta!

Rebecca
):P

---

### Post by ericmarceau on 2007-04-24
[1] Priviledges

For starters, check the priviledges on your "/media/sdc1".  They should look like:

drwxrwxrwx 3 root root 4096 2006-10-25 16:11 /media/sdc1


[2] Automatic mounting

Presumably this is mounted via USB.  If you are looking to use the "Plug-N-Play" approach for the camera, you have to figure out where the system allocates the priviledge for you to do so.  This involves having specific entries in the /etc/fstab file to match.  Since I prefer controlled mounting, by doing so manually, the entries I have in the attached file shows what should NOT be done, i.e. you should comment out the appropriate line in your own fstab file.


[3] Manual mounting

The attached is a script that I created to scan for any USB drives, currently plugged in but not yet mounted, and prompt me to mount them, one by one.

KEY to this is the assumption that specific mountpoint directories are created for specific types of external devices, to ensure correct choice of "filesystem type", otherwise some drives (camera is considered a drive) could have things scrabbled if the systems writes to the device with the wrong assumption of format.


Eric

---

