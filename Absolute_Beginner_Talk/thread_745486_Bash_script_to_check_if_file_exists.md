---
title: "Bash script to check if file exists"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by DBrocks on 2008-04-04
Hey guys. I have a question: I am writing a script, and I need it to check if a file exists before continuing, and if that file doesn't exist, then it exits. What is the code for that? Thanks in advance!

~Dan

---

### Post by olejorgen on 2008-04-04
if [ ! -e "filename" ]; then
 # print error message
 return # or exit
fi

---

### Post by sisco311 on 2008-04-04
```
if [ -f /path/to/testfile ] 
then 
  echo testfile exists! 
else
  exit 1
fi
```

---

### Post by DBrocks on 2008-04-04
Does the code need to be indented? or is that just to be more organized?

---

### Post by sisco311 on 2008-04-04
> **DBrocks said:**
> Does the code need to be indented? or is that just to be more organized?
no, but is very useful

---

