---
title: "Wine"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by harts12 on 2006-10-01
I just installed uduntu on my Inspiron and I am just about to switch my family's pc over. I used wine on Myst (as a test case) and it worked pefectly. My problem comes in finding the files so I can put make desktop link that will wine my windows .exe's. Any suggestions? because it certainly isn't in C:Program Files\\Myst\\... If I wine the autorun of Myst it works, but I still can't find where it was installed. Before I stick my less patient family members on ubuntu I would like to be able to make their Windows progams easy to use. Any suggestions at all would be helpful...

---

### Post by adwait on 2006-10-01
Umm not quite sure what you are tryinh to say, but if you are askin where the program that you instaleld through wine go installed, it most probably got installed in /home/<you>/.wine/dosdevices/...

---

### Post by harts12 on 2006-10-01
Hey, thanks, that is what I was trying to get at. The rest I should be able to manage myself... Thanks again!

---

### Post by harts12 on 2006-10-02
One more question, how do I get around this:
 [email]harttop@Harttop:~/.wine[/email]/dosdevices/c:$ cd program files
bash: cd: program: No such file or directory
 I can't go from c: to program files because of the two words and I don't know enough to get around that simple problem....

---

### Post by CatKiller on 2006-10-02
You can either ```
cd "Program Files"
```or you can ```
cd Program\ Files
``` with the space being "escaped" by the \. Note the capital P and remember that you can use Tab to complete paths and filenames.

---

