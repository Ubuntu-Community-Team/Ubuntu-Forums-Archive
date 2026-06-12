---
title: "Backing up /home directory, getting errors"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by lazyart on 2007-05-12
I've installed Feisty onto another machine and want to move my "stuff" from my Edgy box to it.

I've used rsync -av /media/usb /home/dad to copy things over but I get errors when trying to make some directories, ranging from "unable to create directory" (which is strange because it creates some directories but not others) and "operation not allowed" when trying to copy some files/folders.

The target disk is a USB drive formatted FAT32, so that isn't the issue.

Am I going about this in the wrong way?

---

### Post by jfinkels on 2007-05-12
> **lazyart said:**
> I've installed Feisty onto another machine and want to move my "stuff" from my Edgy box to it.

I've used rsync -av /media/usb /home/dad to copy things over but I get errors when trying to make some directories, ranging from "unable to create directory" (which is strange because it creates some directories but not others) and "operation not allowed" when trying to copy some files/folders.

The target disk is a USB drive formatted FAT32, so that isn't the issue.

Am I going about this in the wrong way?

Maybe it's a permissions problem? What are the permissions/ownership for the source and target files?

Have you tried just doing a regular old 'cp'?

---

### Post by lazyart on 2007-05-12
It's my home folder, so I should have permission to copy the contents, right?

Haven't tried cp.. will have to reasearch that.

Thanks for the quick response.

---

### Post by jfinkels on 2007-05-12
> **lazyart said:**
> It's my home folder, so I should have permission to copy the contents, right?

Haven't tried cp.. will have to reasearch that.

Thanks for the quick response.

Yes that's true. Well, maybe for some reason you don't have permission to read the files from the USB disk. Most likely permissions are fine, but it's a possibility :D. I'm afraid I don't know much about rsync.

You can use cp like this to copy everything (including directories) I believe:
```
cp -r -t /home/lazyart/mystuff/ file1 file2 file3 etc.
```
-r for recursive copying of files inside directories and -t for designating a target directory (or you could just put the target directory at the end of the list of files and drop the -t). As with any program, check out the man pages:```
man cp
man rsync
```

---

