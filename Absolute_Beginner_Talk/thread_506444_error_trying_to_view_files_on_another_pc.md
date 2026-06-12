---
title: "error trying to view files on another pc"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by mewisemagic on 2007-07-21
yes, i'm a neewbie lol! i can see my other xp m/c's on my network, but when i click on them i get an error that say's 

"The filename "COBRA260-NKBT8X" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system."

"Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file." 

can someone walk me though this step by step,cause i'm clueless about any type of command/terminal stuff? i mostly just browse the web ,but some times i need to move files to other pc's. the samba network program seemed to be  allredy setup on the knoppix live cd i sometimes run and didn't have to do anything. thanks

---

### Post by koganinja89 on 2007-07-21
ok. you need to research how to setup (if you don't already know how) an ftp on your other computer and NOT use Samba which is what SMB is.

It willl be easier to setup maintain and use on your linux computer because everything you do is on the PC (I assume)

then when you go into your web browser you just type: "ftp://USERNAME:PASSWORD@IP_OF_THE_FTP_COMPUTER/"

and access files, if you can't access some files make sure to add them into the shared folders of your ftp.

---

### Post by koganinja89 on 2007-07-21
you know what... just buy a thumb drive. they are lik 20$ for a 2 Gig.:):popcorn::lolflag:

---

### Post by mewisemagic on 2007-07-21
anybody else with any tips.i really don't want to mess with my xp m/c's

---

### Post by mewisemagic on 2007-07-22
hey,i still need some help? thanks

---

### Post by mewisemagic on 2007-07-22
here is a screenshot of my problem
[IMG][IMG]http://i56.photobucket.com/albums/g182/mewisemagic_2006/Screenshot.png[/IMG][/IMG]

---

### Post by BDNiner on 2007-10-31
I am having the same problem connecting to a share. Setting up ftp would take some time and i would have to talk to the engineer that maintains that server. Are there any other ideas on how to fix this?

---

