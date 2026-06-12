---
title: "How to use the terminal"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by DaveGiant on 2008-02-03
I have a .bin file on my desktop called PlaneShift.bin.

I have looked into how to install .bin files but no matter what I try 'File not found' comes up.

How can I navigate to this file which is on my desktop using the terminal?

---

### Post by appleimac on 2008-02-03
Go to the terminal and type 

```
cd /home/yourusername/Desktop
```

---

### Post by perlluver on 2008-02-03
Yes you can, check out the links in my signature.  The command to navigate to the file is ```
cd /home/username/folder
```.

---

### Post by Moop on 2008-02-03
cd Desktop in terminal will take you to the desktop. Linux is case sensitive so Desktop and desktop are different.

---

### Post by kellemes on 2008-02-03
> **DaveGiant said:**
> I have a .bin file on my desktop called PlaneShift.bin.

I have looked into how to install .bin files but no matter what I try 'File not found' comes up.

How can I navigate to this file which is on my desktop using the terminal?


Start the terminal.
type the following:
```

cd ~/Desktop
chmod +x PlaneShift.bin
./PlaneShift.bin

```

---

### Post by DaveGiant on 2008-02-03
Thanks guys, I now have a new question. It doesn't say 'No such file or directory'

I type in this command 

chmod +x PlaneShift.bin

And nothing happens. Is this not the install command?

---

### Post by DaveGiant on 2008-02-03
Answered while posting, thanks a lot guys

---

### Post by tangibleorange on 2008-02-03
No. What that does is give the shell (called BASH) permission to execute that file. The command to execute the file is:

> ./PlaneShift.bin

---

### Post by DaveGiant on 2008-02-03
None of the directories are writable.

I have added a  a+x to the command to see if it makes a difference but it doesn't. I have the only account, why can I not write to anything?

---

### Post by kellemes on 2008-02-03
> **DaveGiant said:**
> None of the directories are writable.

I have added a  a+x to the command to see if it makes a difference but it doesn't. I have the only account, why can I not write to anything?


Sorry, didn't think about it.. you need root-permissions

```
sudo ./PlaneShift.bin
```
enter **your** password when asked.

---

