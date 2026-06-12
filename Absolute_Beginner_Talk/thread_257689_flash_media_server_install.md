---
title: "flash media server install"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by tickles on 2006-09-14
folks,

the install script does some checks for platform compatibility. the easiest solution is to comment out the function calls to exit when the installer discovers that you are not running enterprise linux 3 or 4. i should have thought to do this obvious hack before i posted here. doesn't seem as if i wasted anyone's time...

cheers!

hi,

i see where steffjay successfully installed the FMS. i was not able to get the installer to run without immediately crashing. the output of the install is:

 sudo ./installFMS 

ERROR: Your distribution, unknown, is not supported by this
       Macromedia Flash Media Server installer.


i would love to run FMS on ubuntu and not have a seperate windoze machine running to serve my flash content. today is day one for me of ubuntu. very nice. much better than red hat bloatware. at any rate, any help getting this installed would be great. btw, i am running ubuntu server 6.06 and the version of fms i downloaded was: FMS_2_0_2_r51_linux

cheers,
tickles

---

### Post by jwing on 2006-10-15
create a file named redhat-release under /etc, with the following content:

Red Hat Enterprise Linux ES release 4 (Nahant Update 2)

---

