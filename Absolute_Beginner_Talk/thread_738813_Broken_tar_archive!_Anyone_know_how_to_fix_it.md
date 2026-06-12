---
title: "Broken tar archive! Anyone know how to fix it?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by lamalex on 2008-03-29
Can anyone help me overcome this broken tar archive? I'm getting this error when I try to extract it.
```

tar: Skipping to next header

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
tar: Child returned status 1
tar: media: Not found in archive
tar: Error exit delayed from previous errors

```

Thanks for any help.

---

### Post by nsche on 2008-03-29
Usually when you  have a problem like that you are sol.  When I have seen that problem it has sometimes been a case where I thought it was compressed but it was not or maybe someone wanted to create with tar czf and they really used tar cZf which gives a different compress program or maybe it was created using bzip2.  Try all of the options before you give up.  Try file on it to see what it thinks the file is. (file filename)

---

### Post by commonplace on 2008-04-04
There's an application -- unfortunately Windows-based, and even more unfortunately, not free in any sense of the word -- that can try to fix them. There's a free demo, if you have a Windows machine available to test it on. It will at least tell you if it's able to fix the problem or not. If not, then I guess you're out of luck as far as that goes. If so, though, then you'd at least have the option of buying that software to fix the file. It's called Advanced TAR Repair, by [DataNumen]("http://www.datanumen.com/").

As for myself, I have a 20+ GB backup file which is corrupted, and which the ATR claims it can fix. I just don't have the $150 with which to purchase the software. Plus, I hate buying software. At some point, though, I'm going to NEED files out of this backup, and I may just have to bite the bullet and fork over $150. Ugh.

If you find any other solution to your problem, I'd love to hear it!

/Kevin

---

### Post by commonplace on 2008-04-06
Alright, scratch what I said. I found a solution that worked for me. The best part is, it's Linux-based, and free (in every sense of the word)!

I followed the general instructions [here]("http://texasdrifter.blogspot.com/2007/10/failure-to-recover.html"). Basically you download and compile the gzip Recovery Toolkit, run it against your broken tar.gz file which gives you a repaired file, and then you use the cpio command to extract all your files. It worked great for me.

/Kevin

---

