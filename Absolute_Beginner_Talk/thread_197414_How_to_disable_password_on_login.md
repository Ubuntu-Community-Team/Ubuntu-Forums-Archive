---
title: "How to disable password on login?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by johnthejack on 2006-06-15
I want to boot without being asked either for a user name or a password. I've disabled the user logon screen, but I still get asked for a password. Could someone tell me how to disable that as well. please?
I've tried sytem/admin/users and groups, which will allow me to set a blank password, but I wan't to disable it completely. By going to system/admin/loginwindow and then security I have enabled automatic login, but it still asks for the password.
Thanks.

---

### Post by bruce89 on 2006-06-15
It isn't possible, it just isn't secure enough.  It means that applications could run as root without asking for your password.  You can have GDM automatically log you in, go to System>Administration>Login Window, then Security.

---

### Post by johnthejack on 2006-06-15
Thanks, but that's the problem. It automatically logs in the user name, but then asks for the password.
I have a laptop with no screen. I want to disconnect it from an old monitor and run it with vnc from another laptop. Everything works fine until I have to reboot. I would have to attach it to the monitor each time to enter my password. If I could disable or override the password and get it to start up all the way through, then I could reconnect with the viewer each time.

---

### Post by bollix47 on 2006-06-15
Try the following:

sudo visudo

Change the %admin line (last one in file) to look like 

%admin ALL=(ALL) NOPASSWD: ALL

EDIT:  Apparantly 'automatic' login doesn't work with the latest updates.
           The above does still eliminate the need for a password when using sudo.

---

### Post by bruce89 on 2006-06-15
It seems that somebody else is having the same problem - [http://www.ubuntuforums.org/showthread.php?t=197421](http://www.ubuntuforums.org/showthread.php?t=197421)

---

### Post by bollix47 on 2006-06-15
Check my 2nd post(#9) in the above thread for a solution that may work for you.

---

### Post by johnthejack on 2006-06-16
Thanks, yes, that is exactly the same problem. I tried to follow the commands. I had to use your variation after sudo sed. I still get the little box asking for a password. I'm not sure I've done it properly. The original post said that basically I was adding a name to the etc/nopassusers file. I checked and that file is still blank. I tried to edit in sudo, but it said permission denied. Does that sound possible as to why I've gone wrong? Should I be doing something to edit that file?

---

### Post by bollix47 on 2006-06-16
It appears you have changed the name of the file.  Check to make sure you changed it everywhere or copy and paste the following, one line at a time, into a terminal window.

sudo touch /etc/gdmnopassusers
echo $USER | sudo tee -a /etc/gdmnopassusers
sudo cp /etc/pam.d/gdm /etc/pam.d/gdm.orig
sudo gedit /etc/pam.d/gdm

add the line:

auth sufficient pam_listfile.so file=/etc/gdmnopassusers sense=allow item=user

before @include common-auth directive
save and exit

Your new /etc/pam.d/gdm should look something like:

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so
auth sufficient pam_listfile.so file=/etc/gdmnopassusers sense=allow item=user
@include common-auth
@include common-account
session required        pam_limits.so
@include common-session
@include common-password


btw - this problem has been identified and there is a patch on the way.  See:

[http://www.ubuntuforums.org/showpost.php?p=1144713&postcount=13](http://www.ubuntuforums.org/showpost.php?p=1144713&postcount=13)

---

### Post by johnthejack on 2006-06-16
Thank you, that has now worked.

---

### Post by bruce89 on 2006-06-16
[https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49940/+index](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49940/+index), there is an update to GDM which fixes it - 2.14.9-0ubuntu1.  That is a lot of bugfixes.

---

### Post by ahaslam on 2006-06-16
[QUOTE=bruce89][https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49940/+index](https://launchpad.net/distros/ubuntu/+source/gdm/+bug/49940/+index), there is an update to GDM which fixes it - 2.14.9-0ubuntu1.  That is a lot of bugfixes.[/QUOTE]
Just to confirm, the update is available via Update (screwup) Manager, Synaptic, etc.
It does work, I've now removed that extra line from the 'gdm' file.

Let's hope they test their 'updates' a little further before releasing them. Afterall, they're supposed to "correct errors", not introduce them. ;) 

Tony.

PS. That was great advice from bollix47, comming up with a fix within hours of the problem occuring - you're a star. :KS

---

