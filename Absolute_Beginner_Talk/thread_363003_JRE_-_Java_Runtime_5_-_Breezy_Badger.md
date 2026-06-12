---
title: "JRE - Java Runtime 5 - Breezy Badger"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by blindpete on 2007-02-16
Hello,

I searched through here before posting looking for the answer.
I checked all the repositories in synsptic, searched for JRE found nothing releavent.

I tried the command line:
[PHP]sudo apt-get install sun-java5-pelugin[/PHP]
and I get the error message:
[PHP]E: Couldn't Find Package Sun-Java5-plugin[/PHP]

I am at a loss as to how to proceed now?

---

### Post by igknighted on 2007-02-16
> **blindpete said:**
> Hello,

I searched through here before posting looking for the answer.
I checked all the repositories in synsptic, searched for JRE found nothing releavent.

I tried the command line:
[PHP]sudo apt-get install sun-java5-pelugin[/PHP]
and I get the error message:
[PHP]E: Couldn't Find Package Sun-Java5-plugin[/PHP]

I am at a loss as to how to proceed now?

I'm only guessing, but if you copy/pasted that result from the terminal then you capitalized sun and java, which you should not.  Also, it may not be in the breezy repo's, as I don't know if java 1.5 was out yet when breezy came out.  Do you need Java5?  An update to dapper/edgy might be needed.  Finally, have you enabled all repo's?  The repo sun's java is no isn't enabled by default.

---

### Post by blindpete on 2007-02-16
Thanks, no I retyped the lines in here and it was not capitalized.  How do I add sun repo?

I can not upgrade to dapper-drake, it ran very very slow on that old pc,  I stepped back to breezy with format and it runs fine.

I need the JRE5 for my daughter to play games on [http://pbskids.org/games/index.html](http://pbskids.org/games/index.html)
(Its her computer)

---

