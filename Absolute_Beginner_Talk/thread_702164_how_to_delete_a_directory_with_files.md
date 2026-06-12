---
title: "how to delete a directory with files?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by internetishere on 2008-02-20
so i know how to delete a directory im the computer administrator but it just wont let me delete files it says access denied is there anyway to bypass this
also one file i was able to move to my trash but now how to i remove that file from my trash?

---

### Post by mkoehler on 2008-02-20
Edit: Can you copy and paste the contents of your terminal window so we can see what you are talking about?

```
sudo rm -r <folder>
```

---

### Post by kpkeerthi on 2008-02-20
rm -rf /folder-name

r - Delete the contents recursively
f - Force delete

** Be extra careful with that command **

---

### Post by ruy_lopez on 2008-02-20
Or you can use alt-F2, type "gksudo nautilus" and delete the file, using the file-browser that pops up.

To delete the file in the Trash

```
cd .Trash
rm -rf file
```

---

### Post by mkoehler on 2008-02-20
True, for those of us that like a nice GUI.  Also, there isn't any reason to use gksudo here, sudo is satisfactory.

---

### Post by ruy_lopez on 2008-02-20
> **mkoehler said:**
> True, for those of us that like a nice GUI.  Also, there isn't any reason to use gksudo here, sudo is satisfactory.

There is, if you use alt-F2 it produces a one-line field. If you type 'sudo nautilus' there's no way to enter your password. With 'gksudo' a pop up asks for your password.

---

### Post by internetishere on 2008-02-20
thankyou

---

### Post by mkoehler on 2008-02-20
Ah, I stand corrected - I have never used the ALT-F2 command before - I'm more of a terminal guy myself.

---

### Post by ruy_lopez on 2008-02-20
> **mkoehler said:**
> I'm more of a terminal guy myself.

ditto

---

