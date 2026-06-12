---
title: "Question on Aptitude search pattern"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-02-09
I'm searching for a package called 'libstdc++2.10-glibc2.2'.
```
aptitude search libstdc++2.10-glibc2.2
```
or
```
aptitude search 'libstdc++2.10-glibc2.2'
```
or
```
aptitude search "libstdc++2.10-glibc2.2"
```
does not return me any result.

However, if I use
```
aptitude search libstdc.*2.10-glibc2.2
```
the package is found.

Any reason why the first three commands do not return the expected package?

Thanks !

---

### Post by David Corrales on 2006-02-09
The period after libstdc?

---

### Post by Iowan on 2006-02-09
Regular expressions?  Just a (very) wild guess (or crazy suggestion).  What about the backtick (`)?

---

### Post by lha on 2006-02-09
Aptitude used [regular expressions]("http://gnosis.cx/publish/programming/regular_expressions.html"). At least
```
aptitude search \(libstdc\+\+\)\(2\.10-glibc2\.2\)
```
returns the package you are searching for.

---

### Post by David Corrales on 2006-02-09
You can also use the command:
**apt-cache search *package***

---

