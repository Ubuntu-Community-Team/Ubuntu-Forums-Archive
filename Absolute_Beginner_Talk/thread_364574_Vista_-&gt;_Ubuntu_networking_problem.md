---
title: "Vista -&gt; Ubuntu networking problem"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by draculashaun on 2007-02-18
I'm a total n00b with 'nix, but I've installed ubuntu desktop 6.10 and started to get things working reading through the other posts here...

I've got samba and followed a tutorial ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) on installing & configuring it...

I can see the 'Windows Network' in Network Places OK, and the DRACDATA workgroup is visible fine, and I can even see the //VISTA-SERVER and //XP-SLAVE boxes...

 I can put things into the shared directory on the ubuntu box (/home/samba) from either the XP-SLAVE or VISTA-SERVER machines, and I can view shared directories on the XP-SLAVE box fine...

The problem is that I can't access the network shares on the vista box from the ubuntu one.
I can try, but all I get is a dialog box titled 'Authentication Required', which states 'You must log in to access guest@vista-server', then asks for a username, domain and password.

I figured it would be asking for the username and password of a user account on the vista box, but none (including Administrator) seem to work, and there is no domain... The vista box is merely a workstation. (With about 600GB of multimedia that I wanted to be able to access from the whole 10gb-hdd linux machine :P)

Any ideas?

-Shaun.

---

### Post by jonathan.lees on 2007-02-18
In the domain field do you have DRACDATA?

---

### Post by draculashaun on 2007-02-18
I've tried that, yes, but it won't accept that either.

---

### Post by victor_c26 on 2007-02-19
Apperantly Microsoft created a new standard called SMB2. So until Samba get's updated with the new standard, we're going to have to use XP to transfer files over to our Linux boxes.

---

### Post by pgilmon on 2007-02-19
Well, perhaps Vista includes SAMBA2, but I guess that if it has to transfer files to/from a W98 box it would use SAMBA to ensure compatibility. So I don't see why it wouldn't work with ubuntu...

---

### Post by n8bounds on 2007-02-19
Get used to this.  Microsoft constantly tries to make it hard on the open source community...its never ending.

---

### Post by Mithrilhall on 2007-03-12
[http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746](http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746)

---

### Post by drvista on 2007-08-01
it's ubuntu problem i use freespire with no network problem at all

---

