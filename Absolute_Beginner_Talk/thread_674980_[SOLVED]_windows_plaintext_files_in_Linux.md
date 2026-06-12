---
title: "[SOLVED] windows plaintext files in Linux"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by sagarhshah on 2008-01-22
Windows files in linux

I am uploading a few plaintext files from my university windows account onto my univerity linux box.
The problem is they won't show properly on the linux box when I look at them in vi

Is there anything I can do to make sure the files show properly?

I can't install anything on the linux box as I do not have admin rights
I can install stuff on the windows box as one of the admins has kindly given me admin rights for the windows box.Tried asking for linux admin rights but he doesnt want me messing with it.

any help would be appreciated.

thanks
sagar

---

### Post by p_quarles on 2008-01-22
Get Notepad++ for Windows. It can save text files using the UNIX text formatting standards.

---

### Post by emarkd on 2008-01-22
The issue is that Windows uses a different line ending character than unix.  Some systems have dos2unix installed.  This easily converts those endings.  If you can't get any helper software installed, you can always use awk to replace the characters.  Something like this should work:

awk '{ sub("\r$", ""); print }' winfile.txt > unixfile.txt

---

### Post by sagarhshah on 2008-01-22
that worked :)

many thanks

Sagar

---

### Post by emarkd on 2008-01-22
Glad you got it working.  Could you mark this thread as solved so that others with the same problem can find it easier.  At the top of the thread, click on "Thread Tools" and select "Mark as Solved"

Thanks

---

### Post by sagarhshah on 2008-01-22
Marked as solved.

Notepad++ worked.

I have not tried the awk method of replacing the line characters as yet, but will probabaly have to at some point.

Sagar

---

