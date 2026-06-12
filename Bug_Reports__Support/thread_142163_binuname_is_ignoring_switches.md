---
title: "/bin/uname is ignoring switches"
date: 2006-03-09
forum: Bug Reports / Support
---

### Post by virgule on 2006-03-09
Running Kubuntu 5.10 + ubuntu-desktop meta package
Kernel 2.6.12-10-powerpc
This is a fresh and up-to-date installation. Nothing has been 'modified' so far.

/bin/uname ignore any switches I feed to it:

```

  [virgule @ ~ ]# uname
Linux foxtwo 2.6.12-10-powerpc #1 Mon Feb 13 12:22:10 UTC 2006 ppc GNU/Linux
  [virgule @ ~ ]# uname -r
Linux foxtwo 2.6.12-10-powerpc #1 Mon Feb 13 12:22:10 UTC 2006 ppc GNU/Linux
  [virgule @ ~ ]# uname -a
Linux foxtwo 2.6.12-10-powerpc #1 Mon Feb 13 12:22:10 UTC 2006 ppc GNU/Linux
  [virgule @ ~ ]# uname -m
Linux foxtwo 2.6.12-10-powerpc #1 Mon Feb 13 12:22:10 UTC 2006 ppc GNU/Linux
  [virgule @ ~ ]# uname -v
Linux foxtwo 2.6.12-10-powerpc #1 Mon Feb 13 12:22:10 UTC 2006 ppc GNU/Linux
[virgule @ ~ ]# uname --v
uname (coreutils) 5.2.1
Written by David MacKenzie.

Copyright (C) 2004 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
  [virgule @ ~ ]# uname -s
Linux foxtwo 2.6.12-10-powerpc #1 Mon Feb 13 12:22:10 UTC 2006 ppc GNU/Linux
[virgule @ ~ ]# uname --s
Linux foxtwo 2.6.12-10-powerpc #1 Mon Feb 13 12:22:10 UTC 2006 ppc GNU/Linux
  [virgule @ ~ ]# uname -wtf?
uname: invalid option -- w
Try `uname --help' for more information.

```

What is the fix?

---

