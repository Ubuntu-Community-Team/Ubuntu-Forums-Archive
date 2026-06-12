---
title: "[SOLVED] WinMD5Sum equivalent"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by KIAaze on 2007-11-28
Hi,

Is there an equivalent of WinMD5sum for GNU/Linux?

I noticed k3b automatically calculates the checksum of an ISO. But it doesn't seem to offer a way to compare it to the correct checksum.
I can't even copy the checksum number from the window.

---

### Post by mcduck on 2007-11-28
I have never even tried WinMD5sum, but if you just run 'md5sum nameofyourfile' you'll get the MD5 checksum.

---

### Post by icechen1 on 2007-11-28
Linux got this tool intergrated in the command line just do ```
md5sum [filename here] 
```and compare the result with the md5sum

---

### Post by KIAaze on 2007-11-28
Yes, I know that command. But I was looking for a way to automatically compare them.

Here's what WinMD5sum looks like:
[http://img515.imageshack.us/my.php?image=iso14lt0.png](http://img515.imageshack.us/my.php?image=iso14lt0.png)

Currently, I have to run md5sum, copy both checksums into a text file and then select one and run find to see if they are the same. (or compare manually which is error prone)

I suppose such a program would be quite easy to write if md5sum is used in it. (shellscript with zenity or python-gtk for example)
I was just wondering if it already existed or not.

And it would be really nice to have such a compare function integrated into K3B. :)

---

### Post by =velkyn= on 2007-11-28
> **KIAaze said:**
> 
... But it doesn't seem to offer a way to compare it to the correct checksum.
I can't even copy the checksum number from the window.

I don't understand what you need more to compare the checksum.
Once you have the correct one, calculate the md5 of your file via terminal, or using k3b, and take a brief look to the result.
You don't need to check every single digit, because of the way the md5 is computed, if just a character in the file is different, the result is _completely_ different.

Does this help you?

---

### Post by jken146 on 2007-11-28
In K3B, you can paste in the correct md5sum and it will compare it.

---

### Post by Whiffle on 2007-11-28
If you want to check it, do this

```

md5sum nameoffile > blah
md5sum -c blah

```

heres what that does on mine:
```

andy@blacktop:~$ md5sum silent-1024x768.jpg > blah
andy@blacktop:~$ md5sum -c blah
silent-1024x768.jpg: OK

```

FYI, that information is in the man file.

---

### Post by KIAaze on 2007-11-28
> **jken146 said:**
> In K3B, you can paste in the correct md5sum and it will compare it.

Oops, didn't see it. :oops:
Yes, it's all in the right-click...

Command-line version understood too now. Had to write the md5 sum into a text file with the filename next to it separated by two spaces.
Thanks.

---

