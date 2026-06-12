---
title: "Mounted drive does not show in Open Office"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Thymen on 2005-11-20
Hi folks;

Warning: Newbie questions....!

I added a new HDD, partitoned and formatted it, and mounted it. Everything appears to be OK. Also, I edited fstab, so after boot up it shows (on my desktop and in Nautilus).

But.... it does not show in Open Office! Using the file browser (open, save) from OO does not allow me to navigate to the drive.

What should  I do to?

---

### Post by cuboconojos on 2005-11-20
Hi, in order to understand your problem better:
-In the file browser, you see the drive and you cant navigate to it? or you dont see it at all?
-If you don't see it at all, where did you mount the drive? In /media/hdd_whaterver ? Or somewhere else?. Just in case you're browsing in the wrong place...
-And if you see it but you can't navigate, maybe it has something to do with permissions..you're probably using a non root acount.

Well, I hope we can help you....

---

### Post by Thymen on 2005-11-21
I think I have figured out what my misconception was....

I can see the drive(s), both in Nautilus and on my desktop. I can add files to them, and shen I copy an OO file in them I can start it - it shows the path to /etc/media/<name of mount> in the upper left corner of the OO save dialog.

However, used to Windows, I was looking for a drive, thinking that the folders I created for mounting the drives to were just that - folders. However, I guess that they are mount points, redirecting the file browser to the drive. Guess it is best now to create a link to (a folder on) that drive and put that link in my home folder....

...
Just did that, and it works fine now. It works... but I wonder if it is the correct way of doing things. Any comments or suggestions are welcome.

Thanks,

Thymen

---

