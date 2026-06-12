---
title: "Automatix trouble....just installed and Auroscript hanging on &quot;password&quot;"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-04-29
Hi,

I just installed automatix, and when I open it....I get the usual credits, etc......but when the autoscript boots it is hanging on "password" any ideas why it prompting me for password? I cant even enter one. Or is this just hanging trying to connect somewhere?

Thanks

Gordo

---

### Post by olsonar on 2006-04-29
It's asking you for your password so that it can make changes to your system. Just click in the terminal and enter your login password.

---

### Post by gordong11 on 2006-04-29
Thnaks....solved! I just exited out of firefox...and it works...but Nvidia installer failed...using a 7600GT. bummer. but others stuff works great.

This is what I am getting in the tterminal:


admin@ubuntu:~$ automatix
bash: automatix: command not found
admin@ubuntu:~$ wget [http://beerorkid.com/automatix/automatix_5.8-1_i386.deb](http://beerorkid.com/automatix/automatix_5.8-1_i386.deb)
--16:10:31--  [http://beerorkid.com/automatix/automatix_5.8-1_i386.deb](http://beerorkid.com/automatix/automatix_5.8-1_i386.deb)
           => `automatix_5.8-1_i386.deb.1'
Resolving beerorkid.com... 208.97.133.175
Connecting to beerorkid.com|208.97.133.175|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34,088 (33K) [text/plain]

100%[====================================>] 34,088       125.66K/s

16:10:32 (125.45 KB/s) - `automatix_5.8-1_i386.deb.1' saved [34088/34088]

admin@ubuntu:~$ sudo dpkg -i automatix_5.8-1_i386.deb
Password:
(Reading database ... 61387 files and directories currently installed.)
Preparing to replace automatix 5.8 (using automatix_5.8-1_i386.deb) ...
Unpacking replacement automatix ...
Setting up automatix (5.8) ...
admin@ubuntu:~$ automatix
bash: automatix: command not found
admin@ubuntu:~$ Automatix
cat: /home/admin/automatix.log: No such file or directory

Does this mean anything?

Then I tried to uninstall and got....

admin@ubuntu:~$ sudo apt-get remove automatix
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  automatix
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 61386 files and directories currently installed.)
Removing automatix ...
dpkg - warning: while removing automatix, directory `/usr/local' not empty so not removed.
admin@ubuntu:~$



weird....????

---

