---
title: "Help running scripts"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by akshaysrinivasan on 2006-11-24
Hi,
  I just reinstalled Ubuntu ,i was having edubuntu before.I found that to run scripts i have to type :
$bash ./script
Is it possible to execute them by just typing
$./script

Whenever i type only the script name
$./script
bash ./script Permission Denied

I verified that the script was executable.

Thanks

---

### Post by 23meg on 2006-11-24
Are you sure you have read access to the file and the folder it's in?

---

### Post by akshaysrinivasan on 2006-11-24
Sure i do ,it is in my home folder

---

### Post by akshaysrinivasan on 2006-11-24
It used to work in edubuntu

---

### Post by kenweill on 2006-11-24
Run:
sudo ./your-script.sh
or
sudo /bin/bash ./your-script.sh

---

### Post by tocleora on 2006-11-24
The first line needs to have a call to your bash if I remember correctly.  If you were creating a script that ran ls for example, you would do this:

#!/bin/bash
ls -al

For the record though, I have a few bash scripts I don't have that first line in that I don't have to type bash first to run.  Remember there are three options in chmod, Owner, Group and Anybody (Other).  Make sure the right one is executable.  If it's in a folder you have write access to, then owner can be, but if it's in a folder that you don't normally have write access to, group (if you're in the group) or Anybody will need to be.  I believe just doing chmod +x filename will do the trick, but here's additional information on chmod if you need it:

[http://www.computerhope.com/unix/uchmod.htm]("http://www.computerhope.com/unix/uchmod.htm")

---

### Post by akshaysrinivasan on 2006-11-24
Figured it ,it was none of them actually.I had mounted my home filesystem without the exec tag.Thank you anyway

---

