---
title: "[SOLVED] revert back to thunderbird 1.5"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-09-29
Hey, I have thunderbird2 but it freezes up on me. and when I tried to remove it... it would not remove.
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-2.png[/IMG]
So... how can I get thunderbird 1.5?? Yes, I have tried "Add/Remove" to get thunderbird 1.5, but I cannot find it after it installed it... I do not have thunderbird in my repositories...

Some help please?

SV

---

### Post by por100pre1 on 2007-09-29
Not sure if you have the same issue I had, this worked for me.

If you did not remove Tb 1.5:

```
cd /usr/bin
```

```
sudo mv mozilla-thunderbird mozilla-thunderbird.old
```

```
sudo mv mozilla-thunderbird.ubuntu mozilla-thunderbird
```

Then run Thunderbird 1.5:

```
mozilla-thunderbird
```

---

### Post by staticvoid on 2007-09-29
Hey thanks :) That was exactly my problem, just a little different...
I went back to the site I installed it from and realized I installed it into /opt  so I just went there and removed the direcotry. Then I just added a launcher to my menus for "mozilla-thunderbird"...

Thank you!

sv

---

### Post by por100pre1 on 2007-09-29
Glad to know you solved it. :)

---

### Post by staticvoid on 2007-10-01
Yeah :) To bad about the thunderbird2 bug though, it was no "one-step" process to setting up my gmail account :(

Static Void

---

