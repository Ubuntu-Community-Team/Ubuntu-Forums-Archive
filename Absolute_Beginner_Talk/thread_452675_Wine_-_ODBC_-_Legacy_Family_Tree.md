---
title: "Wine - ODBC - Legacy Family Tree"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by wjhildreth on 2007-05-23
Hello all,

First let me say thanks for all the work you put into Ubuntu and its forums. Second, let me thank you for all the help you have give to me so far. You have made my Ubuntu experience much better than it could have been, I am sure.

I am trying to reach a point that I can be Windows independent. Well, I don't think I can at the moment because of software that I use for Genealogy research that I have grown very comfortable with. (Not to mention that I have not found a Linux equivalent yet IMO).

I have installed Wine on my Ubuntu 7.04 and am able to run the file manager and that sort of thing. I was able to install Legacy Family tree without a hitch, and even though it starts a little funny, from what I got to look at, it seems like Wine could be a happy medium for me to stay in Linux and rid myself of Windows. But alas, I have a problem.

Legacy Family Tree uses what I think is basically a MS Access Database. Or at least I can browse the database with Access. When the program starts, you have to select a database to use, and I chose the default 'sample' database. It is at this point the program dies. I suspect it is because of some kind of ODBC drivers or something. Can anyone help me with this? Point me to good liturature or confirm the problem?

Legacy Family Tree can be had as a free download from [www.legacyfamilytree.com](www.legacyfamilytree.com). The demo does not expire and has some features removed until you buy it. I have this software and a few others from this same company that I use on a regular basis, and would like to figure out how to get them to run on Wine.

I have checked out the Wine app database, the program is listed but there is no maintainer and not being a game or other popular piece of software, has no votes.

Anyway, I would appreciate any help you are willing to give.

Warm Regards,

Joe Hildreth

---

### Post by arkiedan on 2007-05-25
Hate to answer like this but I don't have an answer either. Like you I managed to get Legacy installed (a little quirky) but can't open any database. I doubt we'll find an answer anywhere but ... who knows.

FWIW PAF runs fine and looks fairly nice in both Ubuntu and PCLos. Still, it just ain't the same as my favorite - Legacy.

I have Gramps installed and dislike the limited interface. Will never become accustomed to it I fear.

This is truly my last link with Windows. I'd love to find a good genealogy application in Linux and Windows XP is outa here.

arkiedan

---

### Post by wjhildreth on 2007-05-25
I know there are some other Family Tree packages out there, but I have not found anything quite as versatile as Legacy yet. I did however, find a piece of PHP software that uses a MySQL database to keep you data as well as sources. As I remember it was fairly easy to set up and use.

It is called 'The Next Generation of Genealogy Sitebuilding' and can be found at the following URL.

[http://lythgoes.net/genealogy/software.php]("http://lythgoes.net/genealogy/software.php")

The last version I used us V5 and I think that v6 is out now. It is not free software, but worth the purchase price IMO.

=====

Hmmm.... Want to take and existing Genealogy program that is in the open source and create one like Legacy? I wonder if there is an interest? Want to talk about it? Let me know. You can email me at [email]xavier@gtec.com[/email]

Regards,

Joe Hildreth

---

### Post by Reverendspam on 2008-01-13
I am using Legacy Family Tree on Ubuntu in a different setup. I gave up on wine as it is too buggy.

I have VirtualBox running on Ubuntu. Installed XP onto VirtualBox then installed Legacy Family Tree into XP.

No problems encountered other than a couple of hours to setup and I see no performance problems with XP running this way....but I have a pretty stout machine-- 2GB memory, AMDx2 4200+

I export my Legacy data into The Next Generation (TNG) genealogy software as seen here [http://mullismelange.com/tng/index.php]("http://mullismelange.com/tng/index.php")

You also might want to check out phpgedview as free alternative.

-joe

---

### Post by sgtbob on 2008-01-18
Have you folks tried GRAMPS?  IT is a great program and to me every bit as versitile (or maybe more so) as FTM and other programs.

---

### Post by paul.prinsloo on 2008-01-29
hi al
have to agree, Legacy is very nice indeed, and also one of the last things that stops me from only working in Ubuntu. 
As for the eventual website...also look at Genmod, open source and thus free. I think the developers were originally involved in phpgedview, but I speak under correction.
I use it to publish my stuff.
Paul

---

### Post by MarcG on 2008-02-23
My wife has a related problem. She's running XP, but Legacy is constantly bombing on her. Right now she can't even get into it. She's tried all the helps she could find in the various forums, but nothing works. What she'd like to do is convert her Legacy file to GEDCOM and then find something else to use, eventually probably on a Mac (she's afraid of Linux :roll:)

I'm running Ubuntu 7.04. Is Legacy running well enough under wine to let me take her files and convert? I'd hate to go through the install and find I can't get there, or worse, make a corrupted or partial conversion.

Thanks.

--Marc

---

### Post by anewguy on 2008-02-23
I myself use Family Tree Maker, but Legacy is a very nice product as well.  Non-genealogists out there need to understand that a product like gramps just isn't close to what we are used to.  I also ran into problems trying to run FTM, and finally installed VMWare Server then created a virtual machine with Windows in it to run my FTM.  I would have preferred a native application, but as you've noticed there really isn't one to compare and no clean way to migrate.

Best of luck!  :)

---

### Post by Reverendspam on 2008-04-11
> **MarcG said:**
> My wife has a related problem. She's running XP, but Legacy is constantly bombing on her. Right now she can't even get into it. She's tried all the helps she could find in the various forums, but nothing works. What she'd like to do is convert her Legacy file to GEDCOM and then find something else to use, eventually probably on a Mac (she's afraid of Linux :roll:)

I'm running Ubuntu 7.04. Is Legacy running well enough under wine to let me take her files and convert? I'd hate to go through the install and find I can't get there, or worse, make a corrupted or partial conversion.

Thanks.

--Marc

If your wife is willing to take the time to learn how to use a mac she can use the gnome desktop easily on Ubuntu.

Legacy Family Tree is not running correctly under wine.

As I stated earlier - install a program called Innotek Virtualbox and then install your windows xp on top of Virtualbox. Setup is pretty straight forward.

Legacy runs great as does any other windows xp software.

attached is a picture of my desktop showing legacy running on top of Ubuntu using Virtualbox (seamless mode).

Legacy 7 is getting ready to come out with new templating for sources and I bet there will also be auto connection to the LDS vault files that are coming on line. Woohoo!

Yes Gramps is a valiant attempt, but those of us who have been researching our geneaologies for a while need software with much more than what Gramps offers.

A better alternative to Gramps is TNG (not free). Run both locally on my machine and live online.

-joe

[http://www.mullismelange.com/snapshot1.png]("http://www.mullismelange.com/snapshot1.png")

---

### Post by paul.prinsloo on 2008-04-29
At last...happiness!!!
I now have Legacy running...
thanks to Reverandspam...without his post I would have given up.

Upgraded to Ubuntu 8.04...installed VirtualBox (what a nice program), 
installed Windows XP under Virtual Box, and then Legacy like normal on XP.

Took a while to figure out which VirtualBox to install..easiest was to type in VirtualBox on a command line, and it comes back and says which one to install.

Obviously you still need to install Windows under VirtualBox..but so who cares..for me it works great, better than Wine (just my opinion).
Took a noob like me about 3 hours in total.

---

