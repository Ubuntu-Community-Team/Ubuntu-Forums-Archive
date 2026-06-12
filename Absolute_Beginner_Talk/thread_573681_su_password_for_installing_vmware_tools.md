---
title: "su password for installing vmware tools"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by duffymo on 2007-10-11
I downloaded and installed vmware server 1.0.4 on my Windows XP Pro SP2 Intel machine tonight and loaded Ubuntu 7.04 from an ISO tonight.  The virtual server comes up fine.

Next step is to install VMWare Tools.  I extracted the .tar.gz to my /tmp directory and attemped to run the vmware-install.pl script.  A prompt told me that I had to be super user to accomplish this, so I typed "su -" into my terminal and was prompted for the su password.  I entered "vmware", which is supposed to be the default password, but I got an authorization failure.

What am I doing wrong?  How can I get VMWare tools installed successfully?

Sorry to be so noobish.  It's my first night with Ubuntu.  Thanks.

%

---

### Post by baked on 2007-10-11
Ubuntu doesn't have a super user.  You need to use the 'sudo' command to run a command as root.  So if you need to delete a folder called 'test' with root privileges, you would do something like this.

> sudo rm -rf test

It will then ask you for your password, which is whatever your accounts password is that your running (which should be 'vmware' for you).

---

### Post by duffymo on 2007-10-11
Thank you, baked, you are right on the money.  The Perl script is running now.

Do I want these to go to /usr/bin?  I'm being prompted for a directory.  Is the default appropriate, or is it a case of more noobish ignorance for me?

%

---

### Post by baked on 2007-10-11
You should be able to just use defaults for vmware, I don't remember ever doing anything different.

---

### Post by duffymo on 2007-10-11
Nevermind.  The Ubuntu folks are smart enough to provide defaults all the way through.   I accepted all the defaults.  I think everything went well.  I'm restarting now.  

Thanks so much for your help.  Sincerely, %

---

### Post by ryanVickers on 2007-10-11
> ...Next step is to install VMWare Tools...

next step is to switch to VirtualBox ;)

---

