---
title: "Windows Domain vs Ubuntu"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-05-24
I was just wondering how stuff like a domain can be created like in Windows 2003 Server for use in a network where ubuntu is the server and the workstations are running windows

---

### Post by youthforlinux on 2006-05-24
anyone wish to answer????

---

### Post by tribaal on 2006-05-24
Hum... I believe if no one answers is because no one knows the answer. You should be patient, so posts only are answered a few days/weeks atfer they are first posted.

As a rule of thumb you should only post a "anybody knows an answer" kind of post at least 24 hours after your first post... There are people around the world that are sleeping as you type, and they might have then answer to your problem :)

Patience is the key. :)

- trib'

---

### Post by youthforlinux on 2006-05-24
sorry 
ive always been told that im not patient

---

### Post by uteck on 2006-05-24
There are various how-to's for this at the Samba website.  Were I used to work we used Debian as a Domian for some XP workstations.  I think you can install webmin and the samba pluging for it and configure it that way also.

---

### Post by youthforlinux on 2006-05-24
ok ill try that but if anyone has any other suggestion
feel free to post them!!!!

---

### Post by Iowan on 2006-05-24
Samba can emulate (maybe bad choice of word) an XT domain controller - dunno if it does AD well...

110 posts in 2 days? You've been busy...

---

### Post by rtobyr on 2006-05-24
A couple of things to keep in mind:

1. The SAMBA docs will tell you how to do this.

2. While Ubuntu is great and all, they only guarentee maintenance updates (patches) on each version of Ubuntu for 18 months, which is fine for the desktop. Note that Mr. Zimmerman's promise of a five year lifecycle is still "pie in the sky." So Ubuntu 5.10 will stop getting patches in April, 2007. A free alternative can be found at [http://www.centos.org](http://www.centos.org). They guarentee maintenance updates for, like, 7 or 8 years (I forget). The latest CentOS version (4) will stop getting patches in Feb. 2012. This is much more appropriate for a server platform.

3. If you run a Linux/Samba domain controller without having other domain controllers that are actually running Windows 2003 Server, then you will be unable to use all the features of Active Directory, most noteably, group policies.

---

### Post by youthforlinux on 2006-05-24
[QUOTE=Iowan]Samba can emulate (maybe bad choice of word) an XT domain controller - dunno if it does AD well...

110 posts in 2 days? You've been busy...[/QUOTE]

i love ubuntu

---

### Post by Daremo on 2006-05-24
Recently Xandros released their version of an "Enterprise" class server that supposedly can integrate seamlessly within Active Directory and even be a domain controller. The article did not go into detail as to how it would handle Group Policy objects and Organizational Units though. It would be interesting to hear any feedback from someone that has tried it...

---

### Post by Sef on 2006-05-24
> 2. While Ubuntu is great and all, they only guarentee maintenance updates (patches) on each version of Ubuntu for 18 months, which is fine for the desktop. Note that Mr. Zimmerman's promise of a five year lifecycle is still "pie in the sky." So Ubuntu 5.10 will stop getting patches in April, 2007. A free alternative can be found at [http://www.centos.org](http://www.centos.org). They guarentee maintenance updates for, like, 7 or 8 years (I forget). The latest CentOS version (4) will stop getting patches in Feb. 2012. This is much more appropriate for a server platform.


Dapper will be supported for 3 years on desktops and 5 years on servers, so it will be supported until 2009 for desktops and 2011 for servers.

[DapperGoals]("https://wiki.ubuntu.com/DapperGoals")

---

### Post by youthforlinux on 2006-05-25
[QUOTE=Sef]Dapper will be supported for 3 years on desktops and 5 years on servers, so it will be supported until 2009 for desktops and 2011 for servers.

[DapperGoals]("https://wiki.ubuntu.com/DapperGoals")[/QUOTE]

How long is Breezy supported for?

---

### Post by bruce89 on 2006-05-26
[QUOTE=youthforlinux]How long is Breezy supported for?[/QUOTE]
Antother year from now.

---

### Post by youthforlinux on 2006-05-26
will there be another release in six months?

---

### Post by bruce89 on 2006-05-26
In October - Edgy Eft it is to be called.  Ubuntu releases a new version every 6 months.

---

### Post by youthforlinux on 2006-05-26
[QUOTE=bruce89]In October - Edgy Eft it is to be called.  Ubuntu releases a new version every 6 months.[/QUOTE]
when will the testing begin?
or has it already?
will it be only supported for 18 months?

---

### Post by bruce89 on 2006-05-26
[QUOTE=youthforlinux]when will the testing begin?
or has it already?
will it be only supported for 18 months?[/QUOTE]
1.After Dapper is released
2.Yes

---

### Post by NikoC on 2006-05-26
[QUOTE=youthforlinux]when will the testing begin?
or has it already?
will it be only supported for 18 months?[/QUOTE]

Next stable release is for June 06
[http://www.ubuntuforums.org/showthread.php?t=182432]("http://www.ubuntuforums.org/showthread.php?t=182432")
Dapper is supported for 3 years.

Just a tip from a noob: You should try the 'Search' function on this forum, most of the time people already encountered similar problems which have been solved!

Edit: ppl reply quick here, when I started typing no reply was given yet ;)

---

### Post by youthforlinux on 2006-05-26
[QUOTE=NikoC]Next stable release is for June 06
[http://www.ubuntuforums.org/showthread.php?t=182432]("http://www.ubuntuforums.org/showthread.php?t=182432")
If I read correctly, this release will be supported for 3 years.

Just a tip from a noob: You should try the 'Search' function on this forum, most of the time people already encountered similar problems which have been solved![/QUOTE]
 I thought it was for June 1st:confused: :confused: :confused: :confused:

---

### Post by redistributer on 2006-05-26
if you edit your smb.conf file by default it already has all kinds of comments that explain what each feature does, it's actually alot easier to control user environments from a linux pdc.

---

### Post by gr0kzer0 on 2006-05-26
[QUOTE=youthforlinux]I thought it was for June 1st:confused: :confused: :confused: :confused:[/QUOTE]
Yes, June 1st 2006

---

### Post by youthforlinux on 2006-05-26
sweet 
**_*GO DAPPER DRAKE=+UBUNTU!!!!!!!!!!!*_**

---

### Post by Iowan on 2006-05-26
[QUOTE=gr0kzer0]Yes, June 1st 2006[/QUOTE]
I tho't I heard that the release date slipped...

---

### Post by Dr. C on 2006-05-26
This is a link on setting up Ubuntu to act as a Windows domain controller

[http://www.howtoforge.com/samba_setup_ubuntu_5.10]("http://www.howtoforge.com/samba_setup_ubuntu_5.10")

---

### Post by NikoC on 2006-05-27
[QUOTE=youthforlinux]I thought it was for June 1st:confused: :confused: :confused: :confused:[/QUOTE]

I meant 1ste June 2006, my fault, sorry ;)

---

