---
title: "proftpd doesn't do much"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by destructchaos on 2007-07-05
i just installed proftpd out of the repos.  it started up just fine, but when i try to connect to it from either itself or a remote machine, i get the following message, "Connection closed by remote host." or, "ftp: connect: Connection refused."  what did i do wrong?

Thanks.

---

### Post by dwanders on 2007-07-05
I did a Google search for "Ubuntu Configure ProFtpd" this looks promising - 

A- The GUI way (for beginners only)

For those who are new to linux and don't want to use a FTP server without GUI, or just for those who don't use often their FTP server and wish to set it quickly without a high level of security, there is a GTK GUI for proftpd.

Be careful, it's less secure than configuring yourself your server.

1- Install proftpd and gproftpd with synaptic or with this command :
Code:

sudo apt-get install proftpd gproftpd

2-Play with the GUI and set up quickly your server.

---

### Post by destructchaos on 2007-07-05
thanks for the reply, but i only have access to this server over ssh.  there is no xserver to run a gui on.  the thing that i don't get is why, from the ftp user's end, it's acting like i didn't even install it.  it's like the port is open in a firewall or something, but i didn't install a firewall.  does ubuntu server have a firewall enabled by default that blocks port 21?

---

### Post by dwanders on 2007-07-05
Not that I am aware of. I am not following your set up very well. 

YourPC ---- ssh to ------> SomeOtherPC

Where is Ubuntu? And where did you install proftpd? On YourPC or SomeOtherPC?

---

### Post by destructchaos on 2007-07-05
i am on putty, using ssh to control ubuntu server 7.04 where i installed proftpd, which isn't doing much.

---

### Post by dwanders on 2007-07-06
Personally, I have had really good success with vsftpd. So I would think you can do one of two things:

1) Check out this web site which explains how to set up proftpd without the GUI: 

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) 

it looks to me like this how-to covers the process pretty good (however I have never used it as I do not use proftpd).

2) You could use vsftpd by:
sudo apt-get remove proftpd <cr>
once the install has finished
sudo apt-get install vsftpd <cr>
then you configure vsftp by editing the /etc/vsfptd.conf - just read through it - it is pretty self explanatory.

You can start, stop, or restart VSFTPD after booting by using these commands:
/etc/init.d/vsftpd start
/etc/init.d/vsftpd stop
/etc/init.d/vsftpd restart

If you need more information on the server and the config file - here is a very good write up on the matter:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup)

<cr> = return

Hope this helps.

---

### Post by destructchaos on 2007-07-06
i got vsftpd up and running.  thanks for all your help.

---

### Post by insane_alien on 2007-07-06
i found the problem with proftpd. 

its default config denies all connections. it also limits the badwidth to 40kB/s

---

### Post by destructchaos on 2007-07-07
well that seems like a silly way to configure a server.  i didn't install it so it could block all connections, but then again, myabe that's why the 'vs' in vsftpd stands for Very Simple.  i guess i'm just not 'pro' enough to handle the connection blocking proftpd.

---

### Post by dwanders on 2007-07-08
=) Actually I think its Very Secure - but you could not be more correct. Why would you set up a server with all port locked doesn't make much sense to me. 

Glad you got it going.

---

