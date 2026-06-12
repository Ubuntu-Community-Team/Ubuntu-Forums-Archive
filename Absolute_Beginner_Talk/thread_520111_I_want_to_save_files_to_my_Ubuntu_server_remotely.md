---
title: "I want to save files to my Ubuntu server remotely"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by JoeyJoeJoe on 2007-08-07
I want to be able to, securely, save files up to my Ubuntu server from anywhere on the Internet.

Now, I've played around with vsftpd (very secure FTP daemon) using SSL and passive mode. You can read about them [here,]("http://www.dd-wrt.com/phpBB2/viewtopic.php?t=18288&highlight=") if you want to.

So far this has not worked for me and I need an alternative.

Any thoughts? If I cannot simply copy files up to my server, it won't be of much use to me or anyone else.

Thanks,
JJJ

---

### Post by olejorgen on 2007-08-07
You can look into **ssh** and **scp**. (You will probaly need to open up port 22 if you have a router)

---

### Post by bodhi.zazen on 2007-08-07
scp

scp file ip:/save_location

You will need to set up a ssh server ...

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
	
	See also [denyhosts](http://denyhosts.sourceforge.net/) ~ it is in the repos, but you should read the config file ...

---

