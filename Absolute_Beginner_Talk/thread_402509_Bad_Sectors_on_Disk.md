---
title: "Bad Sectors on Disk"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by rabble123 on 2007-04-05
Hi

When I try and resize my disk I get an error telling me there are bad sectors on the disk. I have run chkdsk /f /r like recommended but it didn't fix these sectors.

What are my options now? Is there another way to solve this problem?

---

### Post by cypherzero on 2007-04-05
Try:
sudo chkdsk /f /r 

If not - format the disk?
If it still doesn't work after that then you know it's a physical problem and you need a new one.

If you are resizing the same disk you are running from this might also be causing the problem since open files can't be moved. Run an from an external disk or CD.

---

