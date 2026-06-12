---
title: "How to make virtual cdroms in Ubuntu 7.04"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by wasim2050 on 2007-07-21
On Windows I rarely use to copy Cd's or Dvd's and instead of copying them I use to make images of them in .nrg(Nero image format) or .iso then whenever I want to use those images then I simply use to mount those images in virtual cdroms by using a free software called daemon.

So is there any such alternative in Ubuntu linux.

I can use the command [[mount -t iso9660 ~/cdimage.iso /target_directory -o loop <--Here ~ represents your Home_Dir]] to mount cd images but I want something in GUI to do my task fast as I have many images and inserting cammand for every image can be quite time consuming.

Thank you

---

### Post by king20878 on 2007-07-21
Try gmountiso.  It should be in universe.

Also try the command line application fuseiso.  It's more straightforward than the loopback mount command.  

There is a KDE app called acetoneISO, but I have not tried it.

---

### Post by wasim2050 on 2007-07-21
Thank u king. It works perfectly.

---

