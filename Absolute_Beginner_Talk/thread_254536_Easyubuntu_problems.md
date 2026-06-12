---
title: "Easyubuntu problems"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by davy9 on 2006-09-10
Hi all,

I am a new ubuntu user and am currently trying to install easyubuntu. I copied and pasted the four lines of code into the terminal and ran them. I then got the following error messege:
------------------------------------------------------------------
System sanity check: PASSED!

Your sources.list does not match your system configuration.
Either you have changed your sources.list or an system
upgrade has failed. EasyUbuntu will not run unless these are fixed!

-------------------------------------------------------------------

I have been tweaking the system configuration a little (just through the menues in System->Preferences and System->Administration). However, I do not know if I did anything to change this sources.list file. 

I also tried to use just python easyubuntu.in instead of sudo python easyubuntu.in but I then got the following error message:

-----------------------------------------------------------------------
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

EasyUbuntu is now trying to run 'dpkg --configure -a'
System sanity check: Failed!
Errors:
--------
dpkg: requested operation requires superuser privilege

EasyUbuntu will not run before these errors are fixed. Please fix them and try again
-----------------------------------------------------------------------

If anyone could help it would be greatly appreciated. Also, is there anyway to get default sources.list file and if so what is the directory of where I would replace it?

Thanks in advance.
Jake

---

### Post by richbarna on 2006-09-10
Hi, I'm sorry that I can't help with easyubuntu, but have you tried Automatix? It's the same as easyubuntu but with more features.

I used automatix at the beginning and never had any problems. Maybe you prefer easyubuntu. It's just a suggestion.

The link is in my sig
|
|
v

---

### Post by Abstract on 2006-09-10
If you follow [this](http://psychocats.net/ubuntu/sources.php) guide it should reset your sources.lst and you should be able to use Easyubuntu.

---

### Post by davy9 on 2006-09-10
Thanks I'll give it a look.

---

### Post by davy9 on 2006-09-10
I now was able to run easyubuntu but after if finished installing it tells me that broken packages must be fixed before it will work. Any Ideas?

Thanks again in advance.

---

### Post by bluebuzzard on 2006-09-10
I got the same error message using vs 3.022 :(

---

### Post by bluebuzzard on 2006-09-10
my advice is to forget easyubuntu and give Automatix a try - it worked fine on my system and you also get more installation options. Best of luck.

---

