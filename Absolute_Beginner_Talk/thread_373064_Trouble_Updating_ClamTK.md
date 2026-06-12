---
title: "Trouble Updating ClamTK"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by ZeroXR on 2007-02-28
I installed ClamTK and when I tried to use the update command within the application, it brings me an error box saying I need to be Root to use the update. Naturally, I go into Terminal and use the command: sudo freshclam and here's the output I get from that -

```
ClamAV update process started at Wed Feb 28 20:48:21 2007
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.88.4 Recommended version: 0.90
DON'T PANIC! Read http://www.clamav.net/faq.html
main.cvd is up to date (version: 42, sigs: 83951, f-level: 10, builder: tkojm)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 8, recommended = 10
DON'T PANIC! Read http://www.clamav.net/faq.html
Downloading daily.cvd [*]
daily.cvd updated (version: 2682, sigs: 11511, f-level: 13, builder: ccordes)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 8, recommended = 13
DON'T PANIC! Read http://www.clamav.net/faq.html
Database updated (95462 signatures) from db.local.clamav.net (IP: 72.21.63.182)
ERROR: Clamd was NOT notified: Can't connect to clamd through /var/run/clamav/clamd.ctl
connect(): No such file or directory
```

Can someone help me out?

---

### Post by go2dell on 2007-03-01
First off, as the messages say:
> **DON'T PANIC!** Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html)

Your definition files are up to date.
> 
main.cvd is up to date (version: 42, sigs: 83951, f-level: 10, builder: tkojm)
...
daily.cvd updated (version: 2682, sigs: 11511, f-level: 13, builder: ccordes)
...
Database updated (95462 signatures) from db.local.clamav.net (IP: 72.21.63.182)


You're getting the evil messages because the developers expect you to be running more up-to-date software than you're running.  Since you installed (presumably) from the Ubuntu repositories, you can expect this to happen from time to time.

You can read the wiki page on ClamAV installation [here]("https://help.ubuntu.com/community/ClamAV").

There's also a [page]("https://help.ubuntu.com/community/ClamAVUpdates") detailing how to update ClamAV if you don't want to get the messages anymore, but you'll be on your own if it breaks something.

---

### Post by ZeroXR on 2007-03-02
My thanks for clearing that up. I saw the "Don't panic" message, but I think the "WARNING: Your ClamAV Installation is OUTDATED!" stuck out more... so I had a bit of a panic moment.

---

