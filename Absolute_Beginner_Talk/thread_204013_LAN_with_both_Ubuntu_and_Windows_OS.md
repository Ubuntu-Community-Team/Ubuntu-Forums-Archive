---
title: "LAN with both Ubuntu and Windows OS ?"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by MrPacane on 2006-06-26
Hi everyone,

At home I have a LAN that connects my computer (Ubuntu OS) with some other Windows PCs. Everything works fine except one thing : Windows PCs cannot see that my computer is connected to the same LAN.

So, is there a way to make my computer appear in the "Favorite Networks" of Windows PCs ?

Thanks.
MrPacane

---

### Post by GTvulse on 2006-06-26
You need to install samba and publish the directories you want other machines to see (seach the how-to subforum for tips and tricks).

---

### Post by UbieWan on 2006-06-26
MrPacane

You need to run Synaptic and search samba and swat. Install the samba and swat packages (just select Samba and it will automatically install the dependencies like Samba-Common) then check Swat. After they are installed you can run Swat in your Firefox browser by typing [http://localhost:901/](http://localhost:901/) This makes your computer a "Windows" server - BookMark it so you don't have to remember the port. Presently it is only a Windows client and that is why they cannot see you. The entire process may seem daunting, there is a really good book available here: 

[http://www.amazon.com/gp/product/1931836396/qid=1151333068/sr=1-2/ref=sr_1_2/002-3459297-8451213?s=books&v=glance&n=283155](http://www.amazon.com/gp/product/1931836396/qid=1151333068/sr=1-2/ref=sr_1_2/002-3459297-8451213?s=books&v=glance&n=283155)

Basically all you should do is make a share and then they will see you, file permissions, authentication etc are a different subject but this will get you started.

---

### Post by MrPacane on 2006-06-26
I installed samba and swat but when I try to access to [http://localhost:901/](http://localhost:901/) with Firefox, it says that the page cannot be found...

Any ideas?

---

### Post by nalmeth on 2006-06-26
Just browse to the directory you want to share in your file browser, right-click the folder, and hit Share or Shared, whichever is there.

It will then open the samba config where you activate sharing with MSHOME.

I think this config can be found somewhere in SYSTEM --> ADMINISTRATION too

---

### Post by MrPacane on 2006-06-26
Ok thanks... it almost worked... hehe

And how can I share my files with another workgroup than MSHOME?

---

### Post by nalmeth on 2006-06-27
Don't know, MSHOME is all I have experience with.
Sorry!

---

### Post by ProjectGod on 2006-06-27
i think all you need to do is change your network configuration on your linux machine so that it joins whatever workgroup you want it to. like a domain i think you can only be joined to one domain / workgroup at a time. so if you want to rejoin for example workgroup A you have to re enter that setting on your linux... same thing applies to MS OSes... 

one thing i noticed though was that with MS all you need is for two hosts to be in the same IP scheme on a physically connected LAN. there are ways to bypass the workgroup settings so that they (both hosts) don't necessarily have to be on the same work group to share resources and access each other.

within a MS domain environment its obviously not as "loose". when you've got the LAN set up... if you want to access shared resources on another host all you need to do (on windows xp / 2k) is do a start and run and enter the DNS name of the host... e.g. \\computer2\ ...assuming you have a local host file that has been edited to map specific IPs to host names... C:\winnt\system32\drivers\etc\host.

thing i found also with sharing resources between linux and windows... "workgroup" environment is you need not be in the same workgroup for two hosts to share resources. ... just like a window to window resouces sharing...  but something you DO need in a purely windows environment is you need the same local USER ACCOUNT with same PASSWORD on each window machine to access resources... between windows and linux all you need to configure is a SAMBA user and PASSWORD.

---

### Post by it.henrik on 2006-06-29
You can set your workgroup settings etc for your shares in ubuntu here. 
System-administration-shared folders
then click preferences and general windows share .. or something similar

---

### Post by MrPacane on 2006-06-29
Ok, thanks everyone!

I found it... I just had to edit the workgroup in Samba's configuration file (/etc/samba/smf.conf). It works super well O:) !

---

