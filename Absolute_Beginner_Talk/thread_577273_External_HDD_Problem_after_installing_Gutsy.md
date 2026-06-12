---
title: "External HDD Problem after installing Gutsy"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by schreckles on 2007-10-16
Ok, so I just went ahead and jumped on the Gutsy bandwagon (Kubuntu) and love it so far.

My problem however, is that for whatever reason, my 500GB external HDD (/dev/sda1) now just has a folder named "lost+found" in it that's locked. I'm sure you all know what to do with this, so I'm calling on all you gurus out there, but I have no friggin idea. I'm gonna go ahead and venture a guess that all my files are in that folder? How do I get them back? Any tips?

---

### Post by expatCM on 2007-10-16
Lost + Found is automatically created by the system on all new drives.   You can only access the content when you are logged on as root (unless you change the permissions).  There is not normally anything on this directory.

I am sure that I am wrong but I tend to delete this directory ...  but that is me ....

In your case since you cannot find your files I would tread a little carefully and try this from the command line ....

gksudo nautilus

then click on File System and then Media and navigate to the drive and the folder.  You should then be able to see what is in the folder.

However ......   what is the format of this external drive, is it NTFS?

---

### Post by schreckles on 2007-10-16
No, it was fat32, for use on windows and kubuntu, since at the time i didn't realize there were windows ext3 drivers..now it's invisible. I found out how to look into there using nautilus browsing through the forums on here, came up entirely empty (learned a lot, though...just an empty folder). It only had about 40 GB of music, so I decided I'd just go login as root and reformat it as ext3. Here's where a whole NEW problem begins. One of my puppies (the female of course! lol j/k) got curious with the lighted switch on the surge protector, killing it partway through the reformat. I'm on my laptop, so it just went to battery power with no problem, however, kubuntu now does not see my external. Is there anyway I can force it to mount or anything like that, so I can reformat the HDD to ext3 finally? The computer sees the drive when I run my wipedrive (formatting tool) disk on startup, so I know the HDD isn't toast. Or should I just format it with wipedrive (formats the disk to a completely blank slate) and then see if ubuntu will recognize it. (If i can force-mount it somehow, that is preferred, as wipedrive will take quite a few hours to format the drive, and then I'd still hafta make it ext3 with another format, this time I think i'll just use mke2fs -j and tune2fs in the command line instead of gparted)

---

### Post by schreckles on 2007-10-16
Awesome...I've found the drive again after shutting everything down, re-connecting, and rebooting. should be a straight shot from here. Just kinda sucks that I lost that 40GB of stuff. oh well.

---

