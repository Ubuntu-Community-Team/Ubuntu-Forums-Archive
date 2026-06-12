---
title: "Ubuntu is working !!!"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by Ifaistos on 2005-10-13
Hello everyone :-)

Boy, am I glad that I installed Ubuntu on my second computer!!
I had tried the live CD and it worked ok, and today after I used the directions for the dual boot and after defragging my HD, partitioning etc...  Ubuntu was installed on my computer.  Also I upgraded to the latest version after following the instructions that some of you guys gave me!!!

Thank you all !!!

I am now writing this message through Firefox on my dual boot ubuntu Linux computer !!  So now that the first and most difficult step is accomplished I need to learn how to use it.    Maybe in a couple of months I will not need to use Windows anymore and they will be a thing of the past!! heheh :-)

Does anyone of you have any suggestions?
Are there any manuals I could download, or any online manuals I could read concerning the use of the GUI, the use of the various commands?

I am totally new to linux or unix commands and totally new to the GUI.  Totally new to the directory structure...

Btw.. What is mounting and unmounting?
Also how do logon as root and what is the password for root?

In order to install Java for Firefox I need to use the command su and need to have priviliges of root so I need to password which I was never asked to enter.

Anyway could someone direct me to some basic reading or tutorials I could use in order to get some basic knowledge and get some basic skills for linux.  Also could anyone suggest any reading I could do to get more comfortable with the GUI.  Also I noticed that there is another GUI I could use... How can I download that...

Thank you all in advance :-)

---

### Post by matthew on 2005-10-13
Start with the links in my signature. I would also add [http://tldp.org](http://tldp.org) as well. Those will get you started.

---

### Post by ShakingSpirit on 2005-10-13
Repeat after me..."I will never use the su command, or log in as root. It is evil."
There, now you're clensed :)
In short, with Ubuntu, you don't/shouldn't log in as root. Root has no password by default. Insted, you can use the command 'sudo', which stands for SuperUserDO. 
You use sudo infront of your command, e.g
$ sudo cat /etc/passwd

It will ask you for your password, which wont be shown on the screen, and then run the command as root :)

If you need to have a root shell, you can use 'sudo -s' on its own, it will ask for your password, and then give you root access :) To get out of the root shell, just type 'exit'.

Also, don't forget to check out ubuntuguide.org :)

---

### Post by Ifaistos on 2005-10-13
Thank you :-)

I have already started reading !!

Shaking spirit, I was just following the instructions that the official Java page has posted on their site....

Thanks for the info though :-)

---

### Post by meborc on 2005-10-13
one thing i found very helpful in my crusade of getting knowledge on ubuntu is:

[COLOR="DarkRed"]**system -> help **[/COLOR]

there choose the last thing which is [COLOR="DarkRed"]**ubuntu 5.10 starter guide**[/COLOR]... 
it helps u understand most of the commands u need to run ubuntu... and i think that it is a better place to look then [www.linuxcommand.org]("http://www.linuxcommand.org") for example [which is a good place and u should check it out enywho :)], where the commands are to linux distros in general, not just for ubuntu...

*[also u can find it in ur's system: file:///usr/share/ubuntu-docs/generic/faqguide/C/faqguide.xml]*

happy hunting :rolleyes:

---

### Post by fuscia on 2005-10-13
i found this site useful (requires java to be enabled. see firefox tools>options>content) - [http://www.linuxsurvival.com/index.php?module=ContentExpress&func=display&ceid=1&meid=-1](http://www.linuxsurvival.com/index.php?module=ContentExpress&func=display&ceid=1&meid=-1)

---

