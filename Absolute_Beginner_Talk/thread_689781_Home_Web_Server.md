---
title: "Home Web Server"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by drarncruz on 2008-02-06
I am trying to find the best set up for running a webserver from home using ubuntu 7.10 desktop version.  The website will be in php script.  

thanks

---

### Post by ghandi69_ on 2008-02-06
I have setup the same thing on an old machine (800 Mhz 192 MB of ram)

And I followed this setup and had no problems.  Since you are only doing a webpage, you do not have to follow all of it.  You also might want to look up more info on apache, but this will get the basics for you.

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by emarkd on 2008-02-06
Open Synaptic, Click on Edit > Mark packages by Task... and select LAMP server.  That'll get you what you need.

---

### Post by Dr Small on 2008-02-06
Just setup XAMPP, as it is simple to set up and will do everything you want:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

---

### Post by drarncruz on 2008-02-06
Thanks guys for the advice.  I want to set up the server at home to run 3 websites that I developed.  They are currently on host monster and several on godaddy.com.  I just don't know how to "upload" these files to my hp server.  Currently I use filezilla to do this to the commercial web host companies.
I will be developing other websites on my desktop using dreamweaver and I want to upload the site onto my ubuntu server using either the LAMP or XAMPP that you guys suggested.  What is the best setup to do this?  I have filezilla.  Again thanks for your thoughts and advice.

---

### Post by emarkd on 2008-02-06
If you write the files on the same machine you're server runs on, you'll just copy it to the proper directory.  If not, you can transfer the file around your network in any number of ways, ftp, sftp, scp, samba, nfs.  You've got lots of flexibility to find what works for you.

---

### Post by nikoPSK on 2008-02-06
> **Dr Small said:**
> Just setup XAMPP, as it is simple to set up and will do everything you want:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

thanks for the link, now I know too. :)

---

