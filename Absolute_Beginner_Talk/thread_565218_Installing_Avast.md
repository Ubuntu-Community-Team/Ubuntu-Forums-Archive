---
title: "Installing Avast"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by craniumsoftener on 2007-10-02
Hi everybody,

I just installed Ubuntu last night.  I wanted to try installing third party software, so I decided to start with Avast's antivirus program for Linux. 

I downloaded the Debian file ([http://download54.avast.com/files/linux/avast4workstation_1.0.8-2_i386.deb](http://download54.avast.com/files/linux/avast4workstation_1.0.8-2_i386.deb)), double-clicked it and after a few moments it said it was installed.  The problem is, I opened up my Add/Remove Applications and it was nowhere to be seen.  Furthermore, it never asked me for my registration number.  I'm thinking I did something else besides install it, but I'm not sure what.

Does anybody know how to install it?  Does anybody know what went wrong?

Thanks in advance :)

---

### Post by wolfen69 on 2007-10-02
go to system>preferences>main menu. you can add/remove programs to your menu list. or to start any program, open terminal and simply type in the name and hit enter.

---

### Post by craniumsoftener on 2007-10-02
Thanks for your help, but I'm afraid I don't get it.  I got as far as this: system>preferences>main menu, but from there I didn't see how to add/remove programs.   Should it be obvious?  I tinkered around but to no avail.  

Just wondering, is your method any different than going to Add/Remove Applications under Applications?

Thanks

---

### Post by wolfen69 on 2007-10-02
when you go to system>preferences>main menu, you are not installing anything, you are just adding or removing things from your menus. highlight system tools (on the left) then on the right you will see a list of programs that are available. look for avast and put a checkmark to add it to system tools. i only used system tools as an example. it could be under something else. btw, why do you want antivirus in linux?

---

### Post by craniumsoftener on 2007-10-02
Hmmm, seems like my reply didn't show up.  I'll try again.  If you get another reply that is similar, you know why.

Anyway, thanks for your help.  I believe I understand you, but it is still a no-go.  I opened up the main menu, as you said.  I scoured the left side and never found Avast.  Is this normal?  I know that Linux isn't supposed to be the sort of OS that holds your hand, like Windows 'tries' to do, but still, I expected to install something and have it be in the menu without problems.

To answer your question, though, I am aware that most people believe there is no need for antivirus softwar on Ubuntu.  Actually, I mostly wanted to download something and install it, just so I could see how the process goes (and because I am still paranoid about viruses, despite Ubuntu's reputation).  I hope it gets easier from here on out.

---

### Post by mali2297 on 2007-10-02
There is a howto about Avast here:
[http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html](http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html)

> 
Applications Menu Setup

For this you need to run a script from the following location

cd /usr/lib/avast4workstation/share/avast/desktop

sudo ./install-desktop-entries.sh install

This will complete the application menu setup.


An alternative is [AVG]("http://www.howtoforge.com/avg_antivirus_ubuntu_feisty"). But you really don't need an AV for Linux.

If you're concerned about safety, avoid downloading programs from the web. Instead use Ubuntu's repositories, i.e., install programs through Add/Remove or Synaptic Package Manager. There are plenty of programs available in the repositories.

---

### Post by SOULRiDER on 2007-10-02
I think theres some stuff you should know.

First of all, Linux is very sexure, you really dont need an anti-virus, believe me.
Check this post about secutiry out: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Also, installing and removing software can be really easy, and it is done ina  different way than in Windows. This link explains how Software Management is done, check it out.
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

Good luck and I hope you like Ubuntu. If you have any questions just ask!

---

