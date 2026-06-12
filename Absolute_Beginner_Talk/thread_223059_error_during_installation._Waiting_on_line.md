---
title: "error during installation. Waiting on line"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by vasurg on 2006-07-25
I got error message "The test of the file system with type fat16 in partition #1 of IDE1 master (hda) found uncorrected errors."
My desktop is a Dell, and the hda1 is a fat16 set by dell for system files, I think.
2 choice are given here:
Go back;
Continue

What should I do??
Thanks

---

### Post by T700 on 2006-07-25
Are you planning to format the partition with errors?  If so, I'd just hit "continue".  If not, boot back to Windows and run Scandisk and see if you can fix it.

Paul

---

### Post by Kurt` on 2006-07-25
Can you just continue past it and tell the partitioner not to use it?

---

### Post by vasurg on 2006-07-25
T700,
I don't want to format that partition for sure. The thing is I used PM to check all the partitions before the installation, it didn't find any error. Thanks for the suggestion, i will go back and do scandisk. What if scandisk doesn't find error and this propblem consist?

---

### Post by Kurt` on 2006-07-25
It may not be an error... I mean, if the partition was put on their by your PC manufacturer, chances are there's nothing wrong.

Maybe Ubuntu is simply guessing at the filesystem present, and it's not REALLY fat16 (I doubt it, but you never know...)? In any case, you should be able to complete the installation, as you wouldn't be using that partition anyways.

---

