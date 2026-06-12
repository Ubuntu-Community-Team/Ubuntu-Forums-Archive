---
title: "Ubuntu unicode problem"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by eskarthic on 2007-07-23
Hi,
I am new to this ubuntu. I have HP pavilion AMD64X2 processor. I have installed the ubuntu 7.04 in my laptop.  I am not able to read tamil unicode sites. Please see the attachment snapshot. 
Also, anybody can please help me in setting up the flash plugin for the dual core?
Thanks in advance.

I tried the flash options given in the ubuntu forums. didn't work. I tried installing opera. get package broken message for any installation. Any clue??

Please help.

Thanks,
Karthic

---

### Post by Kilz on 2007-07-23
Did you install the 64bit version of Ubuntu? if so please visit one of the links in my signature to get flash working.

---

### Post by eskarthic on 2007-07-23
yup, I installed the 64bit version ubuntu.

I always get the following error when I run the command
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32

Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ia32-libs-gtk
E: Package ia32-libs has no installation candidate

please help.

-regards,
Karthic

---

### Post by Kilz on 2007-07-23
> **eskarthic said:**
> yup, I installed the 64bit version ubuntu.

I always get the following error when I run the command
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32

Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ia32-libs-gtk
E: Package ia32-libs has no installation candidate

please help.

-regards,
Karthic

Its possible you need to enable the multiverse and universe repositories. [Take a look here on how to do that.]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")

---

### Post by expatCM on 2007-07-23
For the Tamil language support ....  have you enabled Tamil support in System / Administration / Languages / Tamil ?

---

### Post by Kilz on 2007-07-23
Also please, if you have problems with the 64bit version. [You might want to post in the 64bit section]("http://ubuntuforums.org/forumdisplay.php?f=134"). We 64bit users have specific problems that 64bit users know how to solve.

---

