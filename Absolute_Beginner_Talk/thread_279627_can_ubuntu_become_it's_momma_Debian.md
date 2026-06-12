---
title: "can ubuntu become it's momma Debian?"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by psycosmyth on 2006-10-18
Not that I need to but my curiosity got me here anyhow, I was wondering if Ubuntu could be converted to full Debian.

---

### Post by Najand on 2006-10-18
> **psycosmyth said:**
> Not that I need to but my curiosity got me here anyhow, I was wondering if Ubuntu could be converted to full Debian.

Well, basically I don't think there is no need for that....

---

### Post by psycosmyth on 2006-10-18
I'm happy with the way it is, jusy wondering;)

---

### Post by dddouglas on 2006-10-18
being DebIan based is not the same as being partially Debian. To be fully Debian it would no longer be Ubuntu but Debian. So why would you want to? If you want Debian then get it and it will coexist with you other OS's.

---

### Post by skymt on 2006-10-18
I think you can crossgrade using apt-get, but it would be a lot (a *lot*) of work. You would basically need to change your sources.list to a Debian one, remove everything, then install everything from Debian.

---

### Post by psycosmyth on 2006-10-19
I guess I'll stick to Uby, I researched Debian's repositories and I feel that the Ubuntu team got it right! This is much more refined than Ian's kernels although I admire his creation deeply.:)

---

### Post by Najand on 2006-10-22
Well, I don't want to have a new edition after 7 years or something like what is happening with Debian now... Debian is nice; but I personally prefer ubuntu.

---

### Post by az on 2006-10-22
> **psycosmyth said:**
> Not that I need to but my curiosity got me here anyhow, I was wondering if Ubuntu could be converted to full Debian.

Ubuntu and Debian are not binary-compatible.

That being said, Ubuntu syncs up with Debian regularly (sometimes more than once per release).

You can have success in doing this by dist-upgrading to whichever release came last.

For example, if you are running a release of Ubuntu that was released before Sarge, you can change your sources.list and dist upgrade to Sarge.

I suspect that when Etch is released, you would be able to dist-upgrade from Dapper that way.  I don't know about Edgy, though.  I think that would be too close since Etch will have some packages that preceed Edgy.

So, it's a bit complicated, and not reccommended, but you can do it.  Free up a weekend and do it for fun!

---

