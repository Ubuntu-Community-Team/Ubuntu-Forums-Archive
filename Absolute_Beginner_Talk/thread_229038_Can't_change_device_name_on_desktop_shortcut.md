---
title: "Can't change device name on desktop shortcut"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by c0rd3l1a on 2006-08-03
I just partitioned, formatted, and mounted a new external hard drive. It's a WD MyBook. I mounted it at /media/Tenzig and I want it to show up on my desktop as Tenzig, but it shows up as MyBook. When I right-click, the "Rename" option is not available to me. How do I rename this?

---

### Post by catlett on 2006-08-03
It might be a permissions issue. If root owns it you, a user, can't change the name because you don't own it.
Try this, launch nautilus as root with this command ans then try to rigth click/rename
```
gksudo nautilus
```If this is it, you can rigth click again (while browsing with gksudo nautilus) and go to properties. Then select the permissions tab. Check off the unchecked boxes to give read/write to others besides root. Don't do this if others use this computer. It will allow all users to modify it. But if it is just yours then you migth want to open it up to users.

---

### Post by c0rd3l1a on 2006-08-03
When running Nautilus as sudo, my desktop shows up as empty (which it is not). And MyBook still carries that title (menu at left on screenshot). And I can't right click on MyBook. Am I doing something incorrectly?

Here is a screenshot so you can see what I'm talking about:
[IMG]http://static.flickr.com/64/206168682_b5ee843bfe.jpg[/IMG]

---

### Post by Anduu on 2006-08-03
When you launch Nautilus as root it defaults to roots home directory....browse to file system>home>yourusername....

---

### Post by c0rd3l1a on 2006-08-03
Thank you! Now when I navigate to the correct desktop, everything *but* MyBook shows up in Nautilus. There should be some way to rename this through the terminal, shouldn't there?

[IMG]http://static.flickr.com/82/206174234_6e914d4034.jpg[/IMG]

---

### Post by Anduu on 2006-08-03
Try the computer icon...the one on the navigation bar.

---

### Post by catlett on 2006-08-03
your mount point should be /media/mybook. When I just went to try it I just slected "computer" from the nautilis menu at the top of the window. It then showed me the icons for the system drives. I then right clicked sand chose rename

---

### Post by c0rd3l1a on 2006-08-03
It's much closer to getting it to work, but I still must be doing something incorrectly. When I click on the computer icon, MyBook shows up (with a few other things). I can right click on it and choose rename. However, it won't let me rename it. There is no real error message, just "Sorry, could not rename MyBook to Tenzig" (see screenshot). I checked the permissions on it and both my username and root have all permissions enabled. What else am I doing incorrectly?

[IMG]http://static.flickr.com/82/206194956_7a247c7484.jpg[/IMG]

---

### Post by c0rd3l1a on 2006-08-03
My mount point that I created for it is media/Tenzig. When I go to Device Manager and check out its details, it says that is where it is mounted. However, it also says "volume.label  string  MyBook".

---

### Post by Anduu on 2006-08-03
Well as a last resort...if you are dual booting Windows you can log into Windows and rename it there.

To view ext2/3 partitions in windows you need a utility called "ext2ifs"(Google it....)

I know this will work as I have done it on a number of occassions.

---

### Post by c0rd3l1a on 2006-08-03
I am not dualbooting. But, after figuring out that my problem is the "volume label" I was able to use the search function more efficiently (because I was searching for the correct terms this time!) and found this: 
[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/30867](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/30867)

So I am going to reformat it (currently fat32) and then use e2label and see if that works.

---

