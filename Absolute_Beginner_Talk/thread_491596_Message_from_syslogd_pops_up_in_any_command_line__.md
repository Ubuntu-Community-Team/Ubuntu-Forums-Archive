---
title: "Message from syslogd pops up in any command line  terminal"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by nirvana_mj on 2007-07-03
Hello everybody):P  

When I open  any command line   terminal the message starts popping up continuously with a beep such as this:

Message from syslogd@asus at Tue Jul  3 18:03:01 2007 ...
asus kernel: [26536.295326] EDAC MC0: UE page 0x23b8, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

Message from syslogd@asus at Tue Jul  3 18:03:02 2007 ...
asus kernel: [26537.293768] EDAC MC0: UE page 0x23b8, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

Message from syslogd@asus at Tue Jul  3 18:03:04 2007 ...
asus kernel: [26539.290656] EDAC MC0: UE page 0x23f7, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

Message from syslogd@asus at Tue Jul  3 18:03:05 2007 ...
asus kernel: [26540.289101] EDAC MC0: UE page 0x23b8, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

Message from syslogd@asus at Tue Jul  3 18:03:06 2007 ...
asus kernel: [26541.287547] EDAC MC0: UE page 0x23f7, offset 0x0, grain 4096, row 0, labels ":": i82875p UE

Message from syslogd@asus at Tue Jul  3 18:03:08 2007 ...
asus kernel: [26543.284434] EDAC MC0: UE page 0x23b8, offset 0x0, grain 4096, row 0, labels ":": i82875p UE


any help or ideas appreciated.

nirvana_mj

---

### Post by greg_g on 2007-07-04
Well, I don't know about what it means, but a good first place to start is:
Is anything not working correctly?  It doesn't say "error" or some other "bad word" so first thought it to not worry too much about it.

Of course it would be nice to figure out what is going on.

I just did some googling and it looks like if you search for offset 0x0, grain 4096, row 0, labels ":" you get some people talking about it.
[http://forums.fedoraforum.org/showthread.php?t=100580](http://forums.fedoraforum.org/showthread.php?t=100580)

Here is a bug in launchpad about it:
[https://bugs.launchpad.net/ubuntu/+bug/113793](https://bugs.launchpad.net/ubuntu/+bug/113793)

Some background on the thing giving the error:
[http://kbase.redhat.com/faq/FAQ_85_7898.shtm](http://kbase.redhat.com/faq/FAQ_85_7898.shtm)

So, it looks like it could be memory.  I would boot using a the livecd and do a memory test (memtest86 I believe it is called).

Good luck,

greg

---

