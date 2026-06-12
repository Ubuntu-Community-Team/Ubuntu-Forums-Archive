---
title: "BIND migration"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by drhiii on 2008-01-25
Hopefully not too bonehead of a question...   I reinstalled to Ubuntu 7.10 after having saved among other things   /etc/bind   and all its files.

I copied them back into place on the new build, made sure the permissions and ownership matched the default files, but they do not show up in Webmin when I go to the BIND admin panel.

Can anyone point me to where/how to re-add these records to a freshly built machine?  Obviously copying them into place as I did is not the correct procedure.

tx

---

### Post by david_kt on 2008-01-26
May be you could try to install bind first and make sure it appear in the webmin. After that, copy the old file back and restart bind.

DK

---

### Post by drhiii on 2008-01-26
Hello and tx for the response.  BIND was/is already installed and was readable by Webmin.  That is when I coped a record into /etc/bind, but it did not appear, this after deleting my browser cache, refreshing, and doing what I knew to make sure I was not reading old data.  No go...



> **david_kt said:**
> May be you could try to install bind first and make sure it appear in the webmin. After that, copy the old file back and restart bind.

DK

---

