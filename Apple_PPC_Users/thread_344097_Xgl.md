---
title: "Xgl"
date: 2007-01-22
forum: Apple PPC Users
---

### Post by youthforlinux on 2007-01-22
im convincing my friend to use ubuntu.  I use x86 but he only has ppc computers at home
he wants to use his ibook
can he use xgl/compiz for eye-candy etc.?:lolflag: :guitar:

---

### Post by Sqwishy on 2007-01-22
he should use beryl. there are several guides on the forums. if he has nvidia
[http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl+howto](http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl+howto)

otherwise search the forums for a beryl guide for his card

---

### Post by 3rdalbum on 2007-01-23
I don't believe Sqwishy is a PowerPC user - if they were, they wouldn't have linked to a guide that only works on x86.

Youthforlinux, I don't think it's a good idea running Beryl on an iBook as it will be very slow. The best thing to do to see if it will work is to run Ubuntu on it. When Ubuntu has loaded, put the following command in:

```
glxinfo | grep "direct rendering"
```

If you get "direct rendering: Yes" being returned in your terminal, then the card is likely to support Beryl. You can try installing Beryl from source and seeing if it runs.

---

### Post by youthforlinux on 2007-01-23
ok ill try out the command then

---

### Post by Sqwishy on 2007-01-23
> **3rdalbum said:**
> I don't believe Sqwishy is a PowerPC user - if they were, they wouldn't have linked to a guide that only works on x86. oh oops, didn't realize he had a powerpc. and btw the guide works for amd64 to.

---

### Post by 3rdalbum on 2007-01-24
> **Sqwishy said:**
> oh oops, didn't realize he had a powerpc. and btw the guide works for amd64 to.

An honest mistake. Yep, I realise the guide works for AMD64 too, but it's all x86. After all, the G5 Macs are actually PowerPC-64(bit), but we still refer to them as PPC :-)

---

### Post by polkajunior on 2007-01-24
well they are PPC just a 64 bit version

---

