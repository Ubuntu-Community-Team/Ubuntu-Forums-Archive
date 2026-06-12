---
title: "[SOLVED] drivers"
date: 2008-02-25
forum: BSD
---

### Post by chris200x9 on 2008-02-25
I know that in linux there is a program so you can use windows drivers uder linux, but is there any program to use windows drivers with the *BSD's?

---

### Post by mips on 2008-02-26
Yes, you can use package [ndis(4)]("http://www.freebsd.org/cgi/man.cgi?query=ndis&sektion=4") or better know as NDISulator.

As fas as I know you can also build [NDISwrapper]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/") on BSD

NDISulator is not available on OpenBSD as they do not support binary blobs of any form.

I would also advise you to first check if your card does not have native bsd support.

---

