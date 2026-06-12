---
title: "How to copy folders remotely"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by moose4204l on 2007-10-15
I want to copy a folder remotely from a remote machine to my local machine. I know how to do a file remotely but i dont know how to do a folder.


```
scp <name>@<server>:/<folder paths>lab5 /<folder path on local computer to copy to>
```
i want the whole lab5 folder what do i append to it if i want the whole folder?

hope thats clear.

thanks 
moose

---

### Post by milton1 on 2007-10-15
scp -r

recursively copies the entire folder and contents

---

### Post by moose4204l on 2007-10-15
ok thank i did that and it worked. Just out of curiosity, i got these other things that werent visible that got copied like entries and format all-wcprops.

what is that?

---

