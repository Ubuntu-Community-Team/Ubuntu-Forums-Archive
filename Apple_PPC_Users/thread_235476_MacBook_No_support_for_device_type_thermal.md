---
title: "MacBook: No support for device type thermal?"
date: 2006-08-13
forum: Apple PPC Users
---

### Post by hajk on 2006-08-13
Much has been written already about the high temperature problems of the MacBook. Any query would start, I think, with checking the processor temperature with the "acpi -V" command, yet on my MacBook running the latest 686-SMP kernel (2.6.15-26), the response is

     Battery 1: charged, 99%
No support for device type: thermal
  AC Adapter 1: on-line

Mmm, I can't imagine that a modern processor like the Core Duo wouldn't support this... so what's wrong with the Ubuntu kernel? Or did I not set things up correctly?

Comments, please.

---

### Post by stmiller on 2006-08-13
> latest 686-SMP kernel (2.6.15-26)

This could be the problem. You could recompile a newer kernel. 
[http://www.kernel.org/](http://www.kernel.org/) It would have better support for the core duo systems. Or wait for the next ubuntu kernel update.

---

### Post by martinbures on 2006-08-16
I would imagine that there are a bunch of Ubuntu-specific patches applied to the kernel - I would like all of the new stuff without giving up the user-friendly patches.  How do I get my hands on the beta ubuntu kernel - like the one going into edgy, or how do I compile my own kernel with all of the ubuntu patches applied?  I have used gentoo's kenel making stuff but I have never done this with a Debian-based distro.

Thanks.
martin.

---

### Post by hajk on 2006-08-16
Yeah, I've been thinking about installing the new 2.6.17 kernel from Edgy, or may be it could be made available to Dapper through backports... But then, I could also wait since I'm not using my MacBook/Ubuntu  much or for long periods right now. Decisions, decisions...:-k

---

### Post by martinbures on 2006-08-17
Ok - I found this:

[http://ubuntuforums.org/showthread.php?t=222018&highlight=kernel](http://ubuntuforums.org/showthread.php?t=222018&highlight=kernel)

so I am going to give it a shot.  Wish me luck!

---

