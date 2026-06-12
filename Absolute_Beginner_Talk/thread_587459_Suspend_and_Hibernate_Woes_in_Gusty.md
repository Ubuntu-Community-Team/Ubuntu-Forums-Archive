---
title: "Suspend and Hibernate Woes in Gusty"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by JacobRogers on 2007-10-22
:(

I was hoping that Gusty would allow my laptop to suspend and hibernate properly.  But it can't do either one.  It can't even hibernate any more like it used to do with Feisty.  How do I fix this...?

:confused:

---

### Post by bbqsandwich on 2007-10-22
I'm an Ubuntu newb, but from looking around the forums this seems to be pretty common.

apparently some people are modifying their acpi-support settings and having some success; if you search the forums you'll find posts about it.

that has not yet worked for me so here is what I did to get hibernate working on my Acer Aspire 3680 laptop. this only worked for hibernate for me, not suspend.

1. I got uswsusp, sudo apt-get install uswsusp

2. I followed these steps to set up the proper swap for uswsusp to use, except i didn't do the first part about disabling ATI drivers (I don't have ATI):
[http://ubuntuforums.org/showpost.php?p=3573566&postcount=12](http://ubuntuforums.org/showpost.php?p=3573566&postcount=12)

3. then these steps:
[http://ubuntuforums.org/showpost.php?p=2830268&postcount=1](http://ubuntuforums.org/showpost.php?p=2830268&postcount=1)

but apparently s2ram isn't available anymore (??) so i just did the steps to fix hibernate (s2disk) and it works. Only problem is i don't have sound anymore after it resumes; i have to restart to get sound back.

hopefully either (a) that will work for you, or (b) someone else will suggest something else that will work even better! good luck!

---

### Post by Mait on 2007-10-22
Are you using ATI restricted driver(fglrx)? Then, check this bug report.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)

---

### Post by JacobRogers on 2007-10-22
Nvidia

---

