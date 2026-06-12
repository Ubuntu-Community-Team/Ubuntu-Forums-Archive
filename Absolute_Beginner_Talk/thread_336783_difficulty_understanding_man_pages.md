---
title: "difficulty understanding man pages"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by JermainWijnhard on 2007-01-12
Hi,

I'm trying to learn to work with the Terminal and i try to make good use of the man pages. But I'm having difficulty understanding the synopses of the commands. Is they're a guide on how understand them? Some parts, like [--regexp=<regexp>] are total gibberish to me, but i want to know what it means. If i can be linked up, i'd appreciate it.

---

### Post by kj1h234lkj1234 on 2007-01-12
Ironically, you can type:

```
man man
```

to get a manual on how to read the manuals. :D

One major tip that is helpful, anything enclosed in brackets ( [ and ] ) is optional.

---

### Post by Arndt on 2007-01-12
> **JermainWijnhard said:**
> Hi,

I'm trying to learn to work with the Terminal and i try to make good use of the man pages. But I'm having difficulty understanding the synopses of the commands. Is they're a guide on how understand them? Some parts, like [--regexp=<regexp>] are total gibberish to me, but i want to know what it means. If i can be linked up, i'd appreciate it.

"man man" says this, among other things:

```
       The following conventions apply to the SYNOPSIS section and can be used
       as a guide in other sections.

       bold text          type exactly as shown.
       italic text        replace with appropriate argument.
       [-abc]             any or all arguments within [ ] are optional.
       -a|-b              options delimited by | cannot be used together.
       argument ...       argument is repeatable.
       [expression] ...   entire expression within [ ] is repeatable.
```

In your example,

> [--regexp=<regexp>] 

there is an additional convention, namely that of putting < > around something when italic style is not available. But it is available in man pages, so this shouldn't be used there, in my view.

--regexp is the option itself. It uses two dashes because the original Unix convention is that single letter options (which were the only kind) are preceded with one dash. This doesn't stop some programs from using single dashes for multiple-letter options, though.

The word regexp itself refers to regular expressions, of which there are many variants, so hopefully your man page describes further down exactly what is meant. You can do "man 7 regex".

---

### Post by JermainWijnhard on 2007-01-12
I found a really simple guide after a lot of searching. Its really for the 1st timers with terminals: [http://www.linux.org.mt/node/49#N10025](http://www.linux.org.mt/node/49#N10025)

---

### Post by blackened on 2007-01-12
> **JermainWijnhard said:**
> Hi,

I'm trying to learn to work with the Terminal and i try to make good use of the man pages. But I'm having difficulty understanding the synopses of the commands. Is they're a guide on how understand them? Some parts, like [--regexp=<regexp>] are total gibberish to me, but i want to know what it means. If i can be linked up, i'd appreciate it.

Have faith. I don't even bother with regular expressions (what the --regexp stands for), it's just too much stuff to remember if you've dealt with their not-so-nuanced implementations across different programming languages.

---

