---
title: "[SOLVED] How do you &amp;quot;CD&amp;quot; to a two name directory?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2008-03-08
How do I cd to a two name directory in linux? A directory with a double word name with a space between words won't work. At least I don't know how to do it.

---

### Post by Madman6510 on 2008-03-08
Put parentheses around the directory name.

---

### Post by prshah on 2008-03-08
eg... "My Documents" in linux

cd My\ Documents\ (Note the slash before the space)

Cheers,
PRShah

---

### Post by odiseo77 on 2008-03-08
Or you can also type the first letters of the directory and then press the tab key for autocompletion.

---

### Post by PinkFloyd102489 on 2008-03-08
Same goes for if you have dashes in between the words, for example "This - is - mine" would be "This\ -\ is\ -\ mine/"

---

### Post by corney91 on 2008-03-08
Yes, a \ is an escape key, so if you want to use something as a character instead of, in this example, a seperator (the space), you'd precede it with \

---

### Post by linuxjerk on 2008-03-08
Amazing the small details you take for granted in windows until you move to linux!

---

### Post by Technophobia on 2008-03-08
windows has the same problem when working with batch script files.

---

