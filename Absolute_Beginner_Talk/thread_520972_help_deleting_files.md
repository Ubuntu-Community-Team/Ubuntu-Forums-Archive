---
title: "help deleting files"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by shepeard on 2007-08-08
I am new to umbutu and am trying to install VMware. II had downloaded some files earlier and now when I try to use Automatix or Synaptic it starts to install vm server but then it says it find some previously installed files and I need to delete them first. I can find them in search and through "computer" but it says I don't have access to more them to the trash. I have even created a root account that I can log into using the user and group manager (it's clear I'm from the GUI world).  Can anyone please talk me through setting up permissions so i can deleted files and then install using these package managers? Thanks alot. 
GS:confused::confused:

---

### Post by Al3xK3aton on 2007-08-08
Did you chmod them?

---

### Post by Dr Small on 2007-08-08
Go to the terminal:
Applications > Accessories > Terminal

and type: "gksudo nautilus" (delimiting the quotes)
This will log you in as sudo (super user, root) in nautilus, your file manager, and then you will be able to browse to the folder and delete things to the trash can.

Regards,
Dr Small

---

### Post by Inxsible on 2007-08-08
what file are you trying to delete?

you can use the command line like this

```
sudo rm -rf /path to the file
```

---

### Post by Al3xK3aton on 2007-08-08
> **Inxsible said:**
> what file are you trying to delete?

you can use the command line like this

```
sudo rm /path to the file
```

No you can't.

---

### Post by Dr Small on 2007-08-08
Inxsible, this new Ubuntu user is, as he clearly stated, from the "GUI world", so we must accomodate his wishes. Sending out a lengthy command to him will detter him away.

Al3xK3aton, you are just nitpicking. It will work if the path to the directories doesn't have a space in them. Otherwise, it must be with quotations around the path.

Dr Small

---

### Post by Inxsible on 2007-08-08
> **Al3xK3aton said:**
> No you can't. Why not. you of course have to replace the path to whatever file you want to delete (which i think is pretty clear from my post).

> **Dr Small said:**
> Inxsible, this new Ubuntu user is, as he clearly stated, from the "GUI world", so we must accomodate his wishes. Sending out a lengthy command to him will detter him away.

Al3xK3aton, you are just nitpicking. It will work if the path to the directories doesn't have a space in them. Otherwise, it must be with quotations around the path.

Dr Small Yup he did say he came from the GUI world, but he didnt say he was averse to the terminal. and i think it always better to know different ways of doing something. Also logging into nautilus with gksudo nautilus, like you suggest, is definitely not safe, especially for new users since they have a free reign and can delete/modify something they are not supposed to. with the terminal, however, it will only be limited to the file they are actually trying to delete.

just my 2 cents :)

---

### Post by shepeard on 2007-08-08
Thanks everyone for your help- I think Dr. Small is right -new I am- confused I was-Thanks Dr. Small for your help-after following your advice, I had the problem solved in 2 minutes-I'm so new at this I didn't even know about nautilus. You guys are great. GS

---

