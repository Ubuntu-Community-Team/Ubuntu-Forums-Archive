---
title: "X-UTILITIES::CAPIX11;libXm.so.2. --what? LispWorks"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Alberio on 2008-01-27
I was trying to run LispWorks and I ended up getting this. (both from the .rpm install (via alien) and the alternative install)

I have libxmu-dev and libxmu-headers installed...

any ideas?

thanks in advance...

```

paarth@Astarael:~/LispWorks$ ./lispworks-personal-5-0-1-x86-linux
LispWorks(R): The Common Lisp Programming Environment Personal Edition
Copyright (C) 1987-2006 LispWorks Ltd.  All rights reserved.
Version 5.0.1
Saved by LispWorks as lispworks-personal-5-0-1-x86-linux, at 09 Jan 2007 15:47
User paarth on Astarael

Error: Could not register handle for external module X-UTILITIES::CAPIX11:
 libXm.so.2: cannot open shared object file: No such file or directory.
  1 (abort) Quit process.

Type :b for backtrace, :c <option number> to proceed,  or :? for other options

CL-USER 1 : 1 > :b
Call to FLI::CREATE-EXTERNAL-MODULE
Call to FLI:REGISTER-MODULE
Call to X-UTILITIES::DO-ENSURE-MOTIF-LIBRARIES
Call to X-UTILITIES:ENSURE-MOTIF-LIBRARIES
Call to CAPI-MOTIF-LIBRARY::ENSURE-CAPI-XM-LIBRARY-INITIALIZED
Call to (METHOD CAPI-LIBRARY:INITIALIZE-CAPI-USING-LOOK-AND-FEEL ((EQL :MOTIF)))
Call to CAPI-INTERNALS:ENSURE-CAPI-INITIALIZED
Call to (METHOD CAPI::CONVERT-OBJECT-TO-SCREEN (CONS))
Call to CAPI-MOTIF-LIBRARY::RUN-INITIAL-FUNCTIONS
Call to (SUBFUNCTION MP::PROCESS-SG-FUNCTION MP::INITIALIZE-PROCESS-STACK)

CL-USER 2 : 1 >        

```

---

### Post by Alberio on 2008-01-28
bump?

---

### Post by msch on 2008-03-30
Do you have lesstif2 installed?

sudo apt-get install lesstif2

---

