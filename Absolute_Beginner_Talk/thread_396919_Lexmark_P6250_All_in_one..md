---
title: "Lexmark P6250 All in one."
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Revord on 2007-03-30
Well, as the title above says, I have the indicated printer attatched to my winxp machine upstairs from my ubuntu machine. I have a working wireless network, and the printer is set up to be a network printer. I have done some searching for the last hour and a half, and have found nothing that I have been able to use to make Ubuntu recognise that printer. So, my questions are:

1. Do I need to install a driver for ubuntu to use that printer.

2. If so, I have found no reference to that particular model for a linux driver from several sources: Lexmark, Linux drivers, etc. Does anyone know where I can find it, or how to make one.

3. If not, then what could I do to get the crazy thing to work for me.

Im using Dapper Drake on the ubuntu machine, XP sp2 on the other one. Im open minded, and willing to do some leg work myself, however, I dont know where to begin. If you need clarifications on any specs, or other specifics, let me know. Ill get them for you.
Revord

---

### Post by 67GTA on 2007-03-30
Unfortunately your printer is not supported [http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-P6250](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-P6250)

The "paperweight" comment means it probably won't be either. You will probably have to get another printer. Check the Open Printing database [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi) and find one that is supported before you buy.

---

### Post by STREETURCHINE on 2007-03-30
unfortunatly lexmark dont run well in linux if at all,hp on the outher hand are well supported even the cheapies,

---

### Post by Revord on 2007-03-31
Ok, well, another idea is this: What would be the easiest way of sharing files between my xp machine and the ubuntu one so that I can at least make use of the printer via xp?

---

### Post by louieb on 2007-03-31
> **Revord said:**
> Ok, well, another idea is this: What would be the easiest way of sharing files between my xp machine and the ubuntu one so that I can at least make use of the printer via xp?
My home network printer is plugged in to a PC running XP. The nice thing about that is it will pass the driver along to other network PC's running XP and need to use that printer. Unfortunately Ubuntu (Linux) can't use the driver. For my HP-7660 its easy System>Administration>Printing>add printer. Did you try that. There may be a drive listed that is close enough to print black and white docs. Doesn't hurt to see. You can always delete the printer if it doesn't work. 

I guess now you want to get on the XP PC to open a file on the Ubuntu PC and print it. For that you use Samba.  Open the file manager and right click on the folder you want to share. You will see a share this folder option. Click on it and follow the prompts.

---

### Post by Revord on 2007-04-04
> **louieb said:**
> My home network printer is plugged in to a PC running XP. The nice thing about that is it will pass the driver along to other network PC's running XP and need to use that printer. Unfortunately Ubuntu (Linux) can't use the driver. For my HP-7660 its easy System>Administration>Printing>add printer. Did you try that. There may be a drive listed that is close enough to print black and white docs. Doesn't hurt to see. You can always delete the printer if it doesn't work. 

I guess now you want to get on the XP PC to open a file on the Ubuntu PC and print it. For that you use Samba.  Open the file manager and right click on the folder you want to share. You will see a share this folder option. Click on it and follow the prompts.

Thank you for your suggestions. I tried both. The drivers didnt work at all for me. The other thing is that Im having some difficulty getting Samba set up. My first problem is I have no clue what Im doing, and the second thing is that I found several places that give some instructions, but Im having a hard time piecing them together, and making sense of them. I have Samba installed, however, ever since I installed Samba, I have been getting error messages whenever I do an update, and it always is linked to Samba, so I wonder if my installation is buggy. Im sure the answer is a simple one, however, Im having a hard time getting my head around what the solution could be. Any ideas? If you need clarification, Ill be more than happy to provide it.
Revord

---

