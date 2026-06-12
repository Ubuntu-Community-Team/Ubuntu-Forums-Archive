---
title: "Join multipart zip files"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by bohboh on 2006-06-23
How do you join zip files that have been split up?

---

### Post by x64Jimbo on 2006-06-23
well, assuming that the splitter didn't do some proprietary mumbo-jumbo, you should be able to just cat them all together.
$cat file1 > joinedfile
$cat file2 >>joinedfile
$cat file3 >>joinedfile
etc

---

### Post by FredB on 2006-06-24
Or simply cat file1 file2 file3 > joined file.

I does so when I grabbed Solaris DVD ISO in order to test it in Qemu.

---

### Post by tanari on 2006-09-07
Is it possible to create Nautilus Script for this action?

---

