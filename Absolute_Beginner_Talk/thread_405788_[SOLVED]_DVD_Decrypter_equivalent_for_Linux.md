---
title: "[SOLVED] DVD Decrypter equivalent for Linux?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-04-10
I am, bit by bit, making the transition from Windows to Ubuntu, helped in large part by the great threads and suggestions on this site.

One app that I use(d) in Windows was DVD Decrypter. My primary usage of this was to get the MPEG stream from DVD+RWs that I'd recorded on my stand alone DVD recorder, take out the commercials, tidy up, etc and then record onto DVD+Rs

I found this site which talks about installing it under WINE - [http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/) - but it doesn't seem to work for me. The problem is finding SCSI emulation (the app tells me I don't have it), and I followed the steps to no avail.

So, the question is either:

- Can someone show me how to fix it?

or...

- Is there a Linux prog I could use instead? (which I suppose is the preference!)

Thanks in advance!

---

### Post by JAwuku on 2007-04-10
Yes, there is an equivalent for Linux, called **dvdrip**.

Just make sure the **universe** and **multiverse** repositories are enabled (see [www.ubuntuguide.org](www.ubuntuguide.org) for details)

and just type in at the command prompt:
```
sudo apt-get install dvdrip
```

and it will install its dependencies.

---

### Post by qprfact on 2007-04-10
Brilliant! I will give it a try!

---

### Post by Efros on 2007-04-10
dvdshrink is one of those gold applications that work well under wine.

---

### Post by qprfact on 2007-04-10
Ah. got that so will give that a try too!

---

