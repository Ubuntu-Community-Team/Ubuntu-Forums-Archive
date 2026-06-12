---
title: "Need to get FTP server working on my Ubuntu server box"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by spdorsey on 2006-09-06
Hello

  I just installed Ubuntu server 6.06.1 (with PHP and MySQL) on an old G4 so that I can use it as a simple web server in my cube. Apparently, I cannot FTP to it from my G5. 

  Is there something I can do to get FTP working on this box? 

  Simple answers, please. And this box has no internet access, we're behind a proxy and I can;t get that working either.

Thanks,

-----------------S

---

### Post by tomBorgia on 2006-09-06
Hiya, you'll need to install vsftpd (very secure ftp deamon) - you can use synaptic :-D 
the config file you'll need to look at are /etc/vsftpd.conf (its pretty self explanitory, its a well-commented file)
you start the ftp daemon from a terminal simply with:

vsftpd

if you have problems and vsftpd is running then its probably a firewall issue...

---

### Post by caiman64 on 2006-09-06
Hi,... try this on the terminal window with your ubunto server cd in the drive:

sudo apt-get install vsftpd

This installs the "Very Secure FTP Daemon"... the configuration file is /etc/vsftpd.conf all the options for this file are explained using this command: man vsftpd.conf

I have it running... but I am not being to upload or download files... for now... I´ll keep reading... if you find something tell me via this thread

I am trying to upload/download files, create/erase directories, directly into the /var/www

regards 
carlos](*,)

---

### Post by spdorsey on 2006-09-06
I'd like to do the same thing. I want some access to specific directories on the box without having to type directory paths all day using scp. a Drag & drop solution would be sooooo much faster!

  When I type 

sudo apt-get install vsftpd

  it asks for my password. When I type that, it says:

Extra junk at end of file

  ????? please help!

---------------S

---

### Post by tomBorgia on 2006-09-06
Hi Carlos, can you upload/download to other directories? if you log in as your user account I would have thought that by default you should be able to write to your /home/carlos directory - I think you'd need to add your user to the www-data group to be able to write to /var/www... if you can't write at all then its probably a firewall issue...

---

