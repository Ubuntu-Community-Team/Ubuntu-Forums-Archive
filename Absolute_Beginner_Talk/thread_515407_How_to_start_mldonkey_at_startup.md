---
title: "How to start mldonkey at startup?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by xellzhang on 2007-08-01
I have installed mldonkey from source (compile it) and it is working.

I want to start it at startup. So I created a file caledl mlnet in /etc/init.d of which content is:
[COLOR="Blue"]#! /bin/sh
/usr/local/mldonkey/bin/mlnet &[/COLOR]

Then I set it executable and created a symbol link in /etc/rc2.d called S99mldonkey.

But after I rebooted my system it did not start automatically... I don't know why...

---

### Post by Kingsley on 2007-08-01
System > Preferences > Sessions

Then add /usr/local/mldonkey/bin/mlnet as a startup program.

---

