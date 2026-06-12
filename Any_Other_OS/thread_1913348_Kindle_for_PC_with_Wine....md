---
title: "Kindle for PC with Wine...????"
date: 2012-01-22
forum: Any Other OS
---

### Post by sanderella on 2012-01-22
Has anyone downloaded this and got it working?

---

### Post by Double.J on 2012-01-22
Hi there!

Interesting.. I had it in my head that this was a no go, don't know why, I just looked on WineHQ and saw most versions of kindle for PC have between a silver and platinum rating, so i'll try and install and report back - as I already have a kindle account :)

All the best!

---

### Post by Double.J on 2012-01-22
Hi there all working!

I upgraded wine on 11.10, installed the Kindle for PC .exe from amazon - the installer completes fine, but Kindle crashes on boot.

I took the fix from the wine HQ site:

Navigate here
```

cd .wine/drive_c/windows/winsxs/manifests
```

And rename the following file
```

mv -v x86_microsoft.vc90.crt_1fc8b3b9a1e18e3b_9.0.30729.4148_none_deadbeef.manifest x86_microsoft.vc90.crt_1fc8b3b9a1e18e3b_9.0.30729.4148_none_deadbeef.manifest.old

```

The fix suggests making the directory read only, but I wasn't sure what other negatives this may have in the future, so I just saved some info on how to fix the problem in a .txt file inside the .wine directory for future reference.

But yes, once done, it's working on 11.10 and 12.04 now - picked up my ebooks from the mirror and opened the browser to let my buy a new one.

All good from the limited testing :)

Hope it helps!

Edit Kindle content is stored in your home directory under /My\ Kindle\ Content :)

---

### Post by sanderella on 2012-01-22
Thank you! Working beautifully now. :KS

---

### Post by cmcanulty on 2012-05-11
Wow pretty obscure but works, thanks!

---

### Post by nitroguy on 2012-06-09
What the...?

That is by far the craziest fix I've encountered yet.

But it works! Thanks!

---

### Post by Kirk Schnable on 2012-12-30
I will confirm that this fix is working with Wine 1.4 on Ubuntu 12.04 LTS and the latest Kindle available from Amazon's website today (1.10.5 - 40382).

Thanks for the post!  I will definitely be purchasing the Kindle books for my online class this semester rather than paper ones, since I can now read them on my Ubuntu laptop!

---

### Post by mamamia88 on 2012-12-31
> **Kirk Schnable said:**
> I will confirm that this fix is working with Wine 1.4 on Ubuntu 12.04 LTS and the latest Kindle available from Amazon's website today (1.10.5 - 40382).

Thanks for the post!  I will definitely be purchasing the Kindle books for my online class this semester rather than paper ones, since I can now read them on my Ubuntu laptop!

you can do that but then you'd get no resale value at all and college books are damn expensive. also i'd invest in a real kindle.  if you can afford college textbooks a $70 kindle wouldn't hurt you much.

---

### Post by Kirk Schnable on 2012-12-31
> **mamamia88 said:**
> you can do that but then you'd get no resale value at all and college books are damn expensive. also i'd invest in a real kindle.  if you can afford college textbooks a $70 kindle wouldn't hurt you much.

I thought about the resale value, but for a $50 and $8 book for my online class, I thought the portability and keyword search ability were worth the loss. 

I have the Kindle app on my iPad, but having the book on the computer which I'll be using most of the time for coursework seems more advantageous.

---

### Post by Jpedros2 on 2013-01-05
Works for me in ubuntu 12.10.
Thanks a lot.
Regards,

---

### Post by david60 on 2013-08-19
I'm just switching over from Windows 7 to Ubuntu... (12.04.2 LTS)... A total newbie!  The above code worked for me with no problems.  *Thank you!*

---

### Post by 3rdalbum on 2013-08-22
Er.. why would you go to all that trouble when you can just use Amazon Cloud Reader?

---

### Post by monkeybrain20122 on 2013-08-22
Can't you just use Calibre?
[http://calibre-ebook.com/](http://calibre-ebook.com/)

---

### Post by mv-email on 2013-08-25
I just installed VC8 runtime and worked for me. M$ provides that at:
[http://www.microsoft.com/en-us/download/confirmation.aspx?id=29](http://www.microsoft.com/en-us/download/confirmation.aspx?id=29)

So just install it with:
wine vcredist.exe

---

