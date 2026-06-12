---
title: "Installing .SH file?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Rylin on 2007-08-26
What is the normal way to install an .sh file from my home folder?

Ive done this before just forgot how to do it again. :(

much appreciated.

---

### Post by mikaelsnavy on 2007-08-26
./file.sh to execute it in the terminal. You may need to right-click, go to properties and then the permissions tab and check the box saying " Allow executing file as a program".

---

### Post by Rylin on 2007-08-26
Ah that worked. Thanks :)

---

### Post by khughitt on 2007-08-26
In general to install using a script you do make it execute and then run it with super-user privileges:

```
chmod +x script.sh
sudo ./script.sh
```

If you want to install it to your *home* directory instead of it's default install location I
think it depends on the script. You may be able to find out by simply opening the script
with a text editor and reading any comments inside, or by checking the documentation from
the site you found it at.

---

### Post by mikaelsnavy on 2007-08-26
Yup, you might need to do sudo ./file.sh

---

