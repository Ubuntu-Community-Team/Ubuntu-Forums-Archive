---
title: "Cannot startup ubuntu 7.10"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Epedemic on 2008-04-10
Well, I boot up my PC, get to the ubuntu menu and select "start or install ubuntu". And then afterwards I get a serious of errors and it didn't give me much time to copy them as it went downwards but it was like this.

[  181.926089] ata5.01:failed to set xfermode (err_mask=0x40)
[  217.066959] ata5.01:failed to set xfermode (err_mask=0x40)
[  252.711157] ata5.01:failed to set xfermode (err_mask=0x40)
[  252.711157]Buffer I/O error on device sda, logical block 0
[  252.7XXXXX]Buffer I/O error on device sda, logical block 1
[  252.7XXXXX]Buffer I/O error on device sda, logical block 2
[  252.7XXXXX]Buffer I/O error on device sda, logical block 3
[  252.711374]sd 4:0:1:0: [sda] Asking for cache data failed
[  252.711412]sd 4:0:1:0: [sda] Assuming drive cache: write through
[  282.682997]ata6.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  282.683035]cmd c8/00:20:00:00:00/00:00:00:00/f0 tag 0 cdb 0x0 data 16384 in
[  418.169274] ata6.01:failed to set xfermode (err_mask=0x40)
[  453.290175] ata6.01:failed to set xfermode (err_mask=0x40)

and these are just bits and pieces of it. and when it's finished, my comp just automatically restarts for some reason. Does anyone have a solution to this? I'm thinking it's a hard drive error or something. Thanks for your help.


EDIT: well finally got into ubuntu but those errors still show up. The problem now is that when I get to the "prepare partitions" menu from the install, nothing is displayed and I can't get anywhere.

---

### Post by R6V2 on 2008-04-10
It may be something else, but my idea would be too, redownload the image, burn it at the slowest speed, and try again.

---

### Post by Epedemic on 2008-04-10
you think it could be the CD? I noticed that it was "712,XXX" KB but when I hovered my mouse over it, it said "695 MB" and the CD was only 700 MB so do you think that may be my problem?

---

### Post by Tatty on 2008-04-10
> **Epedemic said:**
> you think it could be the CD? I noticed that it was "712,XXX" KB but when I hovered my mouse over it, it said "695 MB" and the CD was only 700 MB so do you think that may be my problem?

The conversion between KB and MB is not a perfect one in this case, so dont worry about that.  However it is possible that the CD burned incorrectly.  Try burning it again at a slow speed (less than 4x is generally reccomended).  

You might also want to check the Md5 hash of the .iso [https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")  and also the integrity of the CD [https://help.ubuntu.com/community/Installation/CDIntegrityCheck]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck")

If it all checks out then it probably isnt a problem with the CD, so post back and let us know.

---

### Post by Epedemic on 2008-04-10
Thanks for the input, Tatty. I've tried your suggestions and that didn't fix my issue. The same thing occurs and nothing has changed, I even used different programs to write the iso.

---

### Post by Tatty on 2008-04-10
> **Epedemic said:**
> Thanks for the input, Tatty. I've tried your suggestions and that didn't fix my issue. The same thing occurs and nothing has changed, I even used different programs to write the iso.

If you are trying to install it might be worth trying the Alternative CD.  The live CD is not perfect and sometimes does not work.

Just re-download but make sure you check the "Alternative CD" checkbox on the download page.

---

