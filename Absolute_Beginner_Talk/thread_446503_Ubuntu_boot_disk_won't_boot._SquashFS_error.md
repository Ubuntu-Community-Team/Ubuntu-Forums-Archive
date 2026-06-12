---
title: "Ubuntu boot disk won't boot. SquashFS error:"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Metric on 2007-05-17
I get a lot of text going:

> 
Buffer I/O error on device hda logical(Not sure if that's what I wrote, lol.) block 246400(Not sure of the exact number)
Buffer I/O error on device hda logical block 246401
Buffer I/O error on device hda logical block 246402
Buffer I/O error on device hda logical block 246403
Buffer I/O error on device hda logical block 246404
Buffer I/O error on device hda logical block 246405
Buffer I/O error on device hda logical block 246406
...(Then it keeps going up to 246506)
Buffer I/O error on device hda logical block 246506

SQUASHFS error: sb_bread failure reading block 0x776d0
SQUASHFS error: unable to read page block 1ddac958

                                                            Size 7963


It was something to that effect. Anyone know the problem? It happens right after it says Ubuntu,with the loading bar below it.

Thanks in advance :)

---

### Post by mills on 2007-05-17
have you tried a cd integrity check?

might be worth a shot to see if you get any errors there.
if you do then you'll have to burn another copy i think

---

### Post by Metric on 2007-05-17
Will do.
thanks.

---

### Post by mills on 2007-05-17
actually i just found a post in luanchpad that says to add this boot time option

```
ide=nodma
```

[https://answers.launchpad.net/ubuntu/+question/5246](https://answers.launchpad.net/ubuntu/+question/5246) (bottom post)

---

### Post by Metric on 2007-05-17
Thanks a lot.
Not exactly sure how to add a boot time option, but i think I do. I'll try it out.

---

### Post by Metric on 2007-05-17
Weeelll, I pressed f6 and typed ide=nodma, if that was what I was supposed to do. a prompt comes up that is titled "Error I/O" and says "Error reading boot disk" I think...

---

### Post by mills on 2007-05-17
hmm i think a cd integrity check is needed

also did you do a md5sum check?

---

### Post by Metric on 2007-05-17
I did do an integrity check, I got that same error, but I didn't do an md5sum check.
anyways, I have to go to sleep... :(
But I'm going to download Ubuntu again and reburn it and try tomorrow. Thank you for all your help.

---

### Post by esoterica on 2007-05-17
I burn ISO files to CD's all the time and I had problems with the first 2 CD's I burned not working and going in the trash (good thing blank CD's are cheap), the MD5 check was fine on my downloaded ISO file, and never had a bad disk problem burning ISO's before.

I ran out of blank CD's and even though it's a CD ISO file I burned it to a DVD and didn't have any problems. Just to be sure I didn't waste another blank disk though I slowed my burn speed WAAAAAY down and just suffered through the extra time it took to burn that slow, it worked like a charm. 

My suggestion, providing the MD5 check passes which you do want to check for both security and data integrity reasons (not to mention mental sanity), turn your burn speed way down and burn a new disk.

---

