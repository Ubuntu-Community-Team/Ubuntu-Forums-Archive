---
title: "logging internet activity...."
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-01-12
i would like to create an internet log file which in simple words is going to log the internet activity
from... to... where... by who...(programm/process)

how can i do that and be automated how to access the log (if possible by the syslog)?

---

### Post by bobyy on 2008-01-12
Hy man
a good tool witch i recomand it is IPTRAF ..and this tool have a lo file option ..try`it it is a great tool.
$sudo aptitude install iptraf

---

### Post by someoneouthere on 2008-01-12
> **bobyy said:**
> Hy man
a good tool witch i recomand it is IPTRAF ..and this tool have a lo file option ..try`it it is a great tool.
$sudo aptitude install iptraf

ok installed...any special instruction for my request?:guitar:

---

### Post by bobyy on 2008-01-12
ok..
open the terminal 
strart $sudo iptraf
you have some option :configure
check the logss option /on
in /var/log/iptraf  you will have all log`s.......thats all :)) enjoy

---

### Post by someoneouthere on 2008-01-12
is it possible to to "import" it to the systeml og?

---

### Post by bobyy on 2008-01-12
in witch ..system log...what means that?..it is in /var/log/iptraf.....sowhat`s the problem .be more specific  please.
 aaa...ok i understand ...i use just command line to see logs ..i dont know how to import to system log ...but iti is IPTRAF what you want..?

---

### Post by braddcadd on 2008-01-12
I assume you are talking about the System Log Option in the System Pulldown Menu.  If so just open the system log window, then choose the File->Open from the pulldown menu.

Select the file you want to add:
/var/log/iptraf (or whatever it is)

HTH

---

### Post by someoneouthere on 2008-01-12
it is in folder but it woulbe really nice if i could see it through system-->administation-->system log..

---

### Post by someoneouthere on 2008-01-12
> **braddcadd said:**
> I assume you are talking about the System Log Option in the System Pulldown Menu.  If so just open the system log window, then choose the File->Open from the pulldown menu.

Select the file you want to add:
/var/log/iptraf (or whatever it is)

HTH

just saw the message....yes this is it but i need permission to open the folder....

---

### Post by bobyy on 2008-01-12
$sudo chmod 777 /var/log/iptraf/iptraf.log

---

### Post by someoneouthere on 2008-01-12
is it safe to change the permission?

---

### Post by bobyy on 2008-01-12
NO...but is just a log file.....asuming nobody hack your machine ,my path of the command was whrong....i dont remember exactli where in iptraf.log

---

### Post by someoneouthere on 2008-01-12
> **bobyy said:**
> NO...but is just a log file.....asuming nobody hack your machine ,my path of the command was whrong....i dont remember exactli where in iptraf.log

ok but is there any way to modify it only for the syslog?

---

### Post by bobyy on 2008-01-12
use log wiewer like root

---

