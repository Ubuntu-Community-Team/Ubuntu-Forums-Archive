---
title: "midnight commander samba mount"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by dgifford on 2008-02-27
trying to mount a share from a windows box

select the pane, select smb link....

the windows share has no passwd

get error:

cannot chdir to /*smb://servername/share

what am i missing?

---

### Post by danpre on 2008-02-27
> **dgifford said:**
> trying to mount a share from a windows box

select the pane, select smb link....

the windows share has no passwd

get error:

cannot chdir to /*smb://servername/share

what am i missing?

Try just:

\\servername\share

DANIeL

---

### Post by dgifford on 2008-02-27
same error, tried by ip as well with no joy.  thanks though

---

### Post by dgifford on 2008-02-27
got  a  mount using //ip  without the directory

---

