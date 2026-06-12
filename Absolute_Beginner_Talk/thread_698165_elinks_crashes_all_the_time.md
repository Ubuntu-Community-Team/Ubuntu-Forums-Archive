---
title: "elinks crashes all the time"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by OldNewb on 2008-02-16
I was running elinks earlier in the day and then when I tried it later it crashed.
I have uninstalled and reinstalled with no improvement.

---

### Post by randy78 on 2008-02-16
> **OldNewb said:**
> I was running elinks earlier in the day and then when I tried it later it crashed.
I have uninstalled and reinstalled with no improvement.

Un-installs and re-installs are of the Windows mindset ;)

Post the output of the error message after it crashes :D

---

### Post by OldNewb on 2008-02-16
I can't copy the text in the terminal after I run the program, I'm copying this the best that I can

elinks(dump_backtrace+0x1c)[0x80cf61c]
elinks[0x80acd6d]
elinks[0x80acc98]
[0xffffe420]
elinks(load_uri+0xf5)[0x80a8ad5]
elinks[0x80c5b68]
elinks[0x80c6125]
elinks[0x80c62fe]
elinks(goto_uri+0x2a)[0x80c646a]
elinks(goto_url_with_hook+0x4c)[0x80c64bc]
elinks[0x8060871]
elinks[0x805d200]
elinks(in_term+0x44b)[0x80c83fb]
elinks(select_loop+0x1fb)[0x80a4edb]
elinks(main+0x4a)[0x80a45ca]
/lib/tls/i686/cmov/lib.so.6(__libc_start_main+0xdc)[0xb7c3aebc]
elinks[0x805bfcl]
Aborted (core dumped)

hope that means something to someone

---

### Post by OldNewb on 2008-02-16
I just rebooted and now it is working?!

---

