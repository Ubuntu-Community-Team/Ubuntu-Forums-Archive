---
title: "Possible to pipe standard output &amp; error to a file while displaying them on monitor?"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-11-24
Would it be possible to display the results of 'cat testfile' on the monitor while piping the standard output and error to a file? I tried 'cat testfile &> capturedfile', but the content of 'testfile' is not displayed on the monitor (the content is however piped successfully into the capturedfile). 

Also, does the tee command capture error output in the file (capturedfile) too? Eg.

'cat testfile |tee capturedfile' 

Thanks !

---

### Post by [Rui] on 2005-11-24
cat testfile 2>&1 | tee capturedfile

---

