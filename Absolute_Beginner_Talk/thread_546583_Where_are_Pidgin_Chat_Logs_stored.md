---
title: "Where are Pidgin Chat Logs stored?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-09-09
Does anyone know where the Pidgin chat logs are stored?
There is no such file as .pidgin in my home directory or anything of such!
Thanks,

---

### Post by scxtt on 2007-09-09
it's ~/.purple/logs ... assuming you have logging turned on.

---

### Post by Mazen on 2007-09-09
perfect!
thanks:)

---

### Post by nickleus on 2008-01-30
on my windows vista they are here:
C:\Users\myuser\AppData\Roaming\.purple\logs

---

### Post by LeAstrale on 2008-01-30
i have actually been wondering that myself.. but this does answer my question :)

---

### Post by komal9 on 2008-02-16
hii..
m new to ubuntu..
could u pls tell me exactly d path through which i can get the log files..
and what should i do if i want to log all chats for a particular account.

---

### Post by seventhc on 2008-02-16
You also view the logs from within pidgin. You can open the main window and click *Buddies>View User Logs* then enter the uid of who's log you want, or if you have a chat window open you can click on [I]Conversation>View Log

[/I]Also, in a chat window you can turn logging on there by[I] Option>Enable Logging
[/I]

---

### Post by komal9 on 2008-02-17
yeah that info ws helpful.. thnks

where are these logs stored ?? like on XP its in folder c:\program files\yahoo!\messenger\profiles\usrname.. likewise where are they stored in ubuntu

is there any way to automatically enable to log chat for all contacts of a particular accounts?

---

### Post by seventhc on 2008-02-17
Home folder set it to show hidden files then look for .purple

**Edit:** Oh wait, I think those are different logs.

---

### Post by DavidWeight on 2008-03-08
If you go to filesystem, then /etc/purple/logs

HTH

---

### Post by steveneddy on 2008-03-08
I log my conversations and mine are in

```
~/.purple/logs
```

Then the logs are under the IM client folder

and each folder is organized by user.

In your home folder, open it and hit the Ctrl+H keys to show the hidden files.

Near the bottom you will see the .purple directory.

---

### Post by dracomordag on 2008-06-26
is there any way to change where pidgin stores the logs? I dual boot, and would like to merge my ubuntu pidgin logs with my vista pidgin logs

maybe if i create a shortcut folder thing so that it treats the two folders as the same?

---

### Post by dracomordag on 2008-06-26
is there any way to change where pidgin stores the logs? I dual boot, and would like to merge my ubuntu pidgin logs with my vista pidgin logs

maybe if i create a shortcut folder thing so that it treats the two folders as the same?

EDIT: ^that worked

---

### Post by efrenefren on 2008-06-30
> **DavidWeight said:**
> If you go to filesystem, then /etc/purple/logs

HTH

no logs folder in /etc/purple

---

### Post by AAK on 2008-07-17
> **efrenefren said:**
> no logs folder in /etc/purple

it's in home/user/.purple

---

