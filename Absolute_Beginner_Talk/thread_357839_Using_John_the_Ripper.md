---
title: "Using John the Ripper"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-02-10
Hi,

Perhaps this is one of those questions where the answer will be 'If you have to ask, you shouldn't be doing it!'

However, I've been thinking about security, and I'd like to make sure that my password isn't too easily crackable.  I've got John the Ripper via Symantic, read the help and man pages, done some googling, but still can't figure out what *exactly* I'm supposed to do.

If I get it right, I have to run it followed by the name of the password file I want to check?  But I've no idea where that file is.

I'd be grateful if someone could give me a few tips, (or alternatively advise me to leave it well alone!)

thanks.

---

### Post by jvc26 on 2007-02-10
EDIT:: Reread your post.
What type of password file is this? The man pages will have told you how to run it, so presuming what you've said above is correct, then the command:
```

packagename /path/to/passwordfile

```
Il

---

### Post by supirman on 2007-02-10
Here's a tutorial with some examples: [<John the Ripper Tutorial>]("http://www.osix.net/modules/article/index.php?id=455")

---

### Post by whitefort on 2007-02-10
Thanks, guys.

I think I may have misunderstood this whole thing...  I thought that my password was kept somewhere in a file in my Ubuntu installation (presumably it is, but I have no idea where), and that I just had to point 'john' at it and it would start testing to see if it could crack it.

It seems like it's a bit more complicated than that.  Perhaps I better leae it alone until I understand Ubuntu a bit better!

Thanks anyway!

---

### Post by MrKlean on 2007-02-10
To make it hard to crack your password.... use a combination of letters and numbers.  Make sure the sequential letters don't form a word found in the dictionary, and don't use a numbered sequency.  Also, don't use letters or numbers that can be associated with you..and.... the longer, the better , around 10 is good LOL!   Remeber, almost any password can be cracked if you want to spend the time doing it !!!

---

### Post by nhandler on 2007-02-10
At one point, I attempted to do the same thing you are doing now. Except, instead of using john the ripper, I made my own brute force script in pearl. I'm not sure if it was my sloppy coding, my computer, or both, but it took me a day to generate all the 4 3 2 and 1 character long passwords. I'm not even going to try and crack any longer password. I could probably have sped it up by not using symbols or numbers, but I wanted to make a full brute force app.

So, as long as your password is about 7 characters or longer, you should be fine. But, any password can be cracked if the person is determined enough.

---

### Post by supirman on 2007-02-10
> **whitefort said:**
> ..  I thought that my password was kept somewhere in a file in my Ubuntu installation (presumably it is, but I have no idea where), and that I just had to point 'john' at it and it would start testing to see if it could crack it.
...

The passwords in linux systems are typically stored (encoded) in the file /etc/passwd, but with the shadow suite installed, you'll see an 'x' in the password field in /etc/passwd, and the password will be stored in /etc/shadow.  



To try some stuff out, you can do:

```

$ cd
$ sudo useradd testuser
$ sudo passwd testuser
Enter new UNIX password:   (enter test as the password)
Retype new UNIX password:  (again, enter test)
$
$ sudo unshadow /etc/passwd /etc/shadow > mypasswd
$ sudo john mypasswd
Loaded 2 passwords with 2 different salts (FreeBSD MD5 [32/32])
test             (testuser)
$sudo john --show mypasswd
testuser:test:1002:1002::/home/testuser:/bin/sh

1 passwords cracked, 1 left

```

---

