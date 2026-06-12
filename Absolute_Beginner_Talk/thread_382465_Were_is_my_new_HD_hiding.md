---
title: "Were is my new HD hiding??"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by chillieman on 2007-03-12
i'm real new at unbuntu. i tried it a few months back but got too many headaches. i loaded 6.10 back on again yesturday with no problems. i partitioned my Hd - windows on one half with Ubuntu on the other. when looking at the desktop it show the widows partition - hda1 or something like that but when i connected up a second HD (which has all my stored data on - window was to unreliable) i can't see it any where on the desktop. if i plug in my portable HD, it shows up. what's going on??

---

### Post by Najand on 2007-03-12
What is your second HD? A usb External HD? SCSI HD? IDE HD?SATA HD? And how did you connect it to your computer?

---

### Post by hyper_ch on 2007-03-12
Well, USB uses hotplug which you can un/plug while you are running...

However attaching the hd to IDE or SATA is something different...

In order to see whether the hd is there you can use multiple approaches

(1) Command line:
```

sudo fdsik -l

```
This will list all the partitions recognized...

(2) GUI:
Use GParted for checking whether it recognizes the harddisk...

Once you know it's there then you can mount it :)

Best is to post the output of *sudo fdisk -l*
Then we can help you on mounting it :)

---

### Post by chillieman on 2007-03-12
Good Question Najand. it's the sort of HD that connects to the end of the ribbin after the mater HD. it's convigured as a slave. it's not SATA. it's just a normal type HD called Maxtor or something like that.

---

### Post by chillieman on 2007-03-12
thank you. i'll try that to see what happens.

---

### Post by hyper_ch on 2007-03-12
If it's not plugged in by USB and it's not sata then it's IDE :)

---

### Post by Najand on 2007-03-12
If it is IDE, then asb others has already said posting the output of
```

sudo fdsik -l

```
will enable us to help  you.

---

