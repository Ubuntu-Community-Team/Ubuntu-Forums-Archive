---
title: "General steps to troubleshoot random lockups"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by jhenager on 2007-07-07
I am running Ubuntu 7.04, and am experiencing random lockups that require a hard reset. It doesn't seem to have any pattern, and I can't see anything in the logs that would help narrow it down.
I wouldn't have a problem wiping my HD and reloading, but would prefer to avoid it if I can. However, it is causing me enough aggravation that I need to do something about it.
I will be doing any normal task, and the pointer freezes, and game over.
I looked through system log, user log, messages, and don't see anything unusual, except this in the syslog
Jul  7 08:47:48 jeff-desktop kernel: [   46.252261] eth0: no IPv6 routers present
Jul  7 09:07:26 jeff-desktop -- MARK --

sometimes the MARK line repeats itself four times or more.
One other thing is a reference to a bluetooth device in the debug log, and I don't think I have one.
Jul  7 06:35:16 jeff-desktop NetworkManager: <debug info>^I[1183804516.878400] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 

Any suggestions are welcome.

---

### Post by mikeyphi on 2007-07-07
I can only suggest 2 things to consider....
1) Are you sure it's not Beryl?
2) In the bad old days of windoze I had random freezes and discovered it was caused by a faulty memory chip!

---

### Post by greg_g on 2007-07-07
Also, just so you know, the --MARK-- is simply that, a time mark for when there hasn't been anything to report lately but here is a timestamp anyways.

But yeah, if you think it is completley random, I would do a memory test.

---

### Post by jhenager on 2007-07-15
It could be beryl, but it would be nice to have some confidence in which direction to go. I know it is 'unsupported' and experimental software, but I didn't have this issue with Dapper.
Also, if it was a Beryl bug, and I wanted to report it, I would probably be asked for some logs or config files, and that is what I am looking for.
As for memory, it is new. Any suggestions on how to test it? Like Ultimate Boot CD?

---

### Post by Nekiruhs on 2007-07-15
Just run the app from terminal like this
```
beryl 2> ~/errorBERYL
```That will run it and put the output in ~/errorBERYL

---

### Post by tgalati4 on 2007-07-15
You had a working, reliable system with Dapper.

You created a second partition and installed Feisty.

You find that Feisty freezes.

What prevents you from simply booting back into Dapper?

---

