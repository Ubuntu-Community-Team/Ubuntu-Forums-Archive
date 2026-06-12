---
title: "scanModem help."
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by doudeman on 2007-07-12
I have been trying to unzip scanModem.gz but every time I try it says "unexpected end of file" can anyone tell me what this means or what I am doing wrong? I downloaded it on windows to a thum drive then transfered it to ubuntu and put it on the desktop then I cd to desktop and try to run gunzip and it keeps giving me the error message

---

### Post by kevinlyfellow on 2007-07-12
Sounds like it was a bad download to me.  I tried it out and it worked fine.  to be sure you are doing this
```
gzip -d scanModem.gz
```

---

### Post by doudeman on 2007-07-12
I have downloaded it severaltimes with no luck. What does the -d do?

---

### Post by kevinlyfellow on 2007-07-12
the -d decompresses the file.  As I just learned there is a difference between gzip and gunzip, and it's that option...

I'll post the uncompressed for you up here so you don't need to mess around with some foolish little thing like that.  Once you download it, just remove the .tar from the name, it was just away to fool the attachment manager.

---

### Post by doudeman on 2007-07-16
ok thanks. I still don't know why it wont uncompress the file. I have saved it several times from several different sources and it is always the same. I was following the wiki instructions exactly.

---

### Post by kevinlyfellow on 2007-07-17
It is weird... I really don't know a reason why it would be consistently having a problem.  

If you want to investigate further, you can always check an md5sum (if the site doesn't have it, I'll happily compare it to a copy that I can download and check)

```
md5sum scanModem.gz
```

---

