---
title: "scp problems...."
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by horito on 2006-08-13
I REALLY would like tu unerstand the difference betweeen ssh and scp.

So far I understand that scp is a program that uses ssh to transfer files from one (ssh client) machine to an ssh server machine. But where are the log files located in the server... 

My situation is that I can connect using ssh to my machine at school, but for some reason can't transfer files to it. Well... I should say, almost. 'cuz I actually are able to checkout my files using svn... but can't synchronize my folder with unison (which I know -think- uses the scp functionality)

I have been trough the ssh_config file modifying it in many ways with no success... 

+ I'd think that if one of them works (lets say ssh) then the other should too?? 

Please correct me if I am wrong....

---

### Post by ciscosurfer on 2006-08-13
[http://geekswithblogs.net/bvamsi/archive/2006/03/23/73147.aspx](http://geekswithblogs.net/bvamsi/archive/2006/03/23/73147.aspx)

---

### Post by horito on 2006-08-16
After almost giving up on my problem... (I guess it was too odd for the forum!?)

I solved my issue with the help of the following page: [http://www.snailbook.com/faq/sftp-corruption.auto.html]("http://www.snailbook.com/faq/sftp-corruption.auto.html")

So, basically what happened is that something was been sent to the sshd that he wasn't expecting at logon. This inmediately made me suspect of the customization of my prompt in .bashrc

I thus, had a line in my .bashrc to give me a nice colored prompt that had some spurious code in it... Once I cleared it (commented out) I was able to scp (or sftp) again without any problem.

I hope that this rendering will help someone, someday.

---

