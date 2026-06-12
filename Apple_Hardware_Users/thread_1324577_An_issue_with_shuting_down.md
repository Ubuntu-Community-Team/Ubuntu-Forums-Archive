---
title: "An issue with shuting down"
date: 2009-11-12
forum: Apple Hardware Users
---

### Post by cuddy2977 on 2009-11-12
Hi there.

I’m a relative newcomer to Ubuntu, and I’ve installed Xubuntu 6.06 ppc, on an iMac 400MHz G3.

The actual installation went fairly smoothly, as found enough walk-through’s, online, to help.

However, I find that it will not shut-down, as I’d expect it to; it simply restarts, after displaying the usual shutdown routine.

Is there a walkthrough, to let me resolve this issue?  I’ve found online.

---

### Post by llamabr on 2009-11-13
what method are you using to shutdown?

From a terminal, this should work:

```
sudo shutdown -h now
```

The -h flag is for halt, which you could replace with a -r for reboot.

---

### Post by cuddy2977 on 2009-11-13
> **llamabr said:**
> what method are you using to shutdown?

From a terminal, this should work:

```
sudo shutdown -h now
```

The -h flag is for halt, which you could replace with a -r for reboot.



I’m trying to use the bog standard off button; the one in the top right hand corner?

I’m no coder, so that’s usually the route I’d go … hang on

---

### Post by cuddy2977 on 2009-11-13
> **cuddy2977 said:**
> I&#8217;m trying to use the bog standard off button; the one in the top right hand corner?

I&#8217;m no coder, so that&#8217;s usually the route I&#8217;d go &#8230; hang on

Just tried that bit of command line; it powers down &#8230; and powers right back on, again &#8230;

---

### Post by llamabr on 2009-11-23
That is strange.  This might not be a mac specific question.  You might get better results by asking at a more general forum, like general questions, or absolute beginner.

---

