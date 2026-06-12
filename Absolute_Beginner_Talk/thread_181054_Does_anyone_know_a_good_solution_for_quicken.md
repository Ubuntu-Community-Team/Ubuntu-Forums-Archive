---
title: "Does anyone know a good solution for quicken"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-05-23
in a couple of ways im still bound to windows: games (sometimes) and quicken.  I need to use quicken and it is very important.  What is the best solution so i can use quicken on ubuntu or some sort of opensource substitute

---

### Post by Jagot on 2006-05-23
gnucash which i believe is available in the repositories.

---

### Post by youthforlinux on 2006-05-23
can it read quicken files + can wine run quicken?????????

---

### Post by mjm115 on 2006-05-23
You can find a lot of what you're looking for by reviewing [this article]("http://applications.linux.com/article.pl?sid=05/10/31/1653227&tid=13").

---

### Post by cstudent on 2006-05-23
I use MoneyDance ( [moneydance.com]("http://moneydance.com") ). As a former Quicken user of many years, practically since it was first introduced, I found MoneyDance to be the most acceptable Linux alternative. However, it is proprietary. It cost around $30US, but I think it's worth it. You can download it for free and try it out.

---

### Post by youthforlinux on 2006-05-23
[QUOTE=cstudent]I use MoneyDance ( [moneydance.com]("http://moneydance.com") ). As a former Quicken user of many years, practically since it was first introduced, I found MoneyDance to be the most acceptable Linux alternative. However, it is proprietary. It cost around $30US, but I think it's worth it. You can download it for free and try it out.[/QUOTE]


sweet maybe then ill try it out

---

### Post by usfour on 2006-06-13
[QUOTE=cstudent]I use MoneyDance ( [moneydance.com]("http://moneydance.com") ). As a former Quicken user of many years, practically since it was first introduced, I found MoneyDance to be the most acceptable Linux alternative. However, it is proprietary. It cost around $30US, but I think it's worth it. You can download it for free and try it out.[/QUOTE]

Is this an annual licensing fee of $30 or an indefinite license?

---

### Post by afilonov on 2006-06-16
I successfully installed Quicken 2004 after installing Wine according to Howto. There are several things:

1. Run disk1/*/quinstall.exe program (don't remember exact name of directory under disk1). install.exe in the root of cdrom doesn't work, and actually autoinstall calls quinstall (you can read autoinst.ini)

2. On the first run, installer installs some dlls and exits. You need to rerun it, then it installs OK

3. Initial setup (automatic) in empty installation does not work. I restored my data from backup, works OK.

4. There is a small problem with some pop-up windows. They start flashing different sizes and become unresponsive. The only way to fix it is to unclick "Allow windows manager to control windows" in winecfg (Graphics tab). I only use this option when I definitely need to use those windows (create/edit account, some investment transactions), because Quicken starts full screen and you can't resize it.

I'll put some howto for quicken once World Cup is over...
Internet stuff works! I was able to register and to download info from banks.

---

### Post by usfour on 2006-06-16
[QUOTE=cstudent]I use MoneyDance ( [moneydance.com]("http://moneydance.com") ). As a former Quicken user of many years, practically since it was first introduced, I found MoneyDance to be the most acceptable Linux alternative. However, it is proprietary. It cost around $30US, but I think it's worth it. You can download it for free and try it out.[/QUOTE]


I gave this a try and it looks quite good.  But for $30, I would rather purchase Crossover Office and run Quicken.  I'm currently running Quicken 2002 with CrossoverOffice and it works effortlessly.  ;)

---

### Post by dcstar on 2006-06-17
[QUOTE=usfour]I gave this a try and it looks quite good.  But for $30, I would rather purchase Crossover Office and run Quicken.  I'm currently running Quicken 2002 with CrossoverOffice and it works effortlessly.  ;)[/QUOTE]
I moved from Quicken (it was 95% functional via Wine) to Moneydance and I am quite satisfied.

The Quicken reporting and overall sophistication is another level above Moneydance, but I have found that I didn't use them that much and I don't really miss them now.

The import had a few issues, but I got years of Quicken data imported ok and useable.

At least now I won't be nagged by Quicken to upgrade all the time......

---

### Post by Raavea on 2006-06-17
I took a peek on Google, but it didn't help.

 What is 'Quicken'? I gather it's some kind of budgeting-thingy-ma-bob, but what makes it different from say, a well-set-up Excel/Access document?

 (I forget the equivalent names for my OO-Org stuff... Base and... Something..? :lol:)

---

### Post by usfour on 2006-06-19
[QUOTE=dcstar]I moved from Quicken (it was 95% functional via Wine) to Moneydance and I am quite satisfied.

The Quicken reporting and overall sophistication is another level above Moneydance, but I have found that I didn't use them that much and I don't really miss them now.

The import had a few issues, but I got years of Quicken data imported ok and useable.

At least now I won't be nagged by Quicken to upgrade all the time......[/QUOTE]

I love the budget feature in Quicken.  I'm running Quicken 2002 and it doesn't nag.  It just keeps on working.  :-\"

---

### Post by afilonov on 2007-03-23
Well, I'm sorry I didn't post howto on Quicken installation. I moved from Quicken to Moneydance. It took me the whole day, but I'm quite pleased with results. The reason for moving? Quicken 2004 will stop supporting Internet updates and Online banking in April, and AFAIK nobody succeeded yet in installing 2007 under wine. Also, sunsetting versions after 3 years looks like extortion to me.

---

