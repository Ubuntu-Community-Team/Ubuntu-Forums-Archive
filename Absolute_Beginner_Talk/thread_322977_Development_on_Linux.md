---
title: "Development on Linux"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-12-21
Hello all,
My Linux transition is almost complete. I've rewritten a couple of ASP.NET/MSSQL apps in PHP/MySql and am happy with the results. Now I need to rewrite a couple of automated processes that I wrote in .NET for the task scheduler so that they can be run with Cron. While I find MonoDevelop to be a decent IDE, I'm not absolutely stuck on using Mono. What languages/IDEs should I look into that have native Linux support and good development/deployment situations? I know that this is probably a bit heavy for the beginner forums, but I can imagine that there are other programmers fleeing from Windows as well.

Will

---

### Post by JShadow on 2006-12-21
If you just want to script things, Bash shell scripts would probably be sufficient. Otherwise, python is a good alternative to .NET on Linux.

Could you tell us a little more about the scripts?

---

### Post by steve.horsley on 2006-12-21
You will find a lot of people (including me) suggesting python. It's an interpreted language. It 's unusual in that indentation is used to denote code block structure although this does make it unusually readable and therefore maintainable. Python also runs on Windows.

---

### Post by hod139 on 2006-12-21
Plenty of languages have native linux support.  Languages are just tools, use the right one for the right job.  You can check out the programming talk sub-forum for plenty of active discussions on some of the popular languages.

---

### Post by lamego on 2006-12-21
It would help if you could specify exactly what type of applications are you trying to develop..
Database Frontends ?
Automation with or without GUI ?
Web based ?

---

### Post by zgornel on 2006-12-22
I gues the most supported programming languages in Linux are C and C++. Get some info on GTK+ or QT API's (for graphical devel) and go to work. As for IDEs, Anuta and KDevelop are frequently used (I prefer joe+compile script+xxgdb for my simple stuff).

---

