---
title: "Printing Troubles"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-24
Hi, I'm experiencing some troubles, I'm attempting to fix and issue with my HP PSC 1410 only printing blank pages. Some where along the way my printer stopped talking with Ubuntu and now whenever I send something to print it will just sit up in the top right and nothing will happen, like as the printer and ubuntu aren't talking. I've tried removing the printer several times and every reinstall of the printer, ubuntu sees it. How can I get the two talking again??? Also, how could I fix the blank pages printing??

---

### Post by Sethalos on 2007-05-24
I have the same problem, same printer.

Seth

---

### Post by Tumpster on 2007-05-24
Lets hope someone awesome can help us then!! :)

---

### Post by Tumpster on 2007-05-24
Anyone willing to help???

---

### Post by Tumpster on 2007-05-25
At least a hint or two?

---

### Post by Seisen on 2007-05-25
Have you tried restarting cups?

---

### Post by dstew on 2007-05-25
Was your printer working before? What did you change that might have made it stop working? How is your printer connected? What Ubuntu distribution do you have?

Are you using the HP Linux printing tools (hplip), or the open-source driver only?

---

### Post by Tumpster on 2007-05-25
I thought I undid everything I had done, I've restarted CUPS several times, My printer is connected via USB and I'm running Ubunut: 6.06 Dapper.

---

### Post by ramjet_1953 on 2007-05-25
Try this approach:

1: Uninstall your printer

2: Make sure that you have [COLOR="Blue"]python-qt3[/COLOR] installed (it's in the repositories)

3: Run [COLOR="Blue"]hp-toolbox[/COLOR] (HPLIP toolbox is a menu item in [COLOR="Blue"]System>Preferences[/COLOR], but often has to be made visible in the menu, by using [COLOR="Blue"]Preferences>Menu Layout [/COLOR]and making sure the entry has a tick against it)

4: When you run hp-toolbox it will tell you that you do not have a printer installed. Just follow the directions that it gives you and hopefully, all should work.

Regards,
Roger :cool:

---

### Post by Tumpster on 2007-05-26
Ok, their talking again but it's printing off blank pages, how do I fix this? I know I have ink in my black one.....

---

### Post by Tumpster on 2007-05-26
Awesome, got it working, refilled the cartridges as well, all is right with the world and my printer!! :)

---

### Post by warpuck on 2007-08-07
I started out with an Epson r220, which prints well, too well. I let Fiesty decide what to use and every thing worked the first time and all the time. I have used 3 sets of cartridges since February.  So I added a Samsung SCX-4200 and installed the Samsung unified driver, cus Fiesty didn't know what it was.
Now, if you just Control P and let the default printer (Samsung) do its thing, both printers spit out blank paper at the same time. If you click on the printer you want to print from Fiesty prints as it is supposed to. however my darling Michelle just wants to control p and grab her printed pages. she don't want to do no stinking extra clicking! I can assure you her middle name is not Patience.  She called me at work to trouble shoot this issue starting with “ I hate F*&%#~^ computers”. HELP anybody my ears can't take any more.

---

