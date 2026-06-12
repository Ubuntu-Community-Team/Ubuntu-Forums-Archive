---
title: "How I fixed my java jre elua adept problems with kubuntu 6.10"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by jeffeb3 on 2006-11-12
Oh how frustrating, I installed Kubuntu, learned it's sudo routines, and then was rippin' through the things I wanted to install.  I got to jave, specifically, sun-java5-jre.  Then it all went wrong, I was using the Graphical User Interface KDE -> System -> Adept Manager Mange Packages, I enabled the universe/multiverse repositories, and I searched, found and attempted to install sun-java5-jre, and sun-java5-jre-bin.  During the install, however, it stuck, I clicked on the details, and you sould see the EULA, but you couldn't accept it.

SO, I killed, it.  Then rebooted, several times, and I kept getting the message about having more than one adept program running, so I searched the forums and found that a lot of people had this same problem, the solution:

sudo dpkg --configure -a

Then I can get back into the adept stuff, but when I try to install anything, it lets me know I need to install java first, when I try Java, I get the same EULA problem.  I searched the forums, and not one of the threads I read on the subject included any more details.  So, here's what I did to fix it, I ran it from the command line!  it worked.  I used this:

sudo apt-get install sun-java5-jre

That will only work if you already are clear of the adept program conflict, but it let me install java, and now I can install like a crazy fool again!

Sorry for the verbose post, and I don't know much about it, so I may have left out what to do next for Java to work nice with Firefox, but this information wasn't anywhere else in this forum.

---

### Post by ThrobbingBrain66 on 2006-11-12
i discovered a few weeks ago that hitting the tab key when that happens refocuses the terminal so you CAN accept the EULA

---

### Post by Muis24 on 2006-11-19
I had the same problem, but I had it before when I tried to install the VMware player. It also shows an EULA with an <OK> button you cannot click. I also tried oressing the tab key several times but it didn't help.

---

