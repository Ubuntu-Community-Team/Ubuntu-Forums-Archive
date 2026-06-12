---
title: "uhhhhh....how to log on as root??????"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Caermundh on 2007-06-03
This is going to sound like the worlds DUMBEST question buuuuuuuut..........

How do i log on as the root user in ubuntu 7.04? im using the correct password, but if i try to log in at the initial login in screen as root it tells me "The system administrator is not allowed to login from this screen"

If i cant log in from the initial passwrd screen, where the heck DO i login as root???

---

### Post by miggols99 on 2007-06-03
Why do you want to login as root? You can use sudo (gksudo for graphical programs) to make your commands run as root.

You can use the recovery mode (found when you boot) which lets you do everything as root. Logging in as root is disabled by default in Ubuntu for security reasons.

---

### Post by bone43 on 2007-06-03
> **Caermundh said:**
> This is going to sound like the worlds DUMBEST question buuuuuuuut..........

How do i log on as the root user in ubuntu 7.04? im using the correct password, but if i try to log in at the initial login in screen as root it tells me "The system administrator is not allowed to login from this screen"

If i cant log in from the initial passwrd screen, where the heck DO i login as root???

Hello try here...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Caermundh on 2007-06-03
well, the reason i need to log in as root is i am trying to edit the etc\network\interfaces file so i can put in the information needed for it to configre my wireless adapter at startup. Ive already figured out how to configure it and all, but after I edited the file in Applications->Accessories->Text Editor, when I tried to save it, I got an error message about not being the owner therefore i cannot save it. Root is the owner so i assumed I had to be logged in as root to edit it.

Can you edit the etc\network\interfaces file with sudo?

---

### Post by Lord Illidan on 2007-06-03
> **Caermundh said:**
> well, the reason i need to log in as root is i am trying to edit the etc\network\interfaces file so i can put in the information needed for it to configre my wireless adapter at startup. Ive already figured out how to configure it and all, but after I edited the file in Applications->Accessories->Text Editor, when I tried to save it, I got an error message about not being the owner therefore i cannot save it. Root is the owner so i assumed I had to be logged in as root to edit it.

Can you edit the etc\network\interfaces file with sudo?

Yes, with ```
gksudo gedit /etc/network/interfaces
```

---

### Post by Caermundh on 2007-06-03
thanks Lord Illidan, that did indeed work :D

---

