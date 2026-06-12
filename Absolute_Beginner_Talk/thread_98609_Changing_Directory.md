---
title: "Changing Directory"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2005-12-03
Let's say I have a directory entitled **My Folder**.  When I change directories in the terminal, how would I take care of that space?  I have tried:

```
cd My Folder
```
```
cd My_Folder
```
```
cd My%20Folder
```

But none worked.  Do I simply have to rename the directory or is there a way around it?

Thank you.

---

### Post by IdolizingStewie on 2005-12-03
When there is a space (or any other special character) in a file or directory name in linux you have to escape the special character. This is done by typing a backslash in front of the character like this.
```
cd My\ Folder
```
For spaces you can also use double-quotes around the name like this.
```
cd "My Folder"
```

---

### Post by Terry of Astoria on 2005-12-03
beautiful. Don't forget you can type the first few letters, hit <tab> and (bash?) linux will guess at the rest of a filename usually, or at least part of it.

---

