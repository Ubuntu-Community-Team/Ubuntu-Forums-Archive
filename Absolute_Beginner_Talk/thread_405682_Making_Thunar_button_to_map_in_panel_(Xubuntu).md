---
title: "Making Thunar button to map in panel (Xubuntu)"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by tommie74 on 2007-04-10
When I type this command: "thunar ~/certain-map-path" in a terminal Thunar opens in the specified map location. But when I tried to add a new item to the Xubuntu panel right clicking the panel, choosing "add new item" and then choosing "Launcher" and in the Program Launcher window fill in the command: "thunar ~/certain-map-path" and then close the Program Launcher window, there appears a new button in the panel which does absolutely nothing. When I replace the command just mentioned by just "thunar" pushing the button makes Thunar open in my home directory. Is it not possible in the Program Launcher to add something to a command? Can anybody tell me how to create a shortcut to a map that will open in Thunar?
Thx for reading,
Thomas de Graaff.

---

### Post by Rui Pais on 2007-04-10
hi,
don't use symbol ~. Thats all.

Either just enter "thunar certain-map-path" (without ~/) or use a complete path, like "thunar /home*<your_user_name>*/certain-map-path"

hth

---

### Post by rai4shu2 on 2007-04-10
Rather than ~ what you should do is use $HOME. Like this:

Thunar "$HOME/docs"

---

### Post by slayerboy on 2007-04-10
> **rai4shu2 said:**
> Rather than ~ what you should do is use $HOME. Like this:

Thunar "$HOME/docs"

or you could try:
```
thunar /home/*INSERT YOUR USERNAME HERE*/docs
```Also, beware that in Linux, caps do make a difference:

Let's say I have a folder called Documents and I want to change to it in a command line,

```
cd /home/slayerboy/documents/
``` will tell me it doesn't exist.

```
cd /home/slayerboy/Documents/
``` will lead me directly into that directly.

---

### Post by tommie74 on 2007-04-10
Great! Not using the ~ did the job! Thx all! 
Now if anybody knows how to add a map icon to the button it would make my day!
This community is fantastic! I have fallen in love with Linux. (at least, as far as one is able to love something like an operating system...   ; )

Thx again,
Thomas.

---

### Post by Rui Pais on 2007-04-10
> **tommie74 said:**
> Great! Not using the ~ did the job! Thx all! 
Now if anybody knows how to add a map icon to the button it would make my day!
This community is fantastic! I have fallen in love with Linux. (at least, as far as one is able to love something like an operating system...   ; )

Thx again,
Thomas.

you're wellcome :)

for the icon:
right click on the button and choose 'Properties'
click on the icon button (of Properties window) and you can choose between some default or, on bottom of the list, choose 'Other' to set a personalized one.

Have fun

---

### Post by tommie74 on 2007-04-10
Ola Rui,
obrigado de novo!

---

### Post by Rui Pais on 2007-04-10
> **tommie74 said:**
> Ola Rui,
obrigado de novo!

De nada.

(nice portuguese ;))

---

