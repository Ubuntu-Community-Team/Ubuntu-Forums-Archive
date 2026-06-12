---
title: "autorun issues: Collins Cobuild (dictionary)"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Lambik on 2007-07-08
I have been running a Ubuntu-only desktop for just over a week now, and so far I have had no reason to complain at all. However, I am afraid I need to post this thread as I have just encountered a problem to which I have not been able to find the solution. Any help, such as relevant links or a straightforward explanation why I am experiencing this problem, would be greatly appreciated.

I want to install the Collins Cobuild **Advanced Learner's English Dictionary**, so I installed wine, as this is a Windows application (though it does not say it is on the blurb). Then I navigated to the CD-ROM using Nautilus, but I could not find a setup.exe file or anything similar, not even when I navigated to it using the terminal or the wine file browser. When I open the CD-ROM with my Windows laptop, I can see that there are several files on it, including setup.exe and an autoplay function. On Ubuntu, by contrast, only three folders containing data are visible, even when I check "Show hidden files".

Any ideas how I could install this dictionary on Ubuntu?

---

### Post by chuckyp on 2007-07-08
Are you sure you are looking in the right folder for the cdrom?  You should be able to see .exe's etc... in there.  Things to try:

Open up a terminal and try       ls /media/cdrom   Post the output here.  Or you can just try wine /media/cdrom/setup.exe

Also check out appdb.winehq.org.  There you can search for the specific app you are trying to install and see if anyone has had success or even tried it before.

---

### Post by Lambik on 2007-07-08
Thanks for your quick reply.

That's another issue, and I don't know if it's supposed to be like this: When I insert a CD-ROM, it cannot be opened on the cdrom path. Rather, it should be opened using the CD-ROM's name, here: cobuild4l (see screen shot 1).

The terminal output for **ls /media/cobuild4l** is:

data  icon  lang

(= folders)

Output for **wine /media/cobuild4l/setup.exe** (which I had already tried):

wine: cannot find '/media/cobuild4l/setup.exe

(same for Setup.exe instead of setup.exe)

The second screen shot displays the contents of the CD-ROM when viewed in Windows XP.

Collins Cobuild is listed on WineHQ, but I suspect that the version listed is different to mine.

Thanks once again for your quick reply. But the question still stands, I'm afraid.

---

