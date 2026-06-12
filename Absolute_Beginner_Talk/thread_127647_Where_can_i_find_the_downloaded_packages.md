---
title: "Where can i find the downloaded packages?"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by abhishekp on 2006-02-09
Hi, I am pretty new to linux. I recently installed linux and after a successful installation I installed certain software packages through synaptic package manager. Now I want to reformat my HD because there seems to be a problem with my windows.

 Now the problem is I want to backup everything. My question is, Is it possible to find the packages that were downloaded by synaptic or should i download everything again from beginning. I have downloaded almost 500MB. I need help. Thank you in advance.

---

### Post by Kiwinote on 2006-02-09
As far as I know, because windows and linux are on seperate partitions, you should just be able to format/erase that one partition and leave linux in tact.

Kiwinote

---

### Post by abhishekp on 2006-02-09
No i meant i want to resize the partitions. I just wanted to know is it possible to find the downloaded packages or not.

---

### Post by Kiwinote on 2006-02-09
I think it would be easier to reinstall them than try and find all the files and config files.

Kiwinote

---

### Post by carlosqueso on 2006-02-09
If you haven't done an apt-get clean, the downloaded packages live in /var/cache/apt/archives  If you've cleaned them out, you're out of luck.

---

