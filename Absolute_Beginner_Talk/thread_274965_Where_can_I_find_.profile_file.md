---
title: "Where can I find .profile file?"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by 25an on 2006-10-10
Hi!
I am trying to install Qt one of the things that i have to do is to add some environments variables in .profile but I cant find this .profile file?
There is a profile file in /etc but that one is not hidden?
The only .profile file i could find is in /root. but is that really it?

Thanks for the help.

---

### Post by taurus on 2006-10-10
It should be in your home directory, ~/.profile, and if you don't have one, you can create one with

```
touch ~/.profile
```

---

### Post by 25an on 2006-10-10
What is touch?
Is that just to create a hidden file?

---

### Post by taurus on 2006-10-10
Touch is used to create a file if you don't have it.  You can also create it with any other text editor...

---

### Post by Iowan on 2006-10-10
According to **man touch**, touch is intended to>  Update  the  access and modification times of each FILE to the current time.
but it has the added benefit of creating (an empty) FILE if it doesn't exist.
BTW... it's the "." in ".profile" that makes it hidden.

---

