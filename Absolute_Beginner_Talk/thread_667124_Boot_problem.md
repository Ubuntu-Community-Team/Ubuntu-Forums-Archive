---
title: "Boot problem"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by kalya_kvs on 2008-01-14
Hi,

I am new Ubuntu. I have installed Ubunut in Laptop. It takes log time to boot or It take long time to show desktop. It is dual boot system I am not able to change the boot timing option. It is just 10 seconds. I want to make it 30 seconds.

Please somebody help me. I really love to use Ubuntu.

Thanks in advance.

Regards,
Krish

---

### Post by tangibleorange on 2008-01-14
Do you mean you want to change the default countdown timer in the GRUB menu?

If so, type this in a shell to bring up your menu.lst file::

> sudo gedit /boot/grub/menu.lst

go to the top of the file and find the line (line 19) that says something like:

"timeout                 10"

simply change the 10 to 30 (or whatever you want the time to be in seconds).

Hope this helps!

---

### Post by kalya_kvs on 2008-01-14
Hi Thanks a lot. It worked.

Dd you know what is causing problem in bringing by desktop. It take around 10-15 mins to show desktop after I boot.
Everytime I have to wait long time before the desktop appears.

Krish

---

### Post by swoll1980 on 2008-01-14
also you can install start up manager this will give you a graphical way to change all your grub settings

---

### Post by kalya_kvs on 2008-01-14
I have Toshiba Tecra A4. Memory of 1.5bg and harddisk 160GB, 1.6ghz processor. XP pro works properly.

Thanks

Krish

---

### Post by Jeffrey.Lee.Li on 2008-01-14
Yeah, if ubuntu is installed after Windows (XP for instance), by default ubuntu will take over the booting control with GRUB that uses menu.lst in /boot/grub/, which means at the same time the file boot.ini under C:/ in put to inactive status. So it's no use change timeout option of boot.ini, but the menu.lst.

Good luck:)

---

### Post by LeAstrale on 2008-01-14
open terminal and write the following:
>  sudo gedit /boot/menu.lst 

somewhere down the document it says:
> 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

now im not sure if its the timer there you want to change.
the timer above is when not showing grub menu (when you have to push escape to enter grub menu)

to remove the feature of pushing escape you have to comment out the hiddenmenu by writing an # in front of it.

---

### Post by kalya_kvs on 2008-01-14
Hi 

Can any body help in solving the problem. Why Ubuntu is taking long time to Boot up. When I select Ubuntu generic option. It takes 10-15 mins for desktop to appear. 

I am using Toshiba Tecra A4 loptop. 1.5 gb ram. 160 gb hdd. Dual boot.
Xp pro. 1.6 ghz intel.

Please can any body assists.

Thanks

Krish

---

### Post by Sef on 2008-01-14
1) What is your graphics card?

2) Do you have any messages come up while it boots up?

---

### Post by sailor2001 on 2008-01-14
check your sessions under system and uncheck processes you don't think you need in your start-up menu

---

### Post by dstew on 2008-01-14
Sometimes a long boot-up time is due to  TCP/IP detection problems. Sometimes the IPv6 module is causing the delay. It can be de-activated if you don't need it. See [this]("http://ubuntuforums.org/showthread.php?t=432039").

---

