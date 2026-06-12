---
title: "File Share b/t Ubuntu and XP"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by prismhdd on 2008-03-04
I'm a new ubuntu user and need a help in networking b/t Ubuntu and XP.

I have 1 Desktop with Ubuntu 7.10 (Gutsy), and 3 other PCs with XP. I installed samba and was successful with sharing Ubuntu folders FROM XPs. However, for some reasons, I can't connect TO XPs FROM Ubuntu even though all the XP computers are shown in Places>Network panel. When I double-click a computer, it says "The Folder Contents Could Not Be Displayed"

I did network settings and shared folders....
I tried to turn off firewalls on XPs but it didn't work as well. (same message)
I set up the smb.conf file and smbpasswd as posted.

followings are my smb.conf changes from original conf file :

workgroup = myworkgroup
sercurity = user
browseable = yes
writable = yes

I spent all day searching for this answer but couldn't find it...:confused:
I hope you guys can tell me what I am missing.

Thank you in advance.:)

---

### Post by AvalonSkies on 2008-03-04
Hi Prism,

I just tried this to see the message you're talking about.

Are your XP systems asking you for credentials? When the Samba stuff asks you for a username and password, make sure you're logging into your WinXP system with the same username/password combo you'd use on Windows.

I haven't edited any Samba configuration files, this is a fresh install I'm toying with right now.

---

### Post by prismhdd on 2008-03-04
It doesn't ask me any id or password.....:(

---

### Post by AvalonSkies on 2008-03-05
> **prismhdd said:**
> It doesn't ask me any id or password.....:(

Huh. That... um, probably shouldn't be happening. If it's XP Professional, it definitely shouldn't be happening. Computers who let everyone and everything browse their filesystems aren't... aren't so great.

I can think of a few things I'd check.

[LIST]
[*]You *do* have shared folders on the computer you're trying to access, right? (I'm not even sure this would make a difference, but it's worth checking.)
[*]If Samba is automatically filling in credentials somehow, those credentials might be wrong. If you set something up like that, double-check it.
[/LIST]

...I guess maybe if you're using some ye olde pre-SP2 unpatched version of Windows XP Home, it would make sense to me that it's not asking you for a username/password.

Also, I don't know what edits you made to your Samba config file, but it may help you to know that I didn't have to make any edits to mine to get to-WinXP-from-Linux filesharing to work with my system.

Do you know if Windows-to-Windows filesharing works with the computer you're using?

---

### Post by paydaydaddy on 2008-03-05
Check out this link for the best how-to I have seen on setting up samba shares.
[http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer](http://ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer)

---

### Post by prismhdd on 2008-03-05
I get it!!! when I tried to mount WIN BOX using smbclient, it says NT_STATUS_ACCESS_DENIED...

I tried to connect to XP box which doesn't have any password, and it worked
but when I try to connect the XP with password I can't, and it doesn't even ask me a userid or password for XP box....

Can anyone help me on this??

---

