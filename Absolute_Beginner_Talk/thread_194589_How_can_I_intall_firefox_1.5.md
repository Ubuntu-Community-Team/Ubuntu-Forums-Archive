---
title: "How can I intall firefox 1.5?"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by jeanvial on 2006-06-11
Hi.

I downloaded fierox 1.5 whit tar. extenxion but i cant istall them.

¿How can I install them?

---

### Post by 23meg on 2006-06-11
Which version of Ubuntu are you using? If it's Breezy (5.10) you can refer to [these instructions]("http://ubuntuforums.org/showthread.php?t=176636"). Dapper already comes with Firefox 1.5 .

---

### Post by Fafnir on 2006-06-11
[QUOTE=jeanvial]Hi.

I downloaded fierox 1.5 whit tar. extenxion but i cant istall them.

¿How can I install them?[/QUOTE]

If you're using Dapper (latest release of Ubuntu), you should be able to get it from the repositories - either open a terminal and type:

```
sudo apt-get install firefox
```

or open Synaptic Package Manager (under System->Administration) and install the firefox package from there.

If you're using Breezy, there's a guide available on installing 1.5 manually [here]("https://wiki.ubuntu.com/FirefoxNewVersion"), or a script (and instructions) to do it for you [here]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5").

In Ubuntu, you very rarely need to compile from source (which is how you would install Firefox from the .tar.gz) - there are simpler ways!

Hope that helps!

Hope that helps!

---

### Post by glotz on 2006-06-11
[QUOTE=Fafnir]you very rarely need to compile from source (which is how you would install Firefox from the .tar.gz)[/QUOTE]

Nobody knows what .tar file he refers to... However if it's Firefox from mozilla.org then it's probably the binary file. A .tar.gz can contain anything, not just source code.

---

### Post by jeanvial on 2006-06-13
Thanks.

I will try.

---

