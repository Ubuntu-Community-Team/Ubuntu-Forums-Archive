---
title: "How can I execute a command at startup?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by DecemberWinds on 2008-01-13
Every time I log in I type in compiz --version into terminal to make my title bar of my windows normal size. 

How can I make this execute everytime I start up?

---

### Post by PurposeOfReason on 2008-01-13
System > Preferences > Sessions

---

### Post by DecemberWinds on 2008-01-13
> **PurposeOfReason said:**
> System > Preferences > Sessions

Yes, I know that, but what exactly do I put into the boxes when I press ADD to thes tartup list?

---

### Post by PurposeOfReason on 2008-01-13
The name can be whatever you want. The command will be compiz --version and leave the comments blank unless you want them.

---

### Post by holihue on 2008-01-13
> **DecemberWinds said:**
> Yes, I know that, but what exactly do I put into the boxes when I press ADD to thes tartup list?

yes, and then you get an box with :

Name: (here you can have whatever you want)
Command: (here you insert the command to run, in this case: compiz --version)
Comment: (here you can insert a comment if you want)

---

### Post by jordilin on 2008-01-13
> **DecemberWinds said:**
> Every time I log in I type in compiz --version into terminal to make my title bar of my windows normal size. 

How can I make this execute everytime I start up?

In session options you can press the button Remember currently running applications and check the box to remember them when logging out. Probably that will work
PD. You must obviously run this command and then remember the running apps

---

### Post by KingWilliam on 2008-01-13
thats correct!

---

### Post by DecemberWinds on 2008-01-13
I've done everything you guys have suggesting yet nothing... ><

---

### Post by jd65pl on 2008-01-13
```
sudo nano ~/.profile
```

Add the services you require with a & as a option, the apps will then start when you login

---

### Post by DecemberWinds on 2008-01-13
> **jd65pl said:**
> ```
sudo nano ~/.profile
```

Add the services you require with a & as a option, the apps will then start when you login

Um... sorry but I don't understand what you just said...

Can you tell me step by step?

---

### Post by jd65pl on 2008-01-13
[LIST]
[*]do the following command in a terminal[/LIST]
```
gksudo gedit ~/.profile
```

[LIST]
[*]Add the line[/LIST]
> compiz --version &

[LIST]
[*]To the file
[*]click save
[*]close the file[/LIST]
The application should now work as you wish when you log-in

---

### Post by DecemberWinds on 2008-01-13
> **jd65pl said:**
> [LIST]
[*]do the following command in a terminal[/LIST]
```
gksudo gedit ~/.profile
```

[LIST]
[*]Add the line[/LIST]


[LIST]
[*]To the file
[*]click save
[*]close the file[/LIST]
The application should now work as you wish when you log-in

Um... I just added that line to the very end of the text file, saved, and logged in and out. There is no difference...
Am I added the line wrong?

---

