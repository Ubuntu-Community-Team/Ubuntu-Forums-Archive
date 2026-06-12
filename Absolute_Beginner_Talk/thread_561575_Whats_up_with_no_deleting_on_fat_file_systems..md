---
title: "Whats up with no deleting on fat file systems."
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-09-27
Why is it when I delete something from a fat file system (Thumb drive, 2nd HDD, and PSP) it doesn't delete it. It just moves it to a file in the root of a file system called ".trash" then I would boot into windows and really delete it. 
But now I don't have windows. And I don't want to reinstall it just to delete stuff. So is there any way to delete stuff with Linux. Or is this a app that Linux REALLY needs. If so way hasn't any programmers made it.

---

### Post by pointone on 2007-09-27
Whenever you write to a flash drive, you must make sure you unmount the device properly. If you simply just pull the drive out of the USB port, chances are none of the changes you've made will have actually been written.

---

### Post by microsoft92sucks on 2007-09-27
I do unmount properly I still puts it in a folder called .trash. 
And that wouldn't explain my HDD.
I read about this a while ago but I didn't think it was true or I thought it was out dated till it started happening to me. (I didn't use many or any fat file systems on my Linux system then.)

---

### Post by microsoft92sucks on 2007-09-27
So nobody knows if this is true that Linux doesn't have a fat file system deleting app.
Can someone help me out here.

---

### Post by sammael666 on 2007-09-27
if we're speaking of deleting in konqueror, did you try to hold shift while right clicking a file to delete? you notice a delete command with red cross next to it meaning really deleting the file, not just moving to trash. it is not in the menu until you hold shift.

---

### Post by eph1973 on 2007-09-27
Two questions (this is not a flame):

Do you have a particular reason for wanting a FAT* file system if you don't use windows anymore (i.e. reformat the partition to something like ext3?

Have you tried 
```
rm /<RootDirectoryOfYourFAT*Filesystem>/.trash/*
```
in your terminal?  Or are you looking for some sort of program that empties your /*/.trash folder, or am I missing completely what you are asking?

---

### Post by jspangler on 2007-09-27
Yeah, you can just go into the .trash folder and delete the files from there. In nautilus, hit Ctrl+H to show hidden files or folders.

---

### Post by microsoft92sucks on 2007-09-27
ok thank u. I guess I just didn't know how to delete b4. But holding shift worked.
I guess that thing I read was out dated or that guy who wrote it was a idiot. (I know I didn't know eathere but I didn't put something on the internet saying something untrue (I just asked something on the internet)) 
And eph1973 I need to use fat for my thumb drive and PSP and it works good for my second HDD. But thanks for the help.
Glad to know Linux isn't missing such a in important app.

---

### Post by The Warlock on 2007-09-27
> **microsoft92sucks said:**
> So nobody knows if this is true that Linux doesn't have a fat file system deleting app.
Can someone help me out here.

Um, empty the trash? It's much like the Windows recycle bin.

Or use the command line to delete stuff; it doesn't use the trash.

---

