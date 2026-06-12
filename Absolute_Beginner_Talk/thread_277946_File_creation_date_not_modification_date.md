---
title: "File creation date not modification date"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-15
I would like to know the creation date of my files.

When I look at properties I only see modification dates.

Is there a way to see when a file was created?

---

### Post by Arndt on 2006-10-16
> **kent41 said:**
> I would like to know the creation date of my files.

When I look at properties I only see modification dates.

Is there a way to see when a file was created?

No. Unix doesn't keep that information. It keeps three dates: last write, last read and last status change. The last one is involved in permission changes and name changes. To see it, use

```
ls -lc

```

[http://www.faqs.org/faqs/unix-faq/faq/part3/section-1.html](http://www.faqs.org/faqs/unix-faq/faq/part3/section-1.html)

---

### Post by kent41 on 2006-10-16
> **Arndt said:**
> No. Unix doesn't keep that information. It keeps three dates: last write, last read and last status change. The last one is involved in permission changes and name changes. To see it, use

```
ls -lc

```

[http://www.faqs.org/faqs/unix-faq/faq/part3/section-1.html](http://www.faqs.org/faqs/unix-faq/faq/part3/section-1.html)


Thank you for the response. I use the date created to do file maintenance , it is very important to me to know when the file was created and it helps me make decisions weather to delete the file. Maybe if I don't change the permissions I could use it to know when the file was created.
Thanks again
Kent

---

### Post by jnoreiko on 2007-04-21
> **Arndt said:**
> [http://www.faqs.org/faqs/unix-faq/faq/part3/section-1.html](http://www.faqs.org/faqs/unix-faq/faq/part3/section-1.html)

That FAQ doesn't really help -- it says linux doesn't store creation date, but why on earth not?
It's quite a useful thing to know.

---

### Post by Arndt on 2007-04-23
> **jnoreiko said:**
> That FAQ doesn't really help -- it says linux doesn't store creation date, but why on earth not?
It's quite a useful thing to know.

I googled a bit, but didn't find anything clear on the subject (in the news groups comp.unix.*, there have been discussions about it from time to time). Back when Unix was designed, having a fourth date in inodes was probably felt to take too much space. I seem to remember having read something about it in a book about Unix, but that's no big help, I guess.

---

