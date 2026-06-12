---
title: "EasyUbuntu problem"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by comradexiactura on 2006-11-27
Hey all. I just installed EasyUbuntu and am having a problem. I tryed to open easy ubuntu and i get an error. 
Error: Unable to determine desktop environment, falling back to gksudo

so then i tryed: sudo easyubuntu -v
and i got this error,
Error: Unable to determine desktop environment, falling back to gksudo
python: can't open file './easyubuntu.in': [Errno 2] No such file or directory
 can any one help me with this? Thanks in advance.

---

### Post by ziffel on 2006-11-27
I had problems with EasyUbuntu as well. When I click on it from Applications/System Tools, nothing happens at all ... at least not visibly. I ended up going with Automatix2 instead.

---

### Post by comradexiactura on 2006-11-27
yea thats pretty mush the same thing that happens to me so i tryed opening it through the terminal. I really want to fix this problem but if i cant ill switch to something else.

---

### Post by drkkbn on 2006-11-27
Hi I am also new on ubuntu too. I had problems with easyubuntu but I managed to solve them by downloading from the console here is the link to how to hope it helps: 

[http://easyubuntu.freecontrib.org/HtmlDocs/ch02.html](http://easyubuntu.freecontrib.org/HtmlDocs/ch02.html)

PS: just one of the drivers for nvidia i guess wouldn't work for me

---

### Post by STREETURCHINE on 2006-11-27
hi easyubuntu has been having some problems for a while now ,
i would suggest installing automatix2 it works.

[http://www.getautomatix.com](http://www.getautomatix.com).

it will install all your codecs and stuff for you. :-D

---

### Post by comradexiactura on 2006-11-27
i went ahead and installed automatix2 it installed easily and is running fine . i installed the multimedia codecs but for some reason now all my videos are really poor quality any suggestions on what codecs i should use?

---

### Post by STREETURCHINE on 2006-11-27
it seems you may have a resolution problem.
you could try(applications>accesories>terminal)
   sudo cp /etc/x11/xorg.conf/etc/x11/xorg.conf-backup
this will back up your xorg just in case.

        sudo dpkg-reconfigure xserver-xorg
  you can then restart x by  ctrl+alt+backspace
 and try to adjust the resolution but read each question carefully
 sorry after this i am out of my depth but i hope this helps
     (if you still have trouble repost under resolution and some one with that knowledge will help)

---

