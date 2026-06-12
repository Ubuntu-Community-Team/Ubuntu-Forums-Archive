---
title: "Setting up a server ??"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by ultranoize on 2007-02-24
Hi, I'm using Dapper in a Dell laptop. I'd like to connect from my office to my Linux box. I know that you can do this with e.g. shh. The thing is that I need to know what it is I have to do on the Linux box  to be able to connect?   I'm almost sure I have to set up a server. I've already installed Apache and I've got an account in dyndns.org.  There are some issues regarding firewall and portforwarding (which i have absolutely no idea how to do) that I need to consider. Could anyone help me out with this?  I think what I need is to make a list of things to do.  I can google them and ask later if I get stuck.

regards,

---

### Post by hyper_ch on 2007-02-24
well, you need to isntall the ssh server :)

```

sudo apt-get install openssh-server

```

Once that is installed and once you have forwarded port 22 from your router to your pc that is running the ssh server you can simply connect to it...

You your username and password :)

---

### Post by nhandler on 2007-02-24
What type of connection are you interested in? Do you simply want to transfer files between the 2? If so, you could do that with the apache2 webserver, an ftp server (proftpd), or ssh. If you are interested in viewing the screen of your home computer and controling it remotely, you can use vnc or ssh + x forwarding (I never got thee ssh+x forwarding thing to work). One last question, is your office somputer running linux? Windows? Mac?

---

### Post by SeanTater on 2007-02-24
Are you setting an SSH server on the *internet?!* Using plain passwords?!

First read these, focusing on RSA Authentication..

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)


If you are looking for a secure remote-desktop, read this:

[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

---

### Post by ultranoize on 2007-02-25
Thanks for answering. I'd like to view the screen of my home computer so that means that  I'll probably have to use vnc (it is already installed).  I use windows at the office. I know i can probably use Putty to view my screen. On the other hand i use cygwin in my windows machine so probably it could also be done by ssh-ing or something.  I'll take a look at all the links that you guys have posted and will get back to you.

thanks,

---

### Post by steve.horsley on 2007-02-25
SeanTater is right. There are lots of password guessing bots out there that will happily spend 24x7 guessing at usernames and passwords on SSH servers. Best is to use authentication as Sean suggests. Next best, I use plain passwords, but used /etc/hosts.allow and hosts.deny so that ssh only accepts connections from my work location. I get several hits a day from password guessing bots, but they give up soon because ssh won't talk to them.

You need to install package openssh-server, which installs a daemon called sshd. The configuration file is /etc/ssh/sshd_config.

Putty doesn't do GUIs. If you run an X server on your windoze box (such as cygwin) then you can ssh your home from putty (enable X forwarding) and then launch GUI apps from the command line they will open in cygwin. Alternatively, use VNC over an SSH tunnel. **Never** expose your VNC service to the internet.

As for port forwarding, if you use a router to connect to the internet, as opposed to a direct connection like a USB modem, then you will need to configure that router to forward incoming connections to TCP port 22 (the SSH port number) to your Ubuntu box. How you do this depends on the router - it is the router you are configuring here not the Ubuntu box.

I can't help with dynamic IP addresses - I've never had one.

---

### Post by hyper_ch on 2007-02-25
You could look at the NXClient/Server from nomachine.com --> It's simple X-forwarding and I think it's quicker than traditional vnc....

Or have a look at the xlivecd --> [http://xlivecd.indiana.edu/](http://xlivecd.indiana.edu/)

Both worked fine for me connection from my university terminal to my homecomputer (upload 300kbit/s)

---

