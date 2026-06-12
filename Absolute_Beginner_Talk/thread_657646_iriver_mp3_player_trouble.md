---
title: "iriver mp3 player trouble"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by vandekamps on 2008-01-03
I have an iriver S10 2 gig. I have been using it without any problems for quite a well now. Until today, it seems that every cd I copy in any format will not transfer to the player without some of the tracks not making it. The error message says invaild parameters can not copy. I don't use any software to transfer I just click in drag like it was a usb drive. I also found that older albums that I copied before I upgrade to 7.10 make it with no problem. I feel like I am missing something simple. Any help would be great.

---

### Post by dstew on 2008-01-04
I see you have not had an answer in a long time. Here is one thought. This might be related to a file manager program bug. Try the command **killall nautilus**, then see if it works. This command re-starts the nautilus file manager. There is a known bug in this system in Gutsy, but not in Feisty. See [http://ubuntuforums.org/archive/index.php/t-592098.html](http://ubuntuforums.org/archive/index.php/t-592098.html)

---

### Post by nick_h on 2008-01-05
Is there anything unusual about the filenames of the files that fail to copy?

---

### Post by vandekamps on 2008-01-05
I tried the killallnatilus command with out any luck. I have noticed that the files that do make it the transfer are all out of order. I tried ripping cds with different programs, sound juicer and K3b and in different formats. This doesn't seem to make any difference either. I am at a loss with this one.

---

### Post by nick_h on 2008-01-05
What is the exact error message you get?  I asked about the filenames because I expect that you are trying to copy files onto a FAT filesystem with invalid filenames.  I think you would get an invalid argument error message in that case though.

The characters I am thinking about are:
```
* ? " < > | : / \
```

---

### Post by vandekamps on 2008-01-12
Thanks Nick_h that was it. I new it was something simple I was missing.

---

