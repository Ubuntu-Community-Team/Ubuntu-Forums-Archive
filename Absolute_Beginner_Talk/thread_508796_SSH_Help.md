---
title: "SSH Help"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by abefroman on 2007-07-24
I tried searching the forums, but didn't have any luck.

I tried to uninstall, and reinstall ssh (lost private key).

Now, whenever I try to install *anything* I get this error:

/var/lib/dpkg/info/openssh-server.postinst: line 202: /etc/sshd_config: No such file or directory
dpkg: error processing openssh-server (--configure):
 subprocess post-installation cript returned error exit status 1
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however;
       Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
  dependency problems - leaving unconfigured
Errors were encountered while processing:
    openssh-server
    ssh

This is on the server version.

Thanks in advance!

---

### Post by rich.bradshaw on 2007-07-24
try

sudo apt-get if install

to try and force install anything that's been left broken - often does the trick...

---

### Post by abefroman on 2007-07-24
thanks, but that didn't work (i'm guessing you meant sudo apt-get -f install?) unfortunately...anybody else?

---

### Post by Alterax on 2007-07-24
Try this:

sudo dpkg-reconfigure openssh-server

Failing that, you should try purging the installation and reinstalling it:
Traditional uninstallation measures usually leave the configuration files intact.  Purging them removes them completely so you get  a fresh start.

sudo dpkg --purge ssh
sudo dpkg --purge openssh-server
sudo apt-get install ssh

--Alterax

---

### Post by abefroman on 2007-07-24
no luck, 

on reconfigure i got: openssh-server is broken or not fully installed

purges yielded:

dpkg: error processing openssh-server (--purge):
  subprocess post-removal script returned error exit status 1
Erros were encountered while processing:
  openssh-server

thanks though guys...any other thoughts?

---

### Post by abefroman on 2007-07-25
Still looking for help on this.

Thanks!

---

### Post by p_quarles on 2007-07-25
You could try getting the Debian package and installing it with that:
[http://packages.debian.org/stable/net/openssh-server](http://packages.debian.org/stable/net/openssh-server)
I doubt that'll produce better results, since the other things you tried *should* have worked. But, that's all I can think of.

---

### Post by adieb on 2007-07-25
hey man

1. you can try to find the mistake in the post-removal script, so just delete that line where the error occurs and then try to remove again.

i can imagine, that the postremovalscript tries to stop a ssh-server that doenst exist or something like that. it´s not a big problem then.

it happened to me once, but unfortunately i cannot remember, where these scripts are located. 

good luck

---

### Post by Arisna on 2007-07-25
Reading your first post, it appears that the post-installation script is looking for /etc/sshd_config.  However, the sshd_config file is kept under /etc/ssh, at least on my system.  See if it is there on yours.  If so, you could probably make your system compatible with this script, and any other script that uses similar methods, by creating a link at /etc/sshd_config to the appropriate file, as follows:

```
sudo ln -s /etc/ssh/sshd_config /etc/sshd_config
```

---

### Post by jzlharvey on 2007-08-22
I'm in the same situation here on a new 7.04 install.  I think I goofed up the first attempt at installing it.  Now I am getting the same error messages as the OP.  Any help would be great.

---

### Post by jzlharvey on 2007-08-22
ok, I think i figured mine out...

for some reason it was naming what should have been "/etc/ssh" to "/etc/ssh.dist" i renamed it via:
```
sudo mv /etc/ssh.dist /etc/ssh
```

and then started from scratch
```
sudo apt-get install openssh-server
```
and all is good now.

---

