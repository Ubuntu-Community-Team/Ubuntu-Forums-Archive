---
title: "README / INSTALL Files"
date: 2005-08-14
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-08-14
OK, this is not even a LInux newbie question, this is altogether computer illiterate question.
When opening a directory how does one then further open and read those README files etc. 
Like /etc/package name. I then cd package and do 'ls' to find a whole bunch of files. 

thank you,

--
sophtpaw

 
 (\ /)                                                                                                                                                                                                                                        
(O.o)                                                                                                                                               
(> <)
                                                                                                                                         

This is Bunny. Copy Bunny into your signature to help him on his way to world domination.

---

### Post by nad on 2005-08-14
The cat command (concatenate) will spit out the entire contents of the file to your display (including binary files).

Use the less command for more control. This will give you one screenful at a time with the ability to scroll with the arrow and page keys ( q to quit ).

There are several more utilities that are useful. You will learn them in time, as well as the additional features of cat and less. Read the man pages for any program to learn more about it, man program_name .

---

### Post by aysiu on 2005-08-14
[QUOTE=sophtpaw]OK, this is not even a LInux newbie question, this is altogether computer illiterate question.
When opening a directory how does one then further open and read those README files etc. 
Like /etc/package name. I then cd package and do 'ls' to find a whole bunch of files.[/QUOTE] How about just navigating graphically with Nautilus and Gedit? Go to Places > Home and find the folder. Then, you can just double-click on the README files, and they'll open in Gedit.

---

### Post by sophtpaw on 2005-08-14
[QUOTE=nad]The cat command (concatenate) will spit out the entire contents of the file to your display (including binary files).

Use the less command for more control. This will give you one screenful at a time with the ability to scroll with the arrow and page keys ( q to quit ).

There are several more utilities that are useful. You will learn them in time, as well as the additional features of cat and less. Read the man pages for any program to learn more about it, man program_name .[/QUOTE]

thx Dan,

Thats a relief to now know that one. How or where do i insert the less argument for more control?

--
sophtpaw

---

### Post by nad on 2005-08-14
I'm sorry. I should have given you examples. ( less is a utility, not an argument ).

cat file_name

less file_name

---

### Post by sophtpaw on 2005-08-14
[QUOTE=aysiu]How about just navigating graphically with Nautilus and Gedit? Go to Places > Home and find the folder. Then, you can just double-click on the README files, and they'll open in Gedit.[/QUOTE]

Sigh...
That is just too easy. I thought GNU/Linux was supposed to be hard! 
But it's always easy when you know, so thx for showing me another way.

--
sophtpaw

---

### Post by aysiu on 2005-08-14
[QUOTE=sophtpaw]Sigh...
That is just too easy. I thought GNU/Linux was supposed to be hard! 
But it's always easy when you know, so thx for showing me another way.

--
sophtpaw[/QUOTE] I'll be perfectly honest--a lot of people think anything that uses the command-line is hard, but even if that's the case, you need to use the command-line in Ubuntu only for configuring system files and such. Most of your daily use will be point-and-click. [The Ubuntu Guide](http://www.ubuntuguide.org) has been invaluable as a resource to me in getting Ubuntu up and running. You may find it useful as well. Welcome to the adventure.

---

### Post by sophtpaw on 2005-08-14
[QUOTE=aysiu]I'll be perfectly honest--a lot of people think anything that uses the command-line is hard, but even if that's the case, you need to use the command-line in Ubuntu only for configuring system files and such. Most of your daily use will be point-and-click. [The Ubuntu Guide](http://www.ubuntuguide.org) has been invaluable as a resource to me in getting Ubuntu up and running. You may find it useful as well. Welcome to the adventure.[/QUOTE]


Yes, i'm enjoying the adventure. Whose Desktop? Mine! is certainly ready for it  ;-) 
Aswell as ubuntuguide the people in this forum have been invaluable too. After leaving Microshaft Winblows, SuSE was my first destination of refuge, but i have come to prefer debian over rpm's. Synaptic was the killerblow which swayed me. I would like to, when i get another hard drive, run Debian's Sarge as my stable mother distro and have Ubuntu to learn and experiment with. It's great everytime a little extra piece comes together and i learn another phrase in command line.

Enjoy

--
sophtpaw

---

