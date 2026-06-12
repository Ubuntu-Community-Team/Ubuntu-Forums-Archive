---
title: "new user account with same priveleges-how?"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by metuwi on 2005-12-31
hi all,
i would like to create account on kubuntu with all of the same permissions and priveleges that i have (eg. sudo, etc). i tried to create such an account, but upon logging in there is an error message that says permission denied, sound could not be set up, and sound will now be directed the the null output device. 

how can i create such an account?

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=metuwi]hi all,
i would like to create account on kubuntu with all of the same permissions and priveleges that i have (eg. sudo, etc). i tried to create such an account, but upon logging in there is an error message that says permission denied, sound could not be set up, and sound will now be directed the the null output device. 

how can i create such an account?[/QUOTE]
When you create the new account, just make sure to add the same groups that your current user has.  E.g. audio group if the user should be able to use the sound card.

---

### Post by Sutekh on 2005-12-31
The commands 
```
groups **olduser**

```
and
```

groups **newuser**
```
should have almost identical results.  Except for the group of the same name as the user; **olduser** is in the **olduser** group, and **newuser** is in the **newuser** group.

---

### Post by kanem on 2005-12-31
There's a GUI for this: System -> Administration -> Users and Groups

Double click on the new user's name and you'll see a new window with a tab called 'User privileges'. Just make sure that all the boxes that are checked for you original accout are checked for the new one.

Hmm. Just noticed you need it for Kubuntu, not Ubuntu. Still, I think there is a GUI for this.

---

### Post by metuwi on 2006-01-01
yes, there is a gui, i just wasnt sure what to do. thank you much!

---

### Post by Gray. on 2006-01-08
Is there a GUI tool for Xubuntu? Only my account and not the others I created can use audio. Unless theres a way to do it in CLI.

*EDIT* Well I found out how to add a user to a certain group though the CLI. The command is ```
sudo usermod -G <groupname> <username>
```

---

