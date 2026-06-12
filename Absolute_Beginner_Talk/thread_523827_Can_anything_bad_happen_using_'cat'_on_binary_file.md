---
title: "Can anything bad happen: using 'cat' on binary files"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-08-12
So I got a virus in my email, and being on a linux box I wasn't too worried about it. Anyway, I'm sure you can all tell where this is going....curiosity killed the cat.

So I download the attachments to my home directory, and there were two files. One was a .exe, and another had no extension

Just being curious, I ran 'cat' on the file without an extension, and a bunch of jumbled characters came up on the screen.....and stayed up on the screen. I had to use ctrl+c to exit. I then deleted the files using rm.

So lets just suppose that the file *was* intended to attack a linux box. If the file did not have execute privileges, and was not used as root....could it still cause trouble?

Can executing 'cat' on a malicious binary file have any ill effects?

-Andrew

---

### Post by skymera on 2007-08-12
the chances it was a linux virus.
was nil.
stop worrying,

search the .exe on mcafee and find what it does and what it works on if your thay worried

---

### Post by heimo on 2007-08-12
Scenario you describe would be quite... unrealistic. It'd have to specifically attack vulnerability in cat or shell, I believe. And even then... Highly unlikely.

Try running:
```
cat /bin/ls
```

Same effect as with showing contents of .exe binary, isn't it?

---

### Post by Atreus12 on 2007-08-12
> **skymera said:**
> the chances it was a linux virus.
was nil.
stop worrying,

search the .exe on mcafee and find what it does and what it works on if your thay worried

I'm not really worried about it, but just wondering if 'cat'ing malicious binaries can do anything bad.

While I didn't explicitly give it execute, what if it did have execute privileges? Can 'cat'ing executable binaries have ill effects?

---

### Post by u-slayer on 2007-08-12
All cat does is print the data from a file. It can't execute anything.

---

