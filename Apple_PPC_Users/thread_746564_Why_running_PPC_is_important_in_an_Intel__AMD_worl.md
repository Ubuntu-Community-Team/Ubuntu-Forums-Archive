---
title: "Why running PPC is important in an Intel / AMD world"
date: 2008-04-05
forum: Apple PPC Users
---

### Post by stream303 on 2008-04-05
For some, running PPC hardware, which is typically low consumer-level, and no longer produced, brings up the question of why it is important to support it, at least unofficially.

(This thread isn't to debate the decisions made by Ubuntu to stop offering official support, and I'm thankful that they have at least made the ppc forums and unofficial download repos available.  THAT thread(s) can be found elsewhere here, but I see no point in rehashing it.)

In today's Intel / AMD dominated world, I think it right that they concentrate their efforts, but always keep in mind that ports of any other architectures can be extremely valuable to help bring unforeseen bugs to the surface in their primary  support architectures.

Our NetBSD brethren have the right idea about portability.  See how they mention ppc for instance:

[http://www.netbsd.org/about/portability.html](http://www.netbsd.org/about/portability.html)

I would hope that Ubuntu and now even Sun remember that ports are extremely valuable in helping bring about primary architecture problems with their solutions to resolution just that much faster.

We're more than just guys wanting to keep their consumer-level ppc desktops alive for 20 years. :)

---

### Post by ssam on 2008-04-06
just to note, linux runs on more cpu architectures than netBSD these days
[http://www.kroah.com/log/linux/ols_2006_keynote.html](http://www.kroah.com/log/linux/ols_2006_keynote.html) (though most distros only target a very small subset).

---

### Post by nkbj on 2008-04-06
One reason for keeping Ubuntu PPC support is that it is nice to be able to test programs on both big-endian and little-endian systems with the same set of compilers, libraries etc.

Regards,
Niels Kristian

---

### Post by stream303 on 2008-04-06
> **ssam said:**
> just to note, linux runs on more cpu architectures than netBSD these days
[http://www.kroah.com/log/linux/ols_2006_keynote.html](http://www.kroah.com/log/linux/ols_2006_keynote.html) (though most distros only target a very small subset).

Thanks for that link!  What a great read..

I really like the *BSD's, but I haven't run it since I put NetBSD on one of my old-world ppc machines about 8 years ago.  Love their docs!

Ironically, if you do a make-world in *BSD, you are using the gnu compiler.  :)

---

### Post by stream303 on 2008-04-06
> **nkbj said:**
> One reason for keeping Ubuntu PPC support is that it is nice to be able to test programs on both big-endian and little-endian systems with the same set of compilers, libraries etc.

Exactly - and it is my hope that Ubuntu sees that having a ppc port, or even the sparc port, not only helps the end-users with that hardware, but provides devs a way to "think outside the box", if I can use that worn-out phrase, when problems arise in the primary architectures.

I find it interesting to see history repeating itself with FreeBSD now offering a ppc port download.  Originally the split between Free and Open BSD was over optimizing for the 386 architecture, whereas NetBSD stuck to extreme portability, so the ppc offering for FreeBSD is interesting.

What I don't know as an end-user is how well the developer-community works in the *BSD's.  And as Ubuntu has shown us, community is as important as the code itself; although I'm trying not to drink too much kool-aid. :)

---

