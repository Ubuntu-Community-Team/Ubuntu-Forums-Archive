---
title: "Installing xampp"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by rwizibuntu on 2007-06-29
I am trying o install xampp on my new ubuntu, I have the tar file in  /rwizinet . 
I have followed the instructions from the xampp site
this is my attempt and result so far in the terminal

rwizinet@rwizinet-desktop:~$ tar xvfz xampp-linux-1.6.2.tar.gz -c /opt
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
rwizinet@rwizinet-desktop:~$ 

please help
thanks

---

### Post by mlentink on 2007-06-29
Why install XAMPP? 
Apache, MySQL, PHP Python, Perl are all in the repo's

---

### Post by rwizibuntu on 2007-06-29
You are very right on that. However I have been working with xampp for the last three years on  windows. I thought it would be an easier option having hit a snug with the LAMP as i will explain below

I did go through the installation of the LAMP as you suggest but 
1- I failed to save the php files in the right folder ie var/www/  so i can not see the files in the browser how can I do that.

2-when i look for [http://localhost](http://localhost) in the browser i get the index of / and when i click on the link provided apache2-default it takes me to a page which says " it works".

How can i proceed from here on  LAMP
thanks

---

### Post by bvanaerde on 2007-06-29
> **rwizibuntu said:**
> tar xvfz xampp-linux-1.6.2.tar.gz -c /opt
I think the command is case sensitive.
so the -c should be -C
Maybe that's the problem...

edit:@mlentink: Why install XAMPP? Because it is VERY easy to install :p
edit2: @mlentink: you need to be sure you have the permissions to write to that folder.

---

