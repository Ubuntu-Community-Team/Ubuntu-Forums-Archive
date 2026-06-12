---
title: "Printer problems!!"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Dave Walker on 2007-09-19
Hello, just started using Linux & have also got Win XP, which I use for gaming online.
My problem is, my printer only seems to want to print from my Win OS & although it goes through the motions, it wont print diddly in Linux!!!!!!!! Grrrr!
The printer is a small & simple HP Deskjet D1360.
Can anyone help?


:confused:



Cheers,

Dave W.

---

### Post by linuxwizard on 2007-09-19
If this is not what you are looking for post back with more info on problem.


[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by nikoPSK on 2007-09-19
Hey... deskjet you say, I have just the fix! I have an hp deskjet 932C and I couldn't find a driver. Well HPLIP (hp linux imaging an printing system) is just the anwer!

sudo apt-get hplip 

after it's done installing:

sh hplip-2.7.7.run

That shoul configure everything then print a test page!

(make sure you're a root user):)

---

