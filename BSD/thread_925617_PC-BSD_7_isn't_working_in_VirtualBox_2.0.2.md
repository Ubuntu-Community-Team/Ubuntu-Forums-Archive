---
title: "PC-BSD 7 isn't working in VirtualBox 2.0.2"
date: 2008-09-20
forum: BSD
---

### Post by Newuser1111 on 2008-09-20
It starts up then gets to the login screen,
After I log in the graphics look really messed up then it logs me back out.

---

### Post by cardinals_fan on 2008-09-20
> **Newuser1111 said:**
> It starts up then gets to the login screen,
After I log in the graphics look really messed up then it logs me back out.
Was the iso corrupted?  Did it install correctly?

---

### Post by Newuser1111 on 2008-09-20
The install ran fine.
How do I check the ISO?


And here's a picture of how it looks before it logs back out:
[http://playstationportablestuff.googlepages.com/PCBSD2193128038192389123123.png](http://playstationportablestuff.googlepages.com/PCBSD2193128038192389123123.png)

---

### Post by Le-Froid on 2008-09-21
> **Newuser1111 said:**
> The install ran fine.
How do I check the ISO?


And here's a picture of how it looks before it logs back out:
[http://playstationportablestuff.googlepages.com/PCBSD2193128038192389123123.png](http://playstationportablestuff.googlepages.com/PCBSD2193128038192389123123.png)

when you download the file from their website, it gives a md5 string under the download link. cd to the directory of the file you downloaded and type md5sum <filename> in a terminal. If the md5 string matches the one on the website, then the download is okay. If not, its broken.

---

### Post by Newuser1111 on 2008-09-21
They are correct.


Edit:
I changed it to 800x600x16 with vesa and now it works.
Edit:
1024x768x16 also works.

---

### Post by Le-Froid on 2008-09-21
> **Newuser1111 said:**
> They are correct.

I was looking on the forums and found this:
[quote=p_quarles]
PC-BSD (based on FreeBSD) currently does not work with Virtualbox. It says so right on Virtualbox's home page.
[/quote]

---

### Post by Newuser1111 on 2008-09-21
> **Le-Froid said:**
> I was looking on the forums and found this:But now I got it working.

---

### Post by mips on 2008-09-21
> **Newuser1111 said:**
> But now I got it working.

Mind sharing as others might find it useful.

---

### Post by theonlyrealperson on 2008-09-21
Yeah, I'd like to know too. I could never get it to work either!

---

### Post by Newuser1111 on 2008-09-22
> **mips said:**
> Mind sharing as others might find it useful.By changing it to 16 bit graphics instead of 32.

---

### Post by kk0sse54 on 2008-09-22
Has been working fine for me now if only NetBSD would work....

---

### Post by cardinals_fan on 2008-09-22
> **C!oud said:**
> Has been working fine for me now if only NetBSD would work....
I believe most BSDs work better in VMware.  Yet another reason not to use VirtualBox... ;)

---

