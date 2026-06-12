---
title: "Help trying to recover windows files"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Jtrybyne on 2007-01-02
Ok.  I cant boot my laptop into windows anymore, it says there is a corrupt or missing system file.  I made a liveCD of Ubuntu linux and booted into that.  I mounted my HD and when I clicked on my windows folder in my file viewer thing, it started thinking... It took 12+ hours and then it said that I do not have permission to view these files.  What do I do?  Al I want to do is get a few files off of my HD and onto a CD/pendrive/email.  How do I do this?  I am getting desperate here...  Help is much appreciated.  Thanks.

---

### Post by Apple 101 on 2007-01-02
Okay.  That isn't a good problem - happened to me once before, as well.

In your Live CD:
1. Open a terminal. Type: cd /media && mkdir windows
2. Type: sudo mount -t ntfs /media/windows  /dev/hda1
3. Type: gksudo nautilus /media/windows

I'm assuming that /dev/hda1 is your Windows drive.

---

