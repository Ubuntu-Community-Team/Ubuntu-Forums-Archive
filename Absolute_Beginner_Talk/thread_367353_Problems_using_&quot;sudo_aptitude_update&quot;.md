---
title: "Problems using &quot;sudo aptitude update&quot;"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by enpey on 2007-02-22
Hello all,

I have recently installed Ubuntu 6.10 (first experience with Linux). Now I have had a fair amount of trouble with it all, as I can't manage to install some things I want to install nor update what would probably help me install the things I want.

FIrst things first, computer is a Dell Dimension 8400 I believe. P4 3.4GHz, 2GB RAM, SATA 160GB HDD (and a secondary IDE 160GB HDD at hd1). First problem I had was the GRUB loader wasn't doing what it was meant to. I ended up installing GRUB onto (hd1) and editing the menu.lst file so it opened up both Ubuntu and Windows XP correctly.

Once I have Ubuntu installed, I firstly install the build-essentials package. I am now struggling to get Automatix2 or EasyUbuntu to install programs for me. The connections are simply timing out. Nor can I use "sudo aptitude update" or "sudo apt-get update", with the majority of connections timing out. I found this 

[http://www.ubuntuforums.org/showthread.php?t=300401&page=2&highlight=www.psychocats.com%2Fubuntu%2Fsources](http://www.ubuntuforums.org/showthread.php?t=300401&page=2&highlight=www.psychocats.com%2Fubuntu%2Fsources)

this afternoon, and thus had my sources.list file changed. When I first ran "sudo aptitude update" it worked perfectly and took a few minutes to download everything. It then said I have 220 odd MB downloadable updates through the Update Manager. But I decided to reinstall Ubuntu so it would be fresh as I had a few invalid drivers installed through ndiswrapper, and other assorted bits and pieces lieing around. So now I'm back in Ubuntu and stuck with the same problem as before with connections timing out all the time.

If anyone can help me out at all I would really appreciate it,
Thanks, Nathan

---

### Post by Rui Pais on 2007-02-22
hi,
what exactly is the error? 

Note that although the thread you link had a huge quantity of posts about gpgs, the really problem wasn't that (one can install packages without set gpg, although it's considered a security risk) but the one mentioned on the beginning of post #9, an incorrect DNS server list. 

Check if your apt-get update outputs some 1.0.0.0. If that was the case your DNS servers are incorrect... 
if that was not the case you must post the error messages to us understand what exactly is going on.

hth

---

### Post by tchoklat on 2007-02-22
after a new install you will find that you will have many Mb of files to download to bring it up to date. The sources list requires amending to allow this. There are many 'versions' of the sources list that you can use, though you do need to review them to determine what you want as many of the sources are not Ubuntu certiifed and are often 'dodgy. See;
 
[http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)
 
This one is probably safer to use;
 
[http://www.ubuntugeek.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html](http://www.ubuntugeek.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html)
 
these should get you going!
 

Tony

---

### Post by freebird54 on 2007-02-22
Just a thought crosses my mind here - could the problem be internet connection related?  If the timing out is the real problem, could it be the ipv6 problem that so many have had?

COuld well be worth flipping through the forums for the fixes, and trying that - sorry I don't have the thread info to post for you.

freebird54

---

### Post by latanerp on 2007-02-22
I'm using Automatix2 right now, and it has had some timeout errors.  However, it does appear to connect and proceed after 1-3 attempts.  Did you give it time to do that? Just a thought, no expert here. :)

---

### Post by Rui Pais on 2007-02-22
> **freebird54 said:**
> Just a thought crosses my mind here - could the problem be internet connection related?  If the timing out is the real problem, could it be the ipv6 problem that so many have had?

COuld well be worth flipping through the forums for the fixes, and trying that - sorry I don't have the thread info to post for you.

like [these one]("http://ubuntuforums.org/showthread.php?t=87798"), among others....

---

### Post by enpey on 2007-02-22
I don't believe it  is IPV6 as I already disabled that so as I can browse the internet in FireFox (sorry I neglected to mention that).
And I do believe that it may be using 1.0.0.0 although I'm in Windows at the moment, I will reboot and check.
So what must I do to fix this DNS problem?

---

### Post by enpey on 2007-02-22
Yes, the DNS problem is correct:

N:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

Sorry I was unclear before. What should I try doing now?

Thanks, Nathan

---

### Post by Rui Pais on 2007-02-22
> **enpey said:**
> Yes, the DNS problem is correct:

N:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

Sorry I was unclear before. What should I try doing now?

Thanks, Nathan

10.0.0.0 <=> Servername problem :) 

Check your /etc/resolv.conf. 
What's in there? Do you have a router/modem for adsl connection? 
Is the router IP whats in resolv.conf?

---

### Post by enpey on 2007-02-22
I found this thread [http://www.ubuntuforums.org/showthread.php?t=282034](http://www.ubuntuforums.org/showthread.php?t=282034) and added the line 

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

just above the request line and sudo aptitude update now seems to be working. So hopefully have the problem sorted.

Thank you to all :)

---

### Post by Rui Pais on 2007-02-22
uauuu. 
i was to suggest that you use the dns of your internet provider, but i did'nt know that one could use generic dns! 

Thats much better since it would fail if your internet provider change or changes dns servers ips (it happen to me int the past)

i'm glad i try to help you. End up learning a little :)

---

