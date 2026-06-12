---
title: "database locked-adept manager"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by yanqui on 2007-01-29
I keep getting a message:

Read Only mode:  Database Locked - Adept Manager
You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system (probably some other Adept application or apt-get or aptitude).  Please close the otehr application before using this one.

I can't figure out what is running.  I have rebooted, I have rebooted in recovery mode, I have done a repair from CD.  In windows, I would use "task manager."  Does Ubuntu have something like that?

---

### Post by carlosfocker on 2007-01-29
This usually happens when the GUI interface for apt-get is open(Synapetic Pack manager). As far as a task manager there is a system monitor i believe under system-- >Administrator menu.

---

### Post by yanqui on 2007-01-29
> **carlosfocker said:**
> This usually happens when the GUI interface for apt-get is open(Synapetic Pack manager). As far as a task manager there is a system monitor i believe under system-- >Administrator menu.

I would expect it to happen at that time.  It's not open.  I should mention, I'm using Kubuntu, so the K desktop offers a few different options.  But the Adept is not open.  As I said, I've rebooted, and it still thinks it's open.  Wouldn't a reboot normally close it?

---

### Post by yanqui on 2007-01-29
I fixed.  I ran these two commands:

sudo apt-get -f install

sudo dpkg --configure -a

fixed the problem.  found the stepping stones here in the forum, had to play with it a little.

---

### Post by priam on 2007-01-31
Had the same problem but this fixed it.  Thank you very much!

---

### Post by koolguynet on 2007-02-14
I, also had the same problem and that fixed it as well.  Thanks!

---

### Post by noa814 on 2007-03-01
Can someone tell me where I should place these commands listed.

sudo apt-get -f install

sudo dpkg --configure -a

I have Kubuntu loaded and have been running fine until this locked message appeared

---

### Post by yanqui on 2007-03-02
In the system menu, select terminal, and when you get the command prompt, type it exactly as you see it here.

---

### Post by noa814 on 2007-03-03
Thanks for your assistance. I´m up and running

---

### Post by piccolokin on 2007-04-11
Thanx!! I FIxed the problem!! Bye!!!!!:KS

---

### Post by ector on 2007-04-18
Fixed my problem too, thanks! :)

---

### Post by speedygeo on 2007-04-24
Thank you yanqui!!! I fixed it!

---

### Post by DefrostedTuna on 2007-05-02
sweet, that fixed mine too. i installed automatix and it started doing that. thx ^_^.

---

### Post by sambehera on 2007-06-20
> **yanqui said:**
> I fixed.  I ran these two commands:

sudo apt-get -f install

sudo dpkg --configure -a

fixed the problem.  found the stepping stones here in the forum, had to play with it a little.
thanks yanqui! that fixed my problem too! :D i had rebooted 7 times and even tried killing adept frm the root login but nothing seemed to be working... this did the trick!

---

### Post by Exodas on 2007-06-30
Thank you!!:KS:D

---

### Post by leexgx on 2007-06-30
this is an bug that happens just by opening update or Update failing (Stuped java JRE install with an agree box at the bottom does not even ASK you if you want to Skip it and makes the whole update Stop) and ends up brakeing the apept (as thats what did it for me)

this BUG has been in ubuntu for the Last 4 vers (data base locked) all it seems to be doing is checking if A file is there, not checking if it is really in use poor way of checking if the data base is open and No way of resetting it in the GUI or reboot

what it should do is Tell the user Adept may be running still check in the task bar if its not there restart the pc and try agane (it should Clean up apept on reboot) at most One line needs to be added to the system start up to remove the database lock File

allso whare is update its missing on Kubuntu i cant manuley start it on Kubuntu as i can on ubuntu (i have to wait for auto update to pop up and that can be disabled as well when it should not be allowed to new users  mite just click never show agane and miss security updates)

if i can i report this as an bug on the bugza thing

no way i can use ubuntu for customers if Simple problems like this crop up (resorting to forums and command line every time an minor problem props up) 

apart from that seems to be getting better (at least now i can play some music web sites but that does not work completey as well)

---

### Post by someguyonthestreet on 2007-07-12
Mine is the same. Except when i get to the terminal i can't type in my password.

---

### Post by madsmaddad on 2007-11-01
I'm Sorted too. Thanks. 
:)

---

### Post by GayRockies on 2008-02-02
Thanks for the help.  This fixed my problem.

I've been using Ubuntu for over a year, and just now trying Kubuntu.  There are quite a few things about the interface look/feel that I like, but if this type of problem is common (come on, rebooting a computer should fix something like this), I might just have to go back to Ubuntu exclusively.

Thank you, though, for this thread.

Note to forum administrators, though:  This is about the 20th time that I have done a search for a topic and found nothing, until I went to post a thread on the topic.  An upgrade for the search tool so that it works as well when searching as it does when you're about to post would be a great idea.

Kind regards,

M.J. Christensen

---

### Post by spoolboyy on 2008-02-22
Thanks this helped me too!

also i didnt read all the posts but if your looking for Kubuntu's "task manager" its under System and its called KSysGuard.

-adam

---

### Post by davenport651 on 2008-02-24
Thanks!  I also had this problem in Kubuntu.  Does anyone know what "dpkg --configure -a" actually does to the system?

---

### Post by danenbysk on 2008-03-16
Also had this problem and this fixed it! Although I typed the commands in the reverse order shown here. No idea why I had to do that, but it worked. Thanks!  Newbie

---

### Post by scrime on 2008-03-18
Thanks yanqui helped me out as well!! :)

---

