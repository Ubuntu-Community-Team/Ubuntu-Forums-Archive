---
title: "cups locks me out"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Michael Walters on 2007-08-04
Hello All,

Whenever I try to get my printer working by configuring CUPS the CUPS administator locks me out. I logged in as root and could not get in. I logged in as my user name, and could not get in.

I have an Epson STylus CX 4800 but I had the same problem when I tried to configure cups for my old Lexmark Z52 printer.

The problem seems to be logging into the CUPS printer manager.

I also want to disable sudo and replace it with a user log in and true root login. Would that possibly help?

Once I get the printer working, even if I do not disable sudo to do that, I would like to disable sudo after that.

Regards,

Michael

---

### Post by steve.horsley on 2007-08-04
I'm not sure what you mean by "loggin gin" to teh CUPS pronter manager. Can you explain?

I can tell you that starting the printer configuration dialog from System->Administration->Printing can spend several minutes reading the printer database, but is does eventually finish (for me).

Using a true root login is not advisable. Not only as a security risk, but because a number of configuration apps have been modified to expect being used from a non-root account, and I have read that using them from a real root login can cause problems.

---

### Post by Michael Walters on 2007-08-04
Hello Steve,

Thanks for your prompt reply.

When cups printer administrator is called on to confiure cups for the printer, it asks me for a password. And when I supply that password it again asks me for the password.

I do not remember whether it also asks me my login name, but it may do that too. And when I submit it it asks my login name and my pasword again.

I would like to send you a log file and some screen shots of what happens when I try to add a printer.

The cups printing manager works in my Suse 10.2 and Zenwalk 2.6.x (Old Zenwalk) and Zenwalk 4.6.1 .

---

### Post by Michael Walters on 2007-08-04
Hello all,

How do I send log files and screen shots of what happens when I try to add a printer and configure CUPS?

All help would be appreciated,

Michael Walters

---

### Post by steve.horsley on 2007-08-05
You are using the web-based CUPS administrator? I don't know what criteria that uses to decide if you are permitted - probably membership of one or other unix group.

Have you tried the gnome printer configuration - System->Administration->Printing? Ths has always worked for me, despite the pregnant pause while it reads the printer database.

---

