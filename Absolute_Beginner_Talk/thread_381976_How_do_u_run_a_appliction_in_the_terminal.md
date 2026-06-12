---
title: "How do u run a appliction in the terminal"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Lt_Spyder on 2007-03-11
Hello everyone

I am new to ubuntu and like most others I am coming from windows os. I am trying to run a file in the terminal from ATI to determine xFre86 version of linux. I am getting the following. any help would be greatly appreciated. just in case it helps I am trying to install the driver for my ATI 9800 radeon pro vc.

spyder@spyder-desktop:~$ dir
Desktop  Examples
spyder@spyder-desktop:~$ cd Desktop
spyder@spyder-desktop:~/Desktop$ dir
check.sh
spyder@spyder-desktop:~/Desktop$ sh ./check.sh
-e =====================================================================
-e  ATI Technologies 
-e =====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

spyder@spyder-desktop:~/Desktop$ ./check.sh
=====================================================================
 ATI Technologies 
=====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

spyder@spyder-desktop:~/Desktop$



Thanks again:)

---

### Post by aysiu on 2007-03-11
Have you tried this? ```
sudo  sh ./check.sh
``` More details here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Lt_Spyder on 2007-03-11
spyder@spyder-desktop:~/Desktop$ sudo sh ./check.sh
Password:
-e =====================================================================
-e  ATI Technologies 
-e =====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

spyder@spyder-desktop:~/Desktop$ sudo sh ./check.sh
-e =====================================================================
-e  ATI Technologies 
-e =====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

spyder@spyder-desktop:~/Desktop$ 


Im not sure what is going wrong, any help would be great

---

### Post by aysiu on 2007-03-11
Maybe it's not working because the script is looking for XFree86, and Ubuntu users Xorg?

---

