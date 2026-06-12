---
title: "Network Print generates LPR GUI launch"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Busta999 on 2007-01-17
OK I am a major Linux noob..

Setup Ubuntu Dapper
Installed Samsung Printer (CUPS)
Setup Samba
Can access from XP boxes on network disk and printer

Whenever XP box prints to Unbuntu Samsung printer, the Ubuntu box launches an LPR GUI window, If I select OK in this LPR GUI window it prints OK, if I ignore or select cancel the print job dies.

Any ideas on how I can automate printing so I don't always have to go to the back bedroom to approve every print job?

Thanks

M

---

### Post by Busta999 on 2007-01-18
OK so I guess this noob is frying alone with this one.

I must admit having tackled two new OS's at the same time was ambitious but very educational.](*,) 

I worked on Ubuntu and OSX, I can say without a doubt the OSX is much easier friendlier and whole lot more productive.

I did it as an experiment to see if it was possible to break from Windows, it is the Mac.

Ubuntu is not going to be Aunt Mable's computer, it requires too much of it's users. Oh I will master it, I will learn it's quirky little ways, but basically it is a command line interface with some nice graphical stuff on top a bit like Windows v3.00, you can do network sharing but it boy you have to sweat for it, unless you already know your way around a unix CLI.

I am going to have much fun migrating all my Windows PCs to Linux, but it will be quite some time before I put my wife on one, it would be too embarassing to explain how to get basic chores done. I will probably put her ona Mac too and use the Linux as back office functions.

Anyway back to work trying to automate network printing using a Linux box as a print server.....:-k

---

### Post by davysouthernboy on 2008-02-27
The original LPR is renamed and replaced by the installation program.  The original LPR program is now called /usr/bin/lpr.orig .  If you use that in place of the lpr command, the gui will not pop up and you can automate your printing again.  Good luck. Davie Overman.

---

