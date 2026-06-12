---
title: "CheckGmail Suddenly Stops Working"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by cool_penguin on 2007-12-13
Hi Guys, 

I was wondering if any of you have noticed this. Check Gmail has suddenly stopped working. It was working fine until last evening. But since this morning, it is unable to log in. I wonder if Gmail has again changed its mode of authentications. 


Cheers,
Harry

---

### Post by lkz on 2007-12-13
I have the same problem.

---

### Post by hotweiss on 2007-12-13
This should fix it:

> 
wget [http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail](http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail)
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail

---

### Post by nikolas68 on 2007-12-13
> **hotweiss said:**
> This should fix it:

I've the same problem and i've tried this but doesn't work for me....i get this message in return

```
Resolving checkgmail.svn.sourceforge.ne...ail... failed: Name or service not known.
```

---

### Post by hotweiss on 2007-12-13
> **nikolas68 said:**
> I've the same problem and i've tried this but doesn't work for me....i get this message in return

```
Resolving checkgmail.svn.sourceforge.ne...ail... failed: Name or service not known.
```

It's because the forum software turncates the visible link. Click on the link after wget in my previous post, copy the address from you address bar, write wget in terminal, paste the link you just copied, and then paste the next 2 steps from my previous post.

---

### Post by nikolas68 on 2007-12-13
> **hotweiss said:**
> It's because the forum software turncates the visible link. Click on the link after wget in my previous post, copy the address from you address bar, write wget in terminal, paste the link you just copied, and then paste the next 2 steps from my previous post.

OOPPSSSS!!!:oops:

thanks

---

