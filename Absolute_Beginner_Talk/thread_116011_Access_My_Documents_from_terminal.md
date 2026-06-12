---
title: "Access My Documents from terminal"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by drumlight7 on 2006-01-11
I'm having problems accessing some windows folders with spaces in their names from the terminal, such as My Documents. Is there a character in need to substitue for the spaces. Had trouble narrownig anything I serached for down enough so I hope it's a quick answer for someone. Thanks

---

### Post by Sef on 2006-01-11
Have you tried renaming the folders by adding an underscore? E.G.,  My Documents to My_Documents

---

### Post by Sef on 2006-01-11
Duplicate :oops:

---

### Post by kaamos on 2006-01-11
try
```
cd "My Documents"
```
or
```
cd My\ Documents
```

---

### Post by drumlight7 on 2006-01-11
I've tried the under score but it still says no such file exists. Without the underscore it only includes the first part of the file name eg /media/windows/My *Documents*. Just had a guess(edit and then seen kaamos post)  and put the whole thing in quotes and that works, thanks for the reply

---

### Post by TheCyrus on 2006-01-11
wouldn't it be under /media/windows/Documents and Settings/USER/My Documents?

---

### Post by jerrykenny on 2006-01-11
Sef's solution will allow you to put shortcuts to the folders on your desktop.

Without the underbars, your desktop shortcuts will be baffles by the direction to open two locations, ie   "My", and "Documents" . . . 

So its good long term solution.

---

### Post by Chipmunk on 2006-01-11
I have had some success changing directories by using double quotes,  as in the following: ```
cd "/media/windows/Documents and Settings/username/My Documents"
```

---

### Post by flight_master on 2006-01-11
You know,

there is this oft-forgoten function in bash terminals ;)

say, you type cd /media/windows/Do... hit the TAB key (it'll auto-complete)/username/My(hit tab key - if there are multiple files, it'll add the space char, then add the next letter (D) and hit tab again).

It'll change to:
cd /media/windows/Documents and Settings/username/My Documents/ for you, with proper encoding ;)

-Christian

---

