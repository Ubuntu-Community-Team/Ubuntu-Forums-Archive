---
title: "login accounts problem."
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-01-16
Hi its been like 6 months since I touched my Ubuntu :rolleyes: from the time when I experimented with the Windows/Linux-Dual Booting period.

I only created one account(superuser?) now after 6 months I've forgotten it so I can't get into the GNOME.  
Now without going into the technical hacker stuff of re-finding your login/password wich you forgot.

Is there a way to get into GNOME by creating a **GUEST account** just like in Windows XP?  Or some other way to log into the system by creating a temporary account.
I realise this isn't the best solution, that the best solution is to re-install a new Distro.  But I just wanted to have a little looksie inside the Desktop in order to solve a problem which I encountered from trying to install Breezy .iso, which is a whole another chapter that I wont go into here.

---

### Post by jasay on 2006-01-16
You might try [this]("http://help.ubuntu.com/starterguide/C/ch08.html#id2538963").

---

### Post by Sef on 2006-01-16
> Is there a way to get into GNOME by creating a GUEST account

System ----> Administration -----> Users and Groups  -----> Password ----->  Add User

---

### Post by jingo811 on 2006-01-17
tnx y'all that was more than I asked for :KS I appreciate it!
.....so I followed **Chapter 8.1**:

> -Select Ubuntu, kernel 2.6.12-8-386 (recovery mode)
-Press Enter to boot

And managed to get root user access w/o login.  But since I'm not a good terminal typing kind of guy it doesn't really do much for me, I only know how to GUI.  Is there a way for me to list all accounts name for my PC in the root user terminal.
Because I'm not having trouble remembering which passwords alternatives to tryout but rather I'm having trouble remembering how I spelled my login user name more exactly.  If all CAPITAL, small, or mixed, maybe even some obscure Username that I don't usually use?

---

### Post by jasay on 2006-01-17
[QUOTE=jingo811]tnx y'all that was more than I asked for :KS I appreciate it!
.....so I followed **Chapter 8.1**:



And managed to get root user access w/o login.  But since I'm not a good terminal typing kind of guy it doesn't really do much for me, I only know how to GUI.  Is there a way for me to list all accounts name for my PC in the root user terminal.
Because I'm not having trouble remembering which passwords alternatives to tryout but rather I'm having trouble remembering how I spelled my login user name more exactly.  If all CAPITAL, small, or mixed, maybe even some obscure Username that I don't usually use?[/QUOTE]
I'm sure there is a better way, but I'm not the cli guru myself so I would ```
cd /home
ls
```since every user should have a home directory, that will list said directories (plus some other stuff you don't have to worry about).

Or make a new user:```
adduser <username>
```

---

### Post by jingo811 on 2006-01-18
> I'm sure there is a better way, but I'm not the cli guru myself so I would
Code:

cd /home ls

since every user should have a home directory, that will list said directories (plus some other stuff you don't hav

Never in a million years would I have guessed that I used **login/pass**=[COLOR="Blue"]guest/guest[/COLOR] as my superuser account :D 6 months ago.
> {The simplest solution is normally the correct solution}
Occams Razor - (or something in that style) :rolleyes:

---

