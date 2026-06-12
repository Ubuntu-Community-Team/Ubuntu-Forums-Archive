---
title: "vsftpd or proftpd for virtual user access"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by GISuser on 2007-04-18
I am new to linux and ftp servers and am looking for an ftp server to allow users to access their own directory accessed through an ftp client. 

Currently, the users access a FileZilla Server on a Windows 2003 box.  I am moving the ftp site to an Ubuntu box.  The Ubuntu box is called Screamer.  I am running Ubuntu 6.10 Desktop.

For example,

User1 needs read/write permissions on /home/ftp/user1
User2 needs read/write permissions on /home/ftp/user2
User3 needs read/write permissions on /home/ftp/user3 as well as /home/ftp/user2
UserStaff needs read/write permissions on User1, User2, and User3.

Each user will login in with their own username and password which will take them to the their home directory.  The above users will not have a user account on Screamer.  Therefore, I will need to create virtual users.

I installed vsftpd and got the anonymous connection to work.  But I could not get a virtual user to connect to the ftp server.  I followed the HowTo on [ftp://vsftpd.beasts.org/users/](ftp://vsftpd.beasts.org/users/)... and [http://ubuntuforums.org/showthread.php?t=34292&highlight=vsftpd+virtual+user](http://ubuntuforums.org/showthread.php?t=34292&highlight=vsftpd+virtual+user).

Further searching lead me to the conclusion that vsftpd may not be the best ftp server to use since I need mulitple login configurations.  So I decided to to try proFTP, as it may be more suitable for mulitple login configurations (I am correct in my logic?).  During the install process using Synaptic, I chose the "standalone" installation.  Then I received the follwowing error: "E:proftpd: subprocess post-installation script returned error status 1".  Followed by another screen 
*Starting ftp server proftpd
- IPv4 getaddrinfo 'Screamer' error Name or service no known
- Warning: unable to determine IP address of 'Screamer'
- error: no valid servers configured
- Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
[failed]

invoke-rc.d: initdcript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
  subprocess pst-installation script returned error exit status 1
Error were encountered while processing:
  proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
setting up proftpd (1.2.0-9ubuntu0.1)...
*Starting ftp server proftpd
- IPv4 getaddrinfo 'Screamer' error Name or service no known
- Warning: unable to determine IP address of 'Screamer'
- error: no valid servers configured
- Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
[failed]

Am I wasting my time trying to get proftpd to work or will vsftpd work for what I need?

It would also be great if the users can access the ftp site via an internet browser rather than an ftp client.  

Any suggestions and guidance is greatly appreciated.

---

### Post by ayenack on 2007-04-18
I'm no expert about this so this may be stupid but are you using [PAM]("http://www.kernel.org/pub/linux/libs/pam/")?

Best of luck. ayenack.

---

### Post by GISuser on 2007-04-18
I thought about this too.  PAM is installed and from best I can tell, it is working.  If you have any suggestions on testing whether PAM is working properly, please let me know.

---

### Post by ayenack on 2007-04-18
The only one I have (very limited) knowledge about is vsftpd so I hope this may help a bit.

If it says PAM is there then it should be fine.

Not sure if you know this in vsftpd home directory should not be owned by the ftp user itself. Neither should it be writable by the ftp user. A way to fix this is:

**chown root ~ftp; chmod -w ~ftp**

You may also want to put  **local_enable=YES** in your **/etc/vsftpd.conf** to allow local users to log in.

To link with PAM. (Run "ldd vsftpd" and look for libpam to
find out whether this has happened or not). If vsftpd links with PAM, then
you will need to have a PAM file installed for the vsftpd service (the one above may suite). 
I think you put it under /etc/pam.d not sure about this.

This site may be of special interest to you also [http://www.splitbrain.org/projects/pam_require](http://www.splitbrain.org/projects/pam_require) there's a module written for PAM that seems to fit what you want.

You may want to take a look at this site [http://www.kernel.org/pub/linux/libs/pam/modules.html](http://www.kernel.org/pub/linux/libs/pam/modules.html).

Also check this out if you haven't done so already [http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html) all the commands for vsftpd, amy be of some help.

Try this [http://www.vsftpdrocks.org/faq/](http://www.vsftpdrocks.org/faq/) it's the f.a.q page of vsftpd page it's pretty good for general advice.

Hope this may be of some help to you. Let me know.

Best of luck. ayenack

---

### Post by ayenack on 2007-04-18
Go to this site [http://ubuntuguide.org/wiki/Ubuntu_Edgy#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#FTP_Server) scroll down to 1.88.13 FTP Server and this should solve your problems with proftpd.

Your problems with proFTP may be to do with the name server. Check the **resolv.conf** file and that your chosen **nameservers** are functional. This is avery useful proFTPD site [http://www.engr.colostate.edu/~reinholz/freebsd/ftp.html](http://www.engr.colostate.edu/~reinholz/freebsd/ftp.html) take a look at it may help.

Also have you tried gproftpd it's a front end for proftpd that is supposed to help with configuration.
Also gadmintools seems handy. Both can be downloaded using Synaptic Package Manager.

wu-ftpd seems like a good FTP server also.

This site is also very useful [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup)

You may also want to take a look at [Ubuntu Server Edition]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition").

---

### Post by GISuser on 2007-04-19
Thanks to all for the guidance and suggestions.  I could not figure out the proFTP error and since vsFTPd connected with an anon user, I will try to figure out why a virtual user cannot connect.

I have not had time today to try again with vsftpd.  However, I have a few ideas and will let the group know my outcomes; and propably ask for more help!

In addition, I wonder if the vsftpd file in /etc/pam.d/ need to have the extension *.pam?  I will try it with the extension and see what happens.

Be forewarned, I will have a few questions with directory permissions.

Thanks again.

---

