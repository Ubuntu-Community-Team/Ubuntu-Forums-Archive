---
title: "batch file"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by mckay lee on 2008-01-11
hi,

I want to make script like windows batch file, so that user can double click it to run .jar file, any ideas?

thanks

---

### Post by finer recliner on 2008-01-11
if the .jar file is executable, i think you can use this command to run it:

```
 java -jar filename.jar 
```


batch files in windows are called shell scripts in linux. google something like "intro to linux shell scripting" for more info. probably want to choose BASH as your shell language

---

### Post by bodhi.zazen on 2008-01-11
Right click and select "create launcher" from the menu.

In the dialog box, you can change the icon by clicking on it.

You need to enter the jar command manually

---

