---
title: "iso cd boot sequence problem"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by warpedwoof on 2006-10-14
Hi folks. I've booted my computer off the imaged Ubuntu cd, but after it loads the cd drivers and does the basic system check it immediately takes me back to the Dr Dos A-prompt. I've even then inserted the bootable floppy disc suggested in help, but it doesn't  kick-start it either and leaves me at the A-prompt. As far as I know, ram and parameters shouldn't be an issue, but the sequence obviously doesn't like something that isn't showing up on the sequence screeen. I'm trying to reach a Live CD set-up so I can check functions and compatibility on my two-harddrive system running XP. Any suggestions would be heartily appreciated. ....Paul

---

### Post by meng on 2006-10-14
This problem usually arises because you didn't burn the CD properly, but instead created a "bootable" CD. You need to reburn from the ISO, and don't "make" it bootable, if you burn it properly it will be bootable inherently.

---

### Post by ReaderRat on 2006-10-14
> **warpedwoof said:**
> Hi folks. I've booted my computer off the imaged Ubuntu cd, but after it loads the cd drivers and does the basic system check it immediately takes me back to the Dr Dos A-prompt. I've even then inserted the bootable floppy disc suggested in help, but it doesn't  kick-start it either and leaves me at the A-prompt. As far as I know, ram and parameters shouldn't be an issue, but the sequence obviously doesn't like something that isn't showing up on the sequence screeen. I'm trying to reach a Live CD set-up so I can check functions and compatibility on my two-harddrive system running XP. Any suggestions would be heartily appreciated. ....Paul
Maybe this will help:
Dual Booting - On Two HDDs
         [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by warpedwoof on 2006-10-14
It's a curious thing, because with an unbootable iso cd image my computer completely ignores the cd and goes straight into Windows XP. I used CDBurnerXP Pro 3 to burn the image after the download. I've burned the image with a Plexwriter CDR at 12x two times now with the same result. I have both my Plexwriter and my Sony DVD drive set up as bootable before the hard drive. One hard drive has Windows and the other is a slave of course. I'm beginning to wonder if there wasn't a problem in the downloaded ubuntu iso file. I guess that's next?   ......Paul

---

### Post by randiroo76073 on 2006-10-14
Did you check the dual-boot link, to burn an ISO use either "copy disk" or "image" and you should get a bootable linux disk, do not use "bootable" function

---

### Post by warpedwoof on 2006-10-14
Resolved with a proper imaging. Apparently what I thought was an image was only a file copy. Worked great as a live CD!! Many thanks to those who offered suggestions. ........Paul

---

