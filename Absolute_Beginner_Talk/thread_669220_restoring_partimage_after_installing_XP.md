---
title: "restoring partimage after installing XP"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-01-16
Hi, this is a bit complicated.. I hope I can get some help.. 

I was using Ubuntu 7.10 alone on my laptop..   I made a backup of root partition and home partition. Then, I needed to use XP so I formated the harddisk and installed XP. 

After that, I installed ubuntu .. and here I am writing a question. Now I can dualboot the system ..  my question is can I restore root and home from the backup I made previously. 

When I made a backup, 

/dev/sda1 --> root
/dev/sda2 --> home
/dev/sda3 ---> just a storage 
/dev/sda4 --> swap 

Now.. .
/dev/sda1 --> winxp is installed
/dev/sda2 --> storage  (it's just a partition) NTFS 
/dev/sda3 --> root
/dev/sda4 --> extended
/dev/sda5 --> home
/dev/sda6 --> swap


I am afraid that when I restore root and home from the backup, I might damage or change Master Boot Record. I don't want to reinstall system again... (been doing so many times) 
 
Is there any way I can restore the system from the backup files of Partimage and still keep the dual-boot system???

---

### Post by Pevichaey5 on 2008-01-16
personally, i wouldn't restore the root image, because grub lives somewhere in there, and it will be rewritten giving you what you had before

i have doubts that it will even let you rewrite the root partition, but i'd just restore your /home/ stuff, and keep a dual boot

---

### Post by nem75 on 2008-01-16
Specifically it's the /boot/grub/menu.lst file from the backups which would contain the wrong partition identifiers.

Although you could work around that it's easier to just proceed as Xero suggested.

---

### Post by taekr on 2008-01-16
> **thexero said:**
> personally, i wouldn't restore the root image, because grub lives somewhere in there, and it will be rewritten giving you what you had before

i have doubts that it will even let you rewrite the root partition, but i'd just restore your /home/ stuff, and keep a dual boot

Thanks for the reply..

One more question. 

What happens when I restore only Home? 

If I install all the programs I was using, all the settings for programs will be restored? 

I set up keyboard shortcuts...  installed crossover.. (office 2003 installed)..  
and so on .. 

when is the best time to restore home??  after installing all the programs I was using? or before ?  

I had 'windows programs' folder on the menu...  will all these things be back??

---

