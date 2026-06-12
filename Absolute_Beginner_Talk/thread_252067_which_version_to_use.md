---
title: "which version to use?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by tommy2c on 2006-09-06
I have a pIII with only 128 MB of memory.  I have warty on it now but would like to update to newest release.  Is 128 MB enough?

Also, another question.  How do I access root privilage in worty?  the sudo command does not seem to do it for me.  When I installed, program clearly found my internet connection but will not connect now.  I have tried to add my IP to network connection but can't without admin privilage.

Thank you for your help,

tommy2c

---

### Post by Hexidigital on 2006-09-06
If you only have 128MB RAM, that will not be enough for Breezy or Dapper.  If I remember correctly, the minimum required for Ubuntu is 192 MB, and Kubuntu is 256.

Also, you should not "unlock" root.  To access root, use SUDO.  

For more information on SUDO, visit wiki.ubuntu.com.

---

### Post by xpod on 2006-09-06
Try xubunto alternate version.....Ive got kubunto running on 192mb of ram but you might need to take a further step down in size to X........Alternate version will save probable headaches with install

EDIT:im sure kubunto is lighter than Ubunto is it not?hence reqires less

---

### Post by taurus on 2006-09-06
Definitely go with the xubuntu version, using XFce4 as your window manager.  I don't recommand you run Gnome (ubuntu) or KDE (kubuntu) with the amount of RAM that you have.  You can make it run a little faster with the server install and use fluxbox as your window manager...

---

### Post by I922sParkCir on 2006-09-06
Xubuntu should do the job. There is also an unofficial fork called [Fluxbuntu]("http://www.fluxbuntu.org/"). It is very light weight and made for legacy machines. Also if *sudo* doesn't do it for you, you can enable su (permanent root permission) by *sudo su*, or if your want a graphical root login go to System --> Administration --> Login Window --> Security --> *check* Allow local system administrator login , and login as root. I do not recommend that you run as root though.

---

### Post by Druidor on 2006-09-06
I am currentyl runnin 6.06LTS on my PIII 450MHz machine with 128Mb of memory

Yes it runs a bit slow but no problems especially as it is only being used for testing & P2P client atm.

---

