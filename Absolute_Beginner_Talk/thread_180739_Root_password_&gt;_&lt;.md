---
title: "Root password &gt;_&lt;"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Mr Match on 2006-05-22
A few days ago, I installed Ubuntu and I have been having trouble installing programs. :( 

I downloaded the Linux Java plug-in for Firefox, and to install it, I go to the terminal, I type su, and it asks me for the root password...the thing is, I don't know it... and I'm the only person who has an account on this computer! I installed Ubuntu myself, and never did it ask me for a root password :-? 

Who can help me in finding out how to change the root pass, or how do I learn what the root pass is?


Thanks! :) 
~Mr Match

---

### Post by ProjectGod on 2006-05-22
[https://wiki.ubuntu.com/RootSudo?highlight=%28root%29](https://wiki.ubuntu.com/RootSudo?highlight=%28root%29)

---

### Post by Stew2 on 2006-05-22
As the link says, there is no "root" password in Ubuntu. When it asks you for your root password you just type in your regular log in password. Oh and in some password boxes you cant see any asterix's or anything to tell you that it is recognizing your typing, just type it in and hit enter anyway. Hope this helps!
Cheers, :) 
Stew2

Edit:ProjectGod's link has a much better explanation of sudo and root password usage, I should have read it before I posted. Oops!

---

### Post by catlett on 2006-05-22
If you really want one you can make one. ```
sudo passwd root
```
Then you can use the terminal like in other distros with su and a root password. Or if you want you can get to a root terminal by using ```
sudo su
``` Just to clarify. Sudo gives root priveleges for that one command that comes after it. Your sudo password is your regular user password. To get technical sudo is for superuser. There is a superuser file with users who have superuser status. If you have superuser status you can invoke it at the terminal to run commands with root priveleges.
So in Ubuntu all root commands have to be preceded by sudo unless you do the 2 things I just listed.

---

