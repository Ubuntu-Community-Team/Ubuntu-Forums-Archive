---
title: "In boot up Setting up resolvconf failed"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2007-02-03
When I booted up today the error in the scrolling start up said:
"Setting up resolvconf...........failed"
the boot up continued and ended with the command line instead of starting X.[LIST]
[*]So, after loging in I tried ```
startx
``` it screen change to a finely checkered black and white blank.[/LIST][LIST]
[*]After searching the forums I found a similar problem that was evidently overcome by ```
aptitude remove resolvconf
``` which I did but for me it did not work[/LIST]Now I am stuck and need your help..........puleeze

---

### Post by kindafunnylookin on 2007-02-03
bump

---

### Post by confused57 on 2007-02-03
I don't know how to solve your problem, but did you install anything before the error message at boot...possibly could have been a bug with updates.
I found my resolvconf in  /etc/resolvconf/update-libc.d/postfix

postfix was a script:

#!/bin/sh -e

# make sure we're still here...
[ -x /usr/sbin/postconf ] || exit 0

cp /etc/resolv.conf $(/usr/sbin/postconf -h queue_directory)/etc/resolv.conf
/etc/init.d/postfix reload >/dev/null 2>&1

exit 0

update-libc.d was the only directory in resolvconf & postfix was the only file(script) in update-libc.d on my system

Maybe this info will help you do a google search for a possible solution...good luck.

---

### Post by kindafunnylookin on 2007-02-03
Confused57,
Thanks for those ideas but I have already brgun the process of installing Edgy. I have been waiting for a good chance to do this.
Peter

---

