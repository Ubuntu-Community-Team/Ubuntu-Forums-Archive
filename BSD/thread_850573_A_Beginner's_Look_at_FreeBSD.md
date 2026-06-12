---
title: "A Beginner's Look at FreeBSD"
date: 2008-07-05
forum: BSD
---

### Post by ghindo on 2008-07-05
Hello all,
I recently started maintaining a personal server for torrents and storage, using Ubuntu 8.04 Server Edition as my OS.  Recently, I've stumbled across [FreeNAS]("http://www.freenas.org/") and it seemed like an interesting alternative to what I'm using now, and a chance to mess around with BSD.

However, I have absolutely no experience with BSD and don't really know where to start looking.  Does anybody have any good resources they can point me to to start learning BSD?  

[SIZE="1"]Also, stupid question, but BSD uses Bash, right?  So some of the knowledge I gained from Linux is still applicable in BSD?[/SIZE]

---

### Post by cardinals_fan on 2008-07-05
Read the [FreeBSD Handbook]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/index.html").  And most BSDs don't use BASH **by default**, but it's very easy to install/setup.

You could also consider [NetBSD]("http://www.netbsd.org/").

---

### Post by ghindo on 2008-07-12
Interesting.  What do most BSDs use, if not Bash?

---

### Post by cardinals_fan on 2008-07-12
> **ghindo said:**
> Interesting.  What do most BSDs use, if not Bash?
Csh or sh.

---

### Post by Bachstelze on 2008-07-12
> **cardinals_fan said:**
> Csh or sh.

OpenBSD uses a modified ksh, FreeBSD uses a modified ash. Not sure about NetBSD.

Keep in mind, though, that the shell is just the shell, which means that installing Bash on your BSD won't make that much difference regarding how useful your Linux experience will be, there is much, much more difference than that.

---

### Post by cardinals_fan on 2008-07-12
> **HymnToLife said:**
> OpenBSD uses a modified ksh, FreeBSD uses a modified ash. Not sure about NetBSD.

Keep in mind, though, that the shell is just the shell, which means that installing Bash on your BSD won't make that much difference regarding how useful your Linux experience will be, there is much, much more difference than that.
NetBSD is what I was referring to.

---

### Post by angryfirelord on 2008-07-28
To start, the FreeBSD handbook is the first place to go. One advantage of running a BSD system is that the documentation is better written compared to some of the manpages on Linux. One you glance over that, here's an article comparing the general Linux structure to the BSD structure: [http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php]("http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php")

If you desire further reading, I recommend Absolute FreeBSD, 2nd Edition: [http://www.amazon.com/Absolute-FreeBSD-Complete-Guide-2nd/dp/1593271514/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1217303370&sr=8-1]("http://www.amazon.com/Absolute-FreeBSD-Complete-Guide-2nd/dp/1593271514/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1217303370&sr=8-1") It's a well written book and it's not very dry compared to some of the other Linux & FreeBSD books I've glanced at.

& of course, if you have further questions, post them here. :)

---

