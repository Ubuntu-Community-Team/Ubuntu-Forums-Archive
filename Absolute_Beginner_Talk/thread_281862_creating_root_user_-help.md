---
title: "creating root user -help"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by aznboi on 2006-10-21
hi, this is my first time using ubuntu for years. i used to use it when it was 5.10 but then i went back to windows but now im back with ubuntu. When i installed it with 5.1 i remember i had to login and with the terminal do some command to create the root user and password. Does anyone kno how to do that because right now i cant do any sudo commands because i dont have the root user so there is no password fro it. THnx.

EDIT
i think it was something with useradd

---

### Post by raul_ on 2006-10-21
Are u sure? I'm pretty sure that linux FORCES u into creating a root password. Maybe you're talking about the ```
 sudo su root 
``` ?

---

### Post by aznboi on 2006-10-21
that worked i think but how do i change the root password from there? i didnt set a root password so i dont kno wat it is. thnx alot for the help

---

### Post by Sef on 2006-10-21
> Does anyone kno how to do that because right now i cant do any sudo commands because i dont have the root user so there is no password fro it.

What you wrote is incorrect.  Sudo is for commands that require root.  If you are having problems with sudo, either you are inputting the wrong password, which is the one that you use to log on to your computer; the command that you are using is incorrect; or possible you had a bad install.

What are you trying to do? 

Could you copy and post from terminal what you are trying to do, and what the result is.

---

### Post by aznboi on 2006-10-21
i dont kno my root pw it didnt ask for one on install but ikno my normal user pw. thnx

---

### Post by Sef on 2006-10-21
Root is turned off by default.  It is safer that you.  Much harder to break into your system.

---

### Post by aznboi on 2006-10-21
thnx for all the help guys but i figured out wat the command was. i dont kno if i was unclear or anything about my problem so thats probably my fault lol. the command was

```
sudo passwd root
```

thnx for all the help

---

