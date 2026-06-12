---
title: "Lexmark X1240 drivers are no where in sight"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by toosweetnitemare on 2007-02-26
Hi, i just recently reinstalled ubuntu and i got a new printer a lexmark x1240. i can install it in windows XP just fine using the disk. but i cant seem to find the drivers anywhere, on the disk or the interenet, to install the printer. any help with how to find those drivers would be amazing. thanks. and if you need anymore info about my set up let me know.

---

### Post by NewOldTimer on 2007-02-26
see here....[http://gentoo-wiki.com/HOWTO_Lexmark_Printers#Printers_confirmed_not_to_work](http://gentoo-wiki.com/HOWTO_Lexmark_Printers#Printers_confirmed_not_to_work)

---

### Post by toosweetnitemare on 2007-02-26
thanks but my printer wasnt on that list and the ebuild didnt work

---

### Post by NewOldTimer on 2007-02-26
I may be wrong but I don't think the x1240 is supported yet

---

### Post by toosweetnitemare on 2007-02-26
damn. well thanks your help anyways, i guess ill need to make a windows partion to print.

---

### Post by NewOldTimer on 2007-02-26
more info....[http://www.linux-drivers.org/](http://www.linux-drivers.org/)

---

### Post by Maestro23 on 2007-02-26
> **toosweetnitemare said:**
> thanks but my printer wasnt on that list and the ebuild didnt work

Yeah, there is no love loss between Lexmark and linux in any distro.

---

### Post by toosweetnitemare on 2007-02-26
i think i am bound to not print from my linux box. thank you again, but it seems that the driver for my printer doesnt exist

---

### Post by Amaroq on 2007-09-18
You can use the z600 driver to print from the x1240 apparently. I'm having problems getting cups to find the z600 driver, though I have installed apparently the two packages needed.

---

### Post by Silentheero on 2007-12-15
I also have a x1240 that I am trying to install. 

One idea is to run Windows virtually and set the printer up there.  I may do that if I can't find a way to get the scanner and printer to work. Sucks that Lexmark wont help us beyond [this.]("http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html") It's like giving Windows users the driver SDK's and saying 'have fun boys trying to figure it out'.

---

### Post by Amaroq on 2007-12-15
Okay, I did get it to work in the end. Just google up a guide to installing the z600 driver in cups. You can use that driver to print from your x1240. You just won't get the extra options such as copying or scanning.

I forget how. Just know that there's a file that is generated, I think, that you have to use as the driver when it comes to adding the z600 driver to the list of drivers you can choose from.

---

