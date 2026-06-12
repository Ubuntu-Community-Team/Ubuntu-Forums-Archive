---
title: "Perl Libraries installed but not being seen?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by HedonismBot on 2006-11-28
Hey forum fam

So, I'm trying to install OCS Inventory NG on a 6.10 box, ran apt-get when I built the server installed Perl with all options, all other languages, new versions of GCC compiler and make and all that, but when I run the setup.sh script I get:

```

+----------------------------------------------------------+
| Checking for required Perl Modules...                    |
+----------------------------------------------------------+

Checking for DBI PERL module...
Found that PERL module DBI is available.
Checking for Apache::DBI PERL module...
Found that PERL module Apache::DBI is available.
Checking for DBD::mysql PERL module...
Found that PERL module DBD::mysql is available.
Checking for Compress::Zlib PERL module...
*** ERROR: PERL module Compress::Zlib is not installed !

Installation aborted !
```

BUT, what's bugging me is that ZLIB IS INSTALLED. I installed it with apt-get at the exact same time (same command) as the others, but it's not seeing it.

Any ideas? Anyone else have this issue.

Please let me know, peace. :cool:

---

### Post by belaflek on 2007-08-06
I am getting the exact same thing.
I've gone so far as to downloading the packages from CPAN and installing the packages and thier dependancies manually with no luck

---

### Post by tr333 on 2007-08-07
Did you install the "libcompress-zlib-perl" package via apt-get or a different package?

---

