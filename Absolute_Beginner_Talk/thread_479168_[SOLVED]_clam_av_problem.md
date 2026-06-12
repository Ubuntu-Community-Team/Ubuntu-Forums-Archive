---
title: "[SOLVED] clam av problem"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by mike g on 2007-06-20
Problem with clamav and clamtk.

Which file should clamav be in?  Clamtk says it is unable to scan because the program is, _"unable to view clamav information file."_.  It loads in /etc/clamav.  Is that correct and if not where do i put it and how do I move it there?  Any other suggestions to make Clam work?

Sure feeling stupid with all these questions.

Mike

---

### Post by wormser on 2007-06-20
I use avscan as a front end to ClamAV.  It is a decent gui.

```
sudo apt-get install avscan
```

---

### Post by gatdammit on 2007-06-21
I found this just now... it seemed to work

[http://ubuntuforums.org/showthread.php?t=407356&highlight=unable+to+view+clamav%27s+information](http://ubuntuforums.org/showthread.php?t=407356&highlight=unable+to+view+clamav%27s+information)

---

### Post by mike g on 2007-06-22
Thank you all.  I obtained a patch from clamtk.  For those who have this problem, it will go away in the 2.32 version of clamtk.  Attached is information given to me and it seemed to work.

wget clamtk.sf.net/clamtk-2.32.gz
gzip -d clamtk-2.32.gz
chmod +x clamtk-2.32
sudo mv clamtk-2.32 /usr/bin/clamtk
(y to overwrite)

I hope this helps someone else.

Thank you Dave.

Mike g.

---

### Post by mahasmb on 2007-06-26
> **wormser said:**
> I use avscan as a front end to ClamAV.  It is a decent gui.

```
sudo apt-get install avscan
```

That worked for me. Thanks!

Quick question though: How would I add this to my "Applications" menu? Or any of the other menus for that matter.

---

