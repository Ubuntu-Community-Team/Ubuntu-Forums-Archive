---
title: "Exporting emails and address book, calender, etc from Evolution"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by quercusrobur2002 on 2007-01-27
I'm increasingly worrying that I'm going to have to re-install Dapper fom the DVD as I'm not having any luck with my problems here [http://www.ubuntuforums.org/showthread.php?t=347400](http://www.ubuntuforums.org/showthread.php?t=347400)
All my work and files are backed up to a USB drive but I can't work out how to save all my emails, addresses, calender entries, etc from Evolution. I can find an 'import' command but no 'export' to save it all to the USB drive.

Reinstalling Dapper is really last resort stuff, but can't really see I've got a choice if the libc6 issue isn't solved, but it would be good to be able to back up all the Evolution stuff anyway...

---

### Post by gregh on 2007-01-28
You need to take a copy of the whole ~.evolution/ directory. Just zip the lot:

(from your home dir)
tar zcvf my_evolution.tar.gz .evolution/

and then backup the resulting file my_evolution.tar.gz (to usb etc)

after new ubuntu install, go through the evolution first run process, then quit evolution and unzip the my_evolution.tar.gz file into your home dir.

tar zxvf my_evolution.tar.gz

re-launch evolution and you should see all your emails etc.

-Greg

---

### Post by quercusrobur2002 on 2007-01-30
Thats a brilliant help! many thanks, Greg

---

### Post by golem3 on 2007-01-30
The important files to keep are the large files - such as Inbox, Sent Mail, Outbox, etc. Other files, if corrupt or not present, will not affect the files you need to restore.

---

### Post by Healey on 2007-06-24
Hi

I have been using this excellent suggestion by gregh to export all .evolution files to a new system

It has worked flawlessly on two different PC's running dapper and edgy.

I have now installed Feisty and this no longer works !!

It will copy all my emails but will not copy the address book or the calender


Do you know what has changed and if there is a way around it ??

Thanks and regards

Healey

---

### Post by gregh on 2007-06-24
I have not heard of this before, what happens when you restart evolution after un-zipping? Does the evolution "new account" wizard popup?

-Greg

---

### Post by Healey on 2007-06-25
Hi

Many thanks for your reply

No - The wizard does not start - It starts normally except that it has all the email from the un zipping process. What it does not have, is the address book and calender reminders.

I did try deleting the entire contents of .evolution - Then unzipping the file.  The wizard did start that time, but after going through the procedure there was still no address book and calender.

Has the location of the address book changed perhaps ?

Strange dont you think !!!

Regards

healey

---

