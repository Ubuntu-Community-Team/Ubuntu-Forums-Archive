---
title: "Thunderbird upgrade seems to have used old mail file."
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2006-06-21
I upgraded Thunderbird (through apt-get) to 1.5.x.4. According to the HELP..ABOUT info it was already 1.5.x.4 before upgrading, but during upgrade it appeared to say it was changing from 1.5.x.2 to 1.5.x.4.

Anyway, now it appears to have "backdated" the mail file (mail received) by about 10 days, so everything I've received over the last 10 days has mysteriously disappeared. The last mail received before the upgrade appears now to have been on the 10th....although I received mail yesterday and today....and every other day for the last 10.

I'm guessing it's moved an old file into the place of the "current file", and that the "current file" is in a directory somewhere.

Can anybody tell me a few places to look for that lost file and where I should move it to to make it the current file again?

---

### Post by mdsmedia on 2006-07-04
Funny I got no reply to this one, because I eventually found both files while looking for something else.

In my /home directory there is a /.thunderbird and a /.mozilla-thunderbird.  /.mozilla-thunderbird is the current directory used by thunderbird. It must have also been the directory formerly used in an earlier version. Hope this helps someone.

---

