---
title: "Insecure?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2008-01-02
Okay i get this question very often, and i really don't know how to answer it. Isn't Linux insecure? passwords are saved in plain text files in in plain text format, or they are to be entered on terminal in plain text format, i am talking about proxy authentication etc...  if anyone sees you entering the password, you are dead.

---

### Post by llamakc on 2008-01-02
No one dies.

---

### Post by (((X))) on 2008-01-02
You can set ubuntu to boot without asking you for passwd, so nobody can see you typing your password, or set bios-password.

---

### Post by ukripper on 2008-01-02
> **shoaibi said:**
> Okay i get this question very often, and i really don't know how to answer it. Isn't Linux insecure? passwords are saved in plain text files in in plain text format, or they are to be entered on terminal in plain text format, i am talking about proxy authentication etc...  if anyone sees you entering the password, you are dead.

Well it would be as insecure as somone forced into your house by pushing you aside while you are unlocking your own house door. Therefore, it won't be the door fault if someone forced into your house(you should be more watchful) similarly,  that is not linux fault if someone sneaked up your password while you type( it would be yours).

---

### Post by meindian523 on 2008-01-02
Also,passwords are NOT saved in text files in plain text,if you have heard of the /etc/shadow file,you wouldn't have that misconception.

At any rate,if you have people with physical access to your PC,you are dead anyway.

---

### Post by LowSky on 2008-01-02
what are they comparing it to? I can hack someone elses windows install much easier then linux. I just wiped a family member old Windows hard drive, but before I did I went into their old documnets and setting folder and copied the old data onto a DVD.

---

### Post by aysiu on 2008-01-02
> **shoaibi said:**
> if anyone sees you entering the password, you are dead. Isn't that true of anything? Windows, Mac, Linux? Bank ATM cards?

---

### Post by meindian523 on 2008-01-02
> **aysiu said:**
> Isn't that true of anything? Windows, Mac, Linux? Bank ATM cards?

+1.:)

---

### Post by aysiu on 2008-01-02
By the way, as mentioned before, they are not stored in plain text. If you believe they're stored in plain text, please tell us the name of the file that the plain text passwords are stored in.

Also, when you enter your password in the terminal, there is no visual display whatsoever. When you enter it in the graphical user interface, black dots appear.

In other words, your password is never shown in plain text.

---

### Post by picpak on 2008-01-02
The bug of passwords being stored in plain text was found over 2 years ago. It's been fixed.

As everyone else said, passwords aren't stored in plain text files.

---

### Post by ukripper on 2008-01-02
hope you are not typing your passwords in text editor instead of terminal?

---

### Post by FuturePilot on 2008-01-02
If you have Pidgin remember your password it's stored as plain text in and .xml file which can be opened by a text editor. :shock:
~/.purple/accounts.xml

---

### Post by Cypher on 2008-01-02
Native passwords..and by that I mean the password you use to login to Linux is securely saved on the filesystem. It is not possible to recover the real password from the hash that is stored in the file.

You are right that the proxy authentication is sent as plain text and that can indeed be an issue if you are in an environment where people are going to look over your shoulder. But if you are using Linux in our house without anyone peeking over your shoulder, I think you are perfectly fine..

---

### Post by FuturePilot on 2008-01-02
Yeah, seems like Pidgin does this for a reason.
[http://developer.pidgin.im/wiki/PlainTextPasswords]("http://developer.pidgin.im/wiki/PlainTextPasswords")
 Otherwise I think that would be the only exception to this. Other system passwords are not stored in plain text.

---

### Post by Flyingjester on 2008-01-02
> **aysiu said:**
> Isn't that true of anything? Windows, Mac, Linux? Bank ATM cards?

agreed.

---

