---
title: "BOINC 5.4.11 on Dapper?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by txr13 on 2007-05-09
I'm running Kubuntu 6.06 LTS (Dapper) on a server box. I access this through an SSH terminal, so I don't use any GUI to manage it.

Currently I have installed BOINC version 5.4.9 from the universe repo using apt-get. Works fine, except that I need a feature in version 5.4.11 or higher. A cursory inspection of available packages ([http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/pool/universe/b/boinc/](http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/pool/universe/b/boinc/)) seems to show that there is a packaged version of BOINC 5.4.11 out there. However, apt isn't picking it up, even after updating the package lists. I have also tried enabling the backport sources without success.

I don't want to have to build this manually, or download and install it from Berkeley itself. While I could do that, I'd like to keep this managed within apt for neat and tidy server administration.

Finally, sorry for posting in Absolute Beginner Talk if this would have been better addressed in another section of the forum. I'm a forum newb. :P

---

### Post by Seisen on 2007-05-09
The reason apt isn't picking it up is the fact that it isn't in your source list. You can try addding it to your source list and see if you can it work.

---

### Post by txr13 on 2007-05-09
Stupid question: Exactly how?

I know how to get at the sources.list file, but I don't know how to format a new deb line to point apt-get at what it wants. I either end up with a 404 Not Found or an error 25 Malformed when I use apt-get update.

---

### Post by Seisen on 2007-05-09
```
deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/pool universe
``` try that and see if it works.

---

### Post by txr13 on 2007-05-09
Tried that line both with and without a trailing slash after "pool", but both attempts return "E: Malformed line XX in source list /etc/apt/sources.list (dist parse)" (I misdescribed this as an error 25. It doesn't have a specific error number.)

---

