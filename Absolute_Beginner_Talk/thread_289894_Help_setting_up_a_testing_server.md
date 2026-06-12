---
title: "Help setting up a testing server"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by smQQkin on 2006-10-31
I need some help or guidance finishing setting up my "testing" server. I will only be using this to learn Linux/Ubuntu as well as the "LAMP" features.

This is what I have installed so far Ubuntu 6.10, LAMP, GNMOME Desktop. I have configured both the user and root settings and password.

This is where I am stuck.

When I login to my Window$ machine, I can see my "Ubuntu Server" thru my network places. If I click on the icon in windows, it brings up the login screen. I am asked to enter my user name and password. I try do this but it keeps failing. Am I missing something? ](*,) 

I just want to be able to add files to the var/www on the Ubuntu machine, and use Dreamweaver on my Window$ machine to test the functionality of them.

Can anyone help me out. I have read some other posts about setting up Webmin and SWAT and some others. But not sure on configuration or even if I need these to access the "testing" server.

Any help or input would be appreaciated. Thanks

---

### Post by bsussman on 2006-10-31
I assume that dreamweaver uses ftp to upload files so you would need to install an ftp server on your lamp system if you need to exactly reproduce the process.

If you do not need to be that exact, sharing through samba would allow you to use win smb to map /var/www

Although webmin is a very nice tool, I do not see it as essential for your stated goals.  Administering mysql is great through phpmyadmin, apache needs very little and commandline on ubunty or throught putty from the windows side should be sufficient.

---

