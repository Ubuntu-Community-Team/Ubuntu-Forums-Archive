---
title: "Removing an installed module"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by identitet5000 on 2006-12-26
ahoy mateys..

well, I've just compiled & installed a module with the commands 'make' and 'make install', both of which run smoothly. however, I've reached the conclusion that I'd like to remove this module, and the command 'make uninstall' won't work. 

any ideas on how to go about this?

---

### Post by po0f on 2006-12-26
identitet5000,

Do you still have the source tarball available?  Just look for the 'install' rule in the Makefile and reverse the process.  ;)

---

