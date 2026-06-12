---
title: "Acessing folders with spaces in the name with the command line"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by aswells on 2006-11-20
Is there a way to access folders with spaces in the name through the command line?

Thanks
aswells

---

### Post by MicroChris on 2006-11-20
Yeah just make the space, heh.

If you're doing it from a browser and not a terminal try %20 as the space.

-Chris

---

### Post by David_T on 2006-11-21
All you need to do is escape the space with a backslash.

So, if you had a folder called ``space folder'', you would cd into it by typing ``cd space\ folder''.

---

### Post by macogw on 2006-11-21
You can also put quotes around it:
cd "that folder"

---

### Post by bodhi.zazen on 2006-11-21
Or use tab completion.

type:

cd tha<tab> and you will get

cd that\ folder

Or type

cd spca<tab> and you will get

cd space\ folder

---

### Post by adamkane on 2006-11-21
I imagine there is also an escape sequence for tabs, newlines, etc.

---

### Post by aswells on 2006-11-21
Thanks for the help everyone!

---

### Post by jd65pl on 2006-11-21
Use double quotes when a variable is required                   --> "$folder name"
Use single quotes when the string should be taken literally --> 'foldername'
Use the escape character to include a single character        --> folder\ name

---

