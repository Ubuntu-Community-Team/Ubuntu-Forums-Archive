---
title: "What the meaning of the number 6 in libstdc++6-4.1-dev?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by jamadagni on 2006-08-08
In libstdc++6-4.1-dev, I understand that 4.1 is the so-called version number. But what does 6 mean? 

IIRC I have seen a file called libstdc++.so.6 -- is this 6 and that 6 the same? What is its meaning?

Further, the package is described as GNU Standard C++ Library v3. So if the library is version 3, and IIUC (if I understand correctly) the implementation is at version 4.1, then what is 6 here?

Thanks.

---

### Post by moma on 2006-08-08
**GNU Standard C++ Library v3**
is a specification of C++ standard library functions.  C++ Library v3 document is the latest spesification that determines how standard classes such as std::string, std::vector and std::list etc. should work. It's merely a specification, not a package.

**Versioning of libraries:**

All library names in Unix/Linux comprises of these components:
libraryname-<[COLOR="Sienna"]major num[/COLOR]>-<[COLOR="Sienna"]minor num[/COLOR]>.<[COLOR="Sienna"]micro release num[/COLOR]>. 

For example "libstdc++6-4.1-dev"  has major version number 6, minor number 4, and micro release number 1.

**Major version number:**
If the major number changes (eg. from 6 to 7) _it will brake the function call interface_ of the library and applications that link to that library need to be revised and re-compiled.

"libstdc++6" is the 6.th Debian-package version of libstdc++.  It implements the C++ Library v3 specification.

**Minor number:**
A change in minor-number will NOT brake the call interface and the library will still be upward-compatible. New functions may have been introduced but NONE of the existing functions have been changed. 

**Micro release number:**
Is normally a bug-fix release of a library. Micro releases will never introduce new functions or functionality.

Notice that programs search for libraries by their **library name** + <**major version number**> (eg.   [COLOR="black"]**libstdc++.so**[/COLOR].**6**). 
Therefore the library name is always a symbolic link to it's latest and newest  minor (or micro) revision. 

A sample:
$ [COLOR="Green"]ls -l /usr/lib/libstdc*[/COLOR]
lrwxrwxrwx 1 root root     18 2006-05-24 19:54 /usr/lib/[COLOR="Red"]libstdc++.so.6[/COLOR] -> libstdc++.so.6.0.7    
-rw-r--r-- 1 root root 849556 2006-04-20 22:19 /usr/lib/libstdc++.so.6.0.7  [COLOR="SlateGray"]( = libstdc++.so.6 with some bux fixes, thus the name libstdc++.so.6.0.7)  [/COLOR]

---

### Post by jamadagni on 2006-08-08
[quote=moma]For example "libstdc++6-4.1-dev"  has major version number 6, minor number 4, and micro release number 1.[/quote]
Well, other applications have the general system you describe too, for example the Linux kernel. But there, the major version number is stringed together with the minor and micro numbers - eg. 2.6.17.8. Is there a reason that for the libraries alone, the major version number is not stringed together with the other numbers?

Further, you wrote: > libraryname-<major num>-<minor num>.<micro release num>, but there is no hyphen between the library name and the major number. (Just remarking in passing.)

> "libstdc++6" is the 6.th Debian-package version of libstdc++
Why "Debian-package version"? I have libstdc++.so.6 on my SUSE installation too.

Thanks for the neat clarification of the numbers. I just have a few more questions above.

---

