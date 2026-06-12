---
title: "First post for help: alternate clocks and calendars"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Hustle Kong on 2007-06-30
Okay... I have found a number of java clocks that will display decimal time based on the french revolutionary method of reckoning time.

The day is divided into 10 hours, each hour divided into 100 minutes. Each minute into 100 seconds.

So:
1 decimal hour = 2.4 regular hours
1 decimal minute = 1.44 regular minutes
1 decimal second = 0.864 regular seconds


So as of right now (21:00:52), it is 8:75:60 by the decimal method.

I would like to have a little display on my panel (I have regular and "internet time" already), and I assume something like this can be created. I would like to know how, if anyone knows what/where I need to learn.

I also wonder if there is anyway to have the discordian calendar (like on the ddate program) be my "default" calendar.

But just starting out with Linux (this is my first experience with it), I am fairly useless.

Thank you very much in advance for any help on either issue.

---

### Post by pyros on 2007-06-30
wow, i'd never heard of french revolutionary time, although I suppose that's what's meant by decimal time. to add a clock to the panel like that, you'd need to create a panel applet. that means that you will need to know how to write a program in one of the many languages with the bindings to do so. I would recommend starting here:
[http://www.pygtk.org/articles/applets_arturogf/](http://www.pygtk.org/articles/applets_arturogf/)

---

### Post by Hustle Kong on 2007-06-30
I am bookmarking that site for when I have a little bit more brain power to tackle it. Thanks a bunch! :)

---

### Post by pyros on 2007-06-30
> **Hustle Kong said:**
> I am bookmarking that site for when I have a little bit more brain power to tackle it. Thanks a bunch! :)

no problem. it's a bit of an undertaking, but simple number conversion is one of the easiest programming tasks to perform. it's usually covered in the first or second chapter of any howto for a particular language.

---

### Post by Hustle Kong on 2007-07-01
Well, I DID find this:

[http://search.cpan.org/~pfeiffer/Time-Decimal-0.06/Time/Decimal.pm](http://search.cpan.org/~pfeiffer/Time-Decimal-0.06/Time/Decimal.pm)

That looks to be what I need, I believe. Of course, I don't know how to actually USE it. :\

---

