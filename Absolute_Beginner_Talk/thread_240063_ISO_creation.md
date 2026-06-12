---
title: "ISO creation"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-08-20
As you can see, I have been posting on here a little bit, but I still don't know how to do some of the simpliest things.

What command do I run to make a folder into an ISO image to be burned at a later date?

Thanks.

---

### Post by steve.horsley on 2006-08-20
From the command line, I think the command is mkisofs or growisofs. I've never used them directly, but I believe that all the GUI CD burners use one of these as a back end behind the scenes.

If you use the CD creator that comes with nautilus, when you click the **Burn** button you get a pick list of CD drives to write to, and one of the options is **file image**. That should do the trick. I am sure that gnome-baker and k3b (two other GUI CD burners) also have an option to just create the .iso image.

---

### Post by Marsolin on 2006-08-20
For anyone using Konqueror, there is a cool program called Mount ISO ([http://linuxappfinder.com/package/mount-iso](http://linuxappfinder.com/package/mount-iso)). It creates a menu entry when you right click on a folder that allows you to create and iso out if it. You can also use the program to click on an iso file and mount it (hence the name).

---

### Post by luvinit on 2006-12-09
I just thought I'd make an addition to this instead of making a new thread as I was trying to find out how to make an image of a cd. The ubuntu guide says use this command for folders

mkisofs -r -o file.iso /location_of_folder/

and

sudo umount /dev/cdrom
dd if=/dev/cdrom of=file.iso bs=1024

for disks, but I can't get it to work. However, I have found that when the cd is automounted once you put in the drive, it appears on the desktop. Right clicking gives you the option to copy the disc, which further allows you to selct copy to ISO image.

---

