---
title: "Ubuntu and ActiveDirectory"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by elnur on 2007-10-16
Hi. My company uses Windows and Active Directory. When I power my PC up I login to the domain in Active Directory. But I'm going to install Ubuntu on my PC.
Please tell me, will I still be able to login to that domain and, if yes, how?

---

### Post by Chilli Bob on 2007-10-16
I hate networking, don't understand it, and want nothing to do with it, but I believe you want a program called Samba.  Check this link and see if this is the sort of thing you are after.

[http://www.enterprisenetworkingplanet.com/netos/article.php/3487081](http://www.enterprisenetworkingplanet.com/netos/article.php/3487081)

or

[http://www.wlug.org.nz/ActiveDirectorySamba](http://www.wlug.org.nz/ActiveDirectorySamba)

---

### Post by elnur on 2007-10-16
Thanks, **Chilli Bob**, seems like that's what I need. I'll try this couple days later after Gutsy final release.

Any additional ideas are welcome!

---

### Post by imog on 2007-10-24
In my understanding, Samba does not/willl not join you to Active Directory - I could be wrong.  It will allow you to access shared storage on a Microsoft or CIFS-enabled server.  [Read here for gory details that probably dont interest you]("http://en.wikipedia.org/wiki/Cifs").

Samba is an SMB client that is compatible with the SMB protocol implementation used to connect to Shares on a Microsoft server.

Ubuntu includes SMB (Samba) support built in, so with a default Ubuntu install connecting to a Microsoft server volume is very easy.  Select connect to server from the drop down in the top left of ubuntu, then select windows share, then enter the appropriate information.

To actually make your Ubuntu PC a member of Active Directory (AD), like the Windows PCs in your office where it authenticates against AD when you login... I was searching for a good guide/explanation when I found this thread.

---

### Post by ddoctor on 2007-10-28
> In my understanding, Samba does not/willl not join you to Active Directory - I could be wrong. 

Samba DOES enable a Linux computer to join an Active Directory domain. It provides an implementation of the "net use" command, to do this. 

However, a lot of AD functionality is not available, eg Group Policy.

You can, however, log on to a Linux desktop machine using an AD user, and connect to CIFS shares without re-authenticating (via Kerberos).

Most of the cifs stuff is done by smbfs and smbd. The network logins are handled by a samba component called "winbind", along with Linux PAM (Pluggable Authentication Modules), and NSS (name service switch (?), which does group/username-to-id resolution. 

Winbind also now handles the kerberos side of things, so you don't have to deal with kerberos in your PAM configuration.


Using Linux with AD is possible, but its a pain to set up. For me, its worth it, but lots of work. There are a bunch of HOWTO's floating around.

---

