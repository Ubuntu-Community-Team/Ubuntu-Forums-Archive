---
title: "Cannot install Kubuntu updates"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by ifican on 2006-06-25
I have been searching the forums and net for several days, i have tried every little thing i could find but to no avail. The following are errors i am getting, as you see a couple of the update seems to download but i ultimately get an error that says changes could not be committed. Please help as i really do want to make Linux my primary machine but am having difficulty making myself feel comfortable about security, updates and overall usability. I have no problem knowing there is going to be a learning curve but usually i can make a dent by this point and have not even made a scratch. Here is what i am seeing:

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources

about 10 updates return the above, all the rest return what is listed below:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 146.137.96.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 146.137.96.15 80]

Please help.......

---

### Post by Stolie on 2006-06-25
You might post your sources.list, so we can help troubleshoot a bit more. That may give some insight as to what to do next!

---

### Post by ifican on 2006-06-25
Let me also add that i have installed Kubuntu on another machine of mine and the updates installed flawlessly, that is partially what is so perplexing to me how the one machine was so easy and this one is being so difficult.

---

### Post by ifican on 2006-06-25
I am going to need a little hand holding, i have no problem using the terminal however i don't remember how to do most of the commands so please just let me know the command you would like to see and i will be happy to reply.

---

### Post by Stolie on 2006-06-25
I believe the path is /etc/apt/sources.list.

If you do "sudo nano /etc/apt/sources.list", then copy/paste the file contents into a post, you may get a bit more help!

---

### Post by ifican on 2006-06-25
inputting the command  ls /etc/apt/sources.list only returns the line  /etc/apt/sources.list and nothing else.

---

### Post by Stolie on 2006-06-25
how about "sudo nano /etc/apt/sources.list"?

---

### Post by ifican on 2006-06-25
Here is the output:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

---

### Post by Stolie on 2006-06-25
what are you using to update? just "apt-get"? synaptic? Automatix?

---

### Post by ifican on 2006-06-25
I have tried apt-get , synaptic, adept updater and manager all get the same error "cannot commit changes" or the errors i previously listed.

---

### Post by kenklay on 2006-06-26
I am having the same problem.  I installed Dapper using an upgrade from Breezy but inherited some problems from breezy and got more, so did an install from an ISO burned to disk.  

Adept list two files for upgrade but when I try to upgrade I get the same error message as ifican did.  If I try apt-get update I get error message:
Connection failed [IP: 146.137.96.15 80]

My sources list is the same except that the universe repositories are disabled.  I have a home brew computer with a ADM Athlon-XP processor. I can get on line with Konqueror so my internet connection is good.

---

### Post by ifican on 2006-06-26
This seems to be an ongoing issue as i have seen several other folks today post with the same problem. Does anyone have an ideas yet as to a fix?

---

### Post by ifican on 2006-06-26
Can someone please help with this. I really want to try this out but it is getting very frustrating for me, i cannot install anything update or upgrade related, no ubuntu-desktop, traceroute, nada. This is my second attempt over the last couple years to run linux and its very very frustrating. The install was so easy but for some strange reason i cannot do anything else. Please help......

---

### Post by nalmeth on 2006-06-26
Change the us.archive.ubuntu.com/ubuntu to archive.ubuntu.com/ubuntu.
In other words, drop the us

sudo apt-get update
sudo apt-get upgrade

---

### Post by ifican on 2006-06-26
How do you go about doing that? I have no problem resolving or pinging us.archive.ubuntu.com/ubuntu however i will be happy to change it and give it a try if you can give me a little direction.

---

### Post by kenklay on 2006-06-26
I found something that worked for me in
ubuntuforums.org/showthread.php?t=190679

I commented out the only line in my apt.conf file on the proxy status and now Adept works as it should.

---

### Post by WADemosthenes on 2006-06-26
[QUOTE=ifican]How do you go about doing that? I have no problem resolving or pinging us.archive.ubuntu.com/ubuntu however i will be happy to change it and give it a try if you can give me a little direction.[/QUOTE]
This is what I would do to completely replace your sources with good ones.
Open a console, then type exactly:

**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup**

Then type:

**gksudo gedit /etc/apt/sources.list**

A text editor will open up that will list the sources that you are using (someting.net and stuff like that).  Then I would delete all the text and copy and paste this exactly:

[B]## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse 

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free[/B]

This help is from: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by ifican on 2006-06-27
The following line: sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup entered without an issue however the next line: 
gksudo gedit /etc/apt/sources.list was invalid and not excepted. I received the following: bash: gksudo: command not found.

any other suggestions. I checked the other thread as it has helped someone else however i cannot or do not know how to locate the apt.conf file.

---

### Post by gingermark on 2006-06-28
WADemosthenes seems to think you're using Ubuntu. But he said "gksudo" instead of "sudo", so I won't trash him too much.

If you see "gksudo gedit" (or "sudo gedit") in any future guides, replace them with "kdesu kate" and it should then work in Kubuntu.

---

### Post by kenklay on 2006-06-28
In my system the apt.conf file was located under /etc/apt.  I used Kate to edit it starting that using the Alt-f2 box and typing in kdesu kate to open it in root mode which you need to edit conf files.  Kate has a nice navigator on the left side you can use to find a file.  If you do not find it there open Konquorer and go to tools the "find file" and see what it can turn up.

---

### Post by ifican on 2006-06-28
Thanks for clearing up the syntax, i will be sure not to forget that anytime soon. However after editing the archive to just archive from us.archive i have a new issue. Adept no long shows i have any updates to install and if i go to package manager it shows i have absolutely everything installed on my mahcine. Every single file that shows up in package manager shows installed. I also finally figured out how to get to the apt.conf file. Any ideas on what my issue now is? Should i reinstall and something might have gotten messed up? The interesting thing is i have 2 internet connections at 2 different residences. The connects at place 1 updates with no issues, the connection at 2 has issues. Both are through the same provider. Thanks.

---

### Post by ifican on 2006-06-28
Well Im happy to report that after editing the apt.conf file, i just retried and updates are flowing smoothly. Does anyone have any idea why simply searching for a proxy when one is not present updates have an issue? Also i would like to install the ubuntu desktop but when using the command sudo apt-get install ubuntu-desktop i get an error. Thanks everyone for trying to help the previous issue.

---

### Post by ifican on 2006-06-28
Well i am also happy to report after update package manager fixed itself. I also figured out a round about way to get ubuntu-desktop installed as well its running now. Again thanks for all the support. I look forward to playing with linux and potentially moving to linux for all i can. I wont beable to ever get rid of the evil doer however i think i can move really far away and really look forward to learning more and more. 

ifican

---

