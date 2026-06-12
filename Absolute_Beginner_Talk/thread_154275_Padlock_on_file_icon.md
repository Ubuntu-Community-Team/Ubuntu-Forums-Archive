---
title: "Padlock on file icon"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2006-04-02
When I copy a file from another drive the icon of the file shows a little padlock on the top right.
The file seems to function properly etc - but what does the padlock mean ?

---

### Post by Sutekh on 2006-04-02
This means the the file has restricted permissions.  You may not be able to read/write or execute it.  It may also mean that you are not the 'owner' of the file, someone else (ie root) is.

You can determine the permissions by right-clicking the file and choosing Properties and the Permissions tab.  If you are the owner of the file you can change them.

You can also determine the permissions and ownership using the command
```
ls -l /<path of file>/<name of file>
```

For a *really *good explanation of permissions and ownership, check out the link 'How do I use the Terminal' in my signature

---

### Post by cliff0108 on 2006-04-02
That is exactly what I wanted to know.
Thank you.

---

