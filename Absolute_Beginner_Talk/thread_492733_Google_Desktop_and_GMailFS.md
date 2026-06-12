---
title: "Google Desktop and GMailFS"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-07-05
I have installed Google Desktop and GMailFS via Synaptic but whats next? how am I going to use these
applications?

Thanks

---

### Post by cleverselfreferentialname on 2007-07-05
Run:
dpkg -L pkgname
with the name of any package, to see all the files installed by that package.

For example:
dpkg -L wine
returns a ton of output pertaining to wine, all it's various files.

Running:
dpkg -L gmailfs|grep bin
should return entries containing 'bin' in the paths of the filenames. Most likely it'll be something in /usr/bin. That's what you should be looking for.

Also, I'm sorry, but I have to mention it, Google Desktop should scare the hell out of you if you have any concern for your privacy. See: [http://en.wikipedia.org/wiki/Google_Desktop#Criticisms](http://en.wikipedia.org/wiki/Google_Desktop#Criticisms)

I'm wondering if there's any consolidated search tool like Google Desktop that is open source. Anyone?

---

### Post by delphiguy on 2007-07-05
thanks for the help and the the warning. i'll do that when i got home from office.

---

### Post by moredhel on 2007-07-05
google desktop is fine for windows, but...

GET BEAGLE! 

It's basically the same, but more intergrated with linux. and opensource.

:)

---

