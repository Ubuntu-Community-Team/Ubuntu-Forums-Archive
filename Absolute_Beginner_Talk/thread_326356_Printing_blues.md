---
title: "Printing blues"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by paritosh1010 on 2006-12-27
So I have been trying to print on my Ubuntu Dapper since yesterday. The printer just takes in pages, waits 50 secs or so, n gives out blank pages.

The error log says not authorised, as I will show you here:

> E [27/Dec/2006:23:22:59 +0530] CUPS-Set-Default: Unauthorized
E [27/Dec/2006:23:23:28 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:23:38 +0530] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [27/Dec/2006:23:23:39 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:23:57 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:24:13 +0530] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [27/Dec/2006:23:24:13 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:34:45 +0530] Creating missing directory "/var/run/cups/certs"
E [27/Dec/2006:23:36:11 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:36:22 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:36:23 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:36:23 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:36:23 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:36:25 +0530] cupsdAuthorize: Empty Basic username!
E [27/Dec/2006:23:36:25 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:36:35 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:36:36 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:36:36 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:36:36 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:48:30 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:48:45 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:48:45 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:48:45 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:48:45 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:57:18 +0530] Creating missing directory "/var/run/cups/certs"
E [27/Dec/2006:23:59:22 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:59:22 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:59:28 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [27/Dec/2006:23:59:55 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:00:01 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:00:39 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:00:39 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:00:46 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:00:46 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:00:48 +0530] [Job 6] No %%BoundingBox: comment in header!
E [28/Dec/2006:00:01:10 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:01:20 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:01:20 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:01:20 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:01:20 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:18:14 +0530] CUPS-Add-Modify-Printer: Unauthorized
E [28/Dec/2006:00:23:29 +0530] CUPS-Add-Modify-Printer: Unauthorized


I tried adding shadow to SystemGroup, following posts on another forum. I think I might have done that wrong. Please, can anybody resolve this problem for me from scratch?

---

### Post by pseudonym on 2006-12-27
You're using the web interface to configure cups, right? a more elegant solution, which should also solve your problem in the process, would be to install 'system-config-printer' or, if you already have gnome libraries installed, 'gnome-cups-manager' (you could install this even if you don't already have gnome libs, but it would be overkill if this is the only gnome app on your system).

---

### Post by paritosh1010 on 2006-12-27
nono I do have Printing installed in System>Administration and I tried using that too. 

Actually what happened was I tried using the HPLIP toolbox, and it redirected me to the CUPS Configuration utility from browser. Now, that detected my printer too, but it wouldnt let me make any changes, requiring for a password. I was then redirected to CUPS forum, where there was a post pertaining to this, and I did the changing of cups users and groups.

The bottomline still remain though-cant run my printer.

---

### Post by pseudonym on 2006-12-27
Oh, OK. I had this problem once. I'm pretty sure I solved it by logging in to cups as root. If you don't have the root password set on your system (it isn't by default in ubuntu) just do 'sudo passwd root' and choose a password...

---

### Post by paritosh1010 on 2006-12-27
no. I do have the root password, since when I did what you said, it asked for the previous password.
sorry mate for all the trouble..

---

### Post by pseudonym on 2006-12-27
This might be a silly question, but after you added user 'cupsys' to the 'shadow' group, you did restart cups by doing 'sudo /etc/init.d/cupsys restart' ?

something else which may work - on my system, my ordinary user is a member of the 'lpadmin' group. You could try doing the same on yours...

---

### Post by paritosh1010 on 2006-12-28
Yeah, I did restart cupsys, and I should try making my user part of lpadmin right? Ok I am gonna try that.

[edit] - I am a member of lpadmin too.

---

### Post by pseudonym on 2006-12-28
Sorry, I'm out of ideas. :( 

You seem to be aware of the procedures outlined at linuxprinting.org so the only thing I can suggest is to get your system into the state it was in before you had your adventure with CUPS, then start over.

---

### Post by paritosh1010 on 2006-12-28
Ok, thanks for the effort. You know any place where I could find solutions..

---

### Post by pseudonym on 2006-12-28
Hi again,

The best resource for linux printing issues is [Open Printing]("http://www.freestandards.org/en/OpenPrinting"), formerly known as linuxprinting.org . I think some of their stuff is even Ubuntu-specific.

HTH

---

