---
title: "What is the raw device of my printer?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Tallman on 2006-09-02
Hi all,

On my Dapper box I have an Epson Stylus Photo RX425 printer connected. To check the ink level I just installed the escputil package.

In order for escputil package to check the ink level of my printer it needs to write to the raw device of the printer.

How do I find out what the raw device of my printer is? I searched here and there, but I couldn't find out. Any help would be greatly appreciated.

---

### Post by steve.horsley on 2006-09-02
It's probably /dev/lp0 but I don't know how you would go about proving that.

If you can't get escputil to work (I've never tried it), you might want to try **mtink**, which is in the repos and seems to be able to autodetect the printer.

---

### Post by Tallman on 2006-09-03
Thanks for your reply and sorry for getting back so late.

Couldn't get escputil to work (Cannot write to /dev/lp0: Resource temporarily unavailable), but mtink does the job.

Thanks!

---

### Post by steve.horsley on 2006-09-03
sudo escputil might work.

---

