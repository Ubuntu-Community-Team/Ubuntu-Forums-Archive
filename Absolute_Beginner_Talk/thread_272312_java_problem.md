---
title: "java problem"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-06
I can't get javacc to install. When I run synaptic, it gives me the message:

This package is an installer package, it does not actually contain the J2SDK 
documentation. You will need to download from one of the following archives

blahblahblah..........

Please visit now and download. The file should be owned by root.root and be copied to /tmp.
Press RETURN to try again, 'no' + RETURN to abort.

](*,) 
I was just randomly installing anything with the word java in it and it did this. If the workaround seems obvious, I apologize.  But I fail to understand why an absence of documentation would tank the installation process??

---

### Post by boban on 2006-10-06
If you want to have java documentation, then you need to dowload it form sun's homepage and put it in the /tmp directory...

---

### Post by saintj0n on 2006-10-06
So, it still installs java, it just didn't install the docs because I didn't download it?

---

### Post by boban on 2006-10-08
> **saintj0n said:**
> So, it still installs java, it just didn't install the docs because I didn't download it?

I think so...

---

### Post by saintj0n on 2006-10-08
Ok..here's the solution.

1. download from java website
2. Put file in /tmp
3. sudo -s chown root "filename"
rerun install program

I don't understand why you need root ownership on a stupid doc directory:confused:

---

