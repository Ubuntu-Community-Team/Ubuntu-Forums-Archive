---
title: "help with networking plzplz"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by mothafukaa on 2006-09-27
ok, so i have my ubuntu machine and my windows machine
(FIRST time using linux, so detailed help would be good)
and i want to network those machines... how do i do this?
and i was wondering...
can i transfer files from my windows pc to my linux pc?
if so, how?

 (im on 5.10, but those forums are dead, so i took it here, sorry)

---

### Post by Iowan on 2006-09-27
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=peer](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=peer)
See if anything in here helps.

---

### Post by mothafukaa on 2006-09-27
> **Iowan said:**
> [http://www.ubuntuforums.org/showthread.php?t=202605&highlight=peer](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=peer)
See if anything in here helps.
im COMPLETELY noob with linux, and i cant get all this to work, the only thing i could do is pretty much install samba, thats it, is there an easier way?

---

### Post by ashokpappu on 2006-09-27
do u want to transfer files between windows and linux or do u want to map linux machine from your windows machine as G frive or f drove?

if you want to transfer files u can do simple ftp or even better ssh

to install ssh run this command 
 sudo apt-get install ssh

go to windows machine and download filezilla and simply ssh to linux machine and copy files.  

if u want to map the network drive u may have to install samba.

---

### Post by mothafukaa on 2006-09-27
> **ashokpappu said:**
> do u want to transfer files between windows and linux or do u want to map linux machine from your windows machine as G frive or f drove?

if you want to transfer files u can do simple ftp or even better ssh

to install ssh run this command 
 sudo apt-get install ssh

go to windows machine and download filezilla and simply ssh to linux machine and copy files.  

if u want to map the network drive u may have to install samba.
what do i do with filezilla?
i dont know what to do with it...
help

---

### Post by ashokpappu on 2006-09-27
file zilla is a simple ftp/ssh client.  just install it on windows and double click on the short cut.  it will open a window enter the ip address of ubuntu machine userid and password.  make sure u select from the drop down the protocol ssh and click connect.  u will be able to see your home directory on  ubuntu.  just drag and drop files.  just do google search for filezilla if u want to download it.

---

### Post by mothafukaa on 2006-09-27
> **ashokpappu said:**
> file zilla is a simple ftp/ssh client.  just install it on windows and double click on the short cut.  it will open a window enter the ip address of ubuntu machine userid and password.  make sure u select from the drop down the protocol ssh and click connect.  u will be able to see your home directory on  ubuntu.  just drag and drop files.  just do google search for filezilla if u want to download it.
ok, i have filezilla... but where do i input this info??
[http://img95.imageshack.us/img95/3746/untitleddg1.jpg](http://img95.imageshack.us/img95/3746/untitleddg1.jpg)
where do i do itt?

---

### Post by ashokpappu on 2006-09-27
Address is where u enter the ip address user name  is your ubuntu login name and pasword is your password. and try the menus make sure u select ssh or it will not work and hit enter key.  u should be able to get to linux machine.

---

### Post by mothafukaa on 2006-09-27
> **ashokpappu said:**
> Address is where u enter the ip address user name  is your ubuntu login name and pasword is your password. and try the menus make sure u select ssh or it will not work and hit enter key.  u should be able to get to linux machine.
what did i do wrong?
[http://img142.imageshack.us/img142/9850/untitledfp0.jpg](http://img142.imageshack.us/img142/9850/untitledfp0.jpg)

---

### Post by ashokpappu on 2006-09-27
is the ip address correct?  are u able to ping the ubuntu machine. did u select the ssh option from filezilla?

---

### Post by mothafukaa on 2006-09-27
> **ashokpappu said:**
> is the ip address correct?  are u able to ping the ubuntu machine. did u select the ssh option from filezilla?
wheres the SSH option?
[http://img99.imageshack.us/img99/8997/untitleddh3.jpg](http://img99.imageshack.us/img99/8997/untitleddh3.jpg)

---

### Post by mothafukaa on 2006-09-27
> **ashokpappu said:**
> is the ip address correct?  are u able to ping the ubuntu machine. did u select the ssh option from filezilla?
[http://img99.imageshack.us/img99/8997/untitleddh3.jpg](http://img99.imageshack.us/img99/8997/untitleddh3.jpg)
where is the ssh oiption?

---

### Post by ashokpappu on 2006-09-27
i really cannot see all the menus  try different app called winscp.  google for winscp and it will straight do ssh so u dont have to mess with any settings.  it will ask for hostname enter the ip enter the user id and passworrd  that should be it.

---

### Post by mothafukaa on 2006-09-27
you are a god among men, i truly thank you

---

### Post by mothafukaa on 2006-09-27
im currently transferring like 3 gigs worth of media as we speak, THANK YOU

---

### Post by ashokpappu on 2006-09-27
3 gigs will take a long time because u are encrypting and sending it across the wire and decrypting it.  ftp would have been better option but if speed is not an issue ssh works great.

---

### Post by mothafukaa on 2006-09-27
nope, speed is not an issue, it is fast enough, umm what music formats will play here?
are there any mp3/wma players for linux?

---

### Post by ashokpappu on 2006-09-27
pretty much all.  some of the formats are patented so they dont work out of the box because of patent issues.  install kmplayer,vlc,xine and u should be able to play all of them. of u want to run DVD's u need ogle witt libdvdcss.

---

