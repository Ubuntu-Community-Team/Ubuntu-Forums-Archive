---
title: "Webmin install requires root privilages!"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by U2XS on 2007-03-30
Hey guys, I am following this tutorail ([http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)) which suggest I download Webmin.  In doing so I downloaded it and webmin's page states that I should write this in the command line

dpkg --install webmin_1.330_all.deb

I've done so, but the problem is that I am logged in as "family" and not "root" and I need root privileges.  I understand that the "sudo" command will help me here, but I don't know how to invoke it.  Can anyone help?

---

### Post by jerryrw on 2007-03-30
just add sudo to the beginning i.e. 

sudo dpkg --install webmin_1.330_all.deb

then enter your password

---

### Post by Maestro23 on 2007-03-30
> **U2XS said:**
> Hey guys, I am following this tutorail ([http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)) which suggest I download Webmin.  In doing so I downloaded it and webmin's page states that I should write this in the command line

dpkg --install webmin_1.330_all.deb

I've done so, but the problem is that I am logged in as "family" and not "root" and I need root privileges.  I understand that the "sudo" command will help me here, but I don't know how to invoke it.  Can anyone help?

Try:

> sudo dpkg.....

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by x1a4 on 2007-03-30
Hi,

Be sure you take some time and read some of the documentation (System > Help > System Documentation) that comes with Ubuntu.  It will help you with all the basics you need to know.  You might also want to check out the following: 

[Excellent newbie guide](http://ubuntuguide.org/)  <-- start here

[Excellent Ubuntu fan site with tips, tricks and tweaks](http://www.ubuntugeek.com/)

[Good info can also be found here](https://launchpad.net/ubuntu/)

By default, Firefox has some excellent links: 

Bookmarks > Ubuntu and Free Software links

---

### Post by U2XS on 2007-03-30
thanks for the help.  I tried "sudo dpkg --install webmin_1.330_all.deb".  It did get a response other than bash.  It asked for a PW - which I entered and it returned a few lines.

> dpkg: error processing webmin_1.330_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 webmin_1.330_all.deb

But I see the file there on my desktop.  So where does that leave me?

P.S.  I've bookmarked the links and I now realize that firefox does have added help links: thanks!

---

### Post by Maestro23 on 2007-03-30
> **U2XS said:**
> thanks for the help.  I tried "sudo dpkg --install webmin_1.330_all.deb".  It did get a response other than bash.  It asked for a PW - which I entered and it returned a few lines.



But I see the file there on my desktop.  So where does that leave me?

P.S.  I've bookmarked the links and I now realize that firefox does have added help links: thanks!

Are you in your Desktop while in command line?

> cd /home/username/Desktop

then

sudo dpkg ....

More links for you.

Installing in Ubuntu:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by U2XS on 2007-03-30
It seems the last command was key.  I know this must seem commonplace to you, but its all Greek to me!  

> family@ubuntu:~/Desktop$ sudo dpkg --install webmin_1.330_all.deb
Password:
Selecting previously deselected package webmin.
(Reading database ... 88486 files and directories currently installed.)
Unpacking webmin (from webmin_1.330_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin

Now that I got it to work, there is an error! :(

---

### Post by PilotJLR on 2007-03-30
Try this:
```

sudo apt-get update
sudo apt-get install perl5 libnet-ssleay-perl

```

What we're doing here is taking care of dependencies... this basically means that webmin wants packages such as Perl to be installed, since it needs to use them. Apt-get can take care of these requirements for you... after you run these commands, repeat the webmin dpkg install you did before.

---

### Post by U2XS on 2007-03-31
I tried it, and it worked, but stated that I already had the newest versions.  At some point I saw that one of the errors was because the package did not have  a dependency "libauthen-pam-perl" - so I tried to install it using this command "sudo apt-get install libauthen-pam-perl" and I came up with this.

> family@ubuntu:~/Desktop$ sudo apt-get install libauthen-pam-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libauthen-pam-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libauthen-pam-perl has no installation candidate
family@ubuntu:~/Desktop$

It leaves me a little confused because this is a fresh install and I don't remember uninstalling anything.  So if there is a refrence to this in the system, I don't understand why its missing.

---

### Post by thalueng on 2007-06-05
You have the universe repository commented out, see here for instructions: [http://www.webmin.com/udeb.html](http://www.webmin.com/udeb.html)

---

