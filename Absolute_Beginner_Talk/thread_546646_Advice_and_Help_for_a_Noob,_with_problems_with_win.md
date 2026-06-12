---
title: "Advice and Help for a Noob, with problems with windows migration"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by qsr.nrwn on 2007-09-09
This will be a [not so] long post

For some reason - I'm building a system to migrate a so-old-Windows-based (it runs even in Win3.x, I swear) medical record management program - into a web-based one, because it is so important for my father [he is a physician too] and me, and because of security and cost reasons we are considering migrating it into a web-based application, hosted in a dedicated linux box

Let me set some ground rules
1. The program is running on a Windows-XP SP1 computer
2. It has a weird database format, I have almost used every database program to open it and have no success
3. Commands are accesible via automation with [AutoIt,]("http://www.autoitscript.com") and the latter have some integration with MSIE, so I have the oportunity to reformat the data being read and pass it to the browser, so it can "navigate", through a private network and send the info to the linux-box
4. The linux-box should have internet connection available, so if a problem shows it can be fixed via  secure shell
5. The web based solution will be an exact copy of the medical record management program.

Now let me post my answers to some of the statements addressed before:
1. I will defenestrate the computer after it... or at least make it dual boot
2. No other solution to unpack all the medical records database... believe me I have more than 4 years trying convert this database
3. This solution is almost done
4. Not done
5. Not done

So my questions are as follow
1. Which is the most-easy and faster Rapid Development suite: Ruby on Rails or PHP Cake? I have some self-adquired programming experience (C, HTML, Javascript, AutoIt among others) but I do not have all the time [I'm on the first year of Anaesthesiology Residency] and the will to learn another programming language down to its foundations
2. How do I install all the programs to run the proposed solution? I have googled some solutions but I had no success... A hands on and detailed guide will be appreciated

Comments and suggestions are welcome

---

### Post by Daveski on 2007-09-11
> **qsr.nrwn said:**
> 
2. How do I install all the programs to run the proposed solution? I have googled some solutions but I had no success... A hands on and detailed guide will be appreciated


I would have thought the standard approach would be to use a LAMP system: Linux Apache MySQL PHP, Apache is the web server, the data would be stored in MySQL, and PHP glues it all together.

Ubuntu has an 'out of the box' LAMP solution - check 

[http://www.intelligentedu.com/blogs/post/best_new_training_sites/3668/building-a-linux-server-and-lamp-on-ubuntu](http://www.intelligentedu.com/blogs/post/best_new_training_sites/3668/building-a-linux-server-and-lamp-on-ubuntu)

and

[http://ubuntuforums.org/showthread.php?t=510403&highlight=LAMP](http://ubuntuforums.org/showthread.php?t=510403&highlight=LAMP)

---

