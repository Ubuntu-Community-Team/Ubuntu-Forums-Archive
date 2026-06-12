---
title: "Installing LightZone"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by mikemcfarlane on 2007-06-29
Hi

I'm trying to install Lightzone without any success and previous posts don't seem to cover where I am. 

I've downloaded Lightzone and unzipped the tarball into my home dir. I also installed Java 5 from Add/Remove Applications as the Lightzone website said that Java was needed, although it also appears to be included with the Lightzone download.

In the Lightzone dir:
sh Lightzone
gives the following message:
testing JVM in /home/mike/LightZone/jre ...
testing JVM in /usr ...

And then nothing. I can't make sense of the shell script myself to understand where it is failing. Double clicking on the script in Nautilus has no effect that I can see either.

Thanks in advance for any help.

Mike

---

### Post by Seisen on 2007-06-29
Did you change it to reflect that you are using Java 5.0?

```
 sudo update-alternatives --config java
```

---

### Post by mikemcfarlane on 2007-06-29
Hi

I tried the update alternatives as you suggested, but it didn't get me any further. The Sun version was already selected by default.

Mike

---

### Post by mikemcfarlane on 2007-06-29
Found the answer at:

[http://kast-dev.com/pipermail/lightzone/2007-February/000268.html](http://kast-dev.com/pipermail/lightzone/2007-February/000268.html)

>i had to insert
> -client KNOWN
> into jre/lib/i386/jvm.cfg before any other "-" lines, otherwise the program 
> failed to start:

Lightzone now starts, hooray.

---

