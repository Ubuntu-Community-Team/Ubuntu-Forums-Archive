---
title: "Running a SSH server"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by harisund on 2005-09-22
I am running Ubuntu on my laptop in the school dorms. 

I want to know what application I will need to be able to telnet into this machine or SSH into this machine. 

In my desktop machine at home (not in the school dorms) I have installed FileZilla FTP server, and whenever I want some data that is not in my laptop but in my home desktop, I ask my mom to boot the computer, give me the ip, and I login and retrieve my data from school.

Now I want to know the equivalent for a GNU/Linux machine. I want to know how to enable my laptop to listen on SSH ports and telnet ports, so that I can access it from outside.

Is there some sort of a SSH server?

Thanks a bunch

With regards
Hari

---

### Post by KingBahamut on 2005-09-22
apt-get install openssh-server to install the proper ssh server. 

Youll need to foward 22 for ssh to the machine if you can do it. 

Ultimately , you can use SFTP to move data and files the same way you would with ftp as well. 

the openssh client is installed by default, so no worries there.

If you use a windows machine to access that system externally I recommend Putty, its basic , and does just about anything you need.

---

### Post by Xappe on 2005-09-22
filetransfer (sftp/scp) between a windows machine and a linux machine with an ssh server is easily done with the freeware application WinSCP.

[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

---

### Post by mneptok on 2005-09-22
[QUOTE=harisund]
Now I want to know the equivalent for a GNU/Linux machine. I want to know how to enable my laptop to listen on SSH ports and telnet ports, so that I can access it from outside.[/QUOTE]

I find it highly unlikely that you school has no firewalls in place, and student machines are open to incoming traffic on any port. I also find it unlikely that the school will open port 22 on their firewalls and point it at you machine.

IOW, if your school uses netwrk best practices, this will not work.

---

### Post by Gobbla on 2005-09-23
Actually, port 22 and 80 are about the only ports open at our school, so I don't find it that unlikely..

---

### Post by hashimoto on 2005-09-23
[QUOTE=harisund]... I ask my mom to boot the computer, give me the ip...[/QUOTE]

Just a thought: Why dont' you set up a DynDNS account?  You could then use an address like: hari.homeip.net (or something) to reach your box.

---

