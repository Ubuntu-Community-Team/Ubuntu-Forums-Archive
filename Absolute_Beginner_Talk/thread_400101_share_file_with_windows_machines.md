---
title: "share file with windows machines"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by rockymaxsource on 2007-04-03
Hey,

In my office, all of my co-workers are using windows and I'm the only one using Unbuntu. There is a WIndows XP file server in out office which we can access the shared partition by entering \\server or \\192.168.1.15. But in my ubuntu firefox browser \\server or \\192.168.1.15 gives me the error of not found. Can any of you help me on the follwoing issues please?
[LIST=1]
[*]How can I access our file server please?
[*]How can I set up my Ubuntu machine to share files with my co-workers?
[/LIST]  

Thanks in advance!
Rocky

---

### Post by thelinuxguy on 2007-04-03
Samba is one way in which you could do this. Navigate to section 1.19.5 at [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

> 
How can I access our file server please?

I don't think Firefox can parse addresses such as \\192.168.1.15.
Use Places >> Network Servers to connect to the windows shares in your network

> 
How can I set up my Ubuntu machine to share files with my co-workers?

Try setting up a Samba server using the link above. After Samba is setup correctly, your co-workers will be able to browse your shared folders just like they browse any windows machine with shared folders.

---

### Post by mikeyphi on 2007-04-03
> **rockymaxsource said:**
> Hey,

In my office, all of my co-workers are using windows and I'm the only one using Unbuntu. There is a WIndows XP file server in out office which we can access the shared partition by entering \\server or \\192.168.1.15. But in my ubuntu firefox browser \\server or \\192.168.1.15 gives me the error of not found. Can any of you help me on the follwoing issues please?
[LIST=1]
[*]How can I access our file server please?
[*]How can I set up my Ubuntu machine to share files with my co-workers?
[/LIST]  

Thanks in advance!
Rocky

You need Samba on Ubuntu to fileshare (if not already installed) look here for in-depth advice  [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_browse_network_computers](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_browse_network_computers)

---

### Post by Ubluedog on 2007-04-03
i gather your network card is setup ok , can you open a terminal and ping the server?
ping 192.168.1.15

see if you dont get replies , might be a network card installation problem, with something not set right in your configuration of it.
cheers

---

### Post by useResa on 2007-04-03
Sharing files/folders from Ubuntu can be done by using **Samba**

A -- IMHO -- a clear HOWTO on how to set this up is written by Stormbringer:
[HOWTO: Setup Samba peer-to-peer with Windows](http://www.ubuntuforums.org/showthread.php?t=202605)

I hope this HOWTO can help you solve your issue.

---

### Post by rockymaxsource on 2008-01-29
Hey Guys,

Thank you all for your reply! Yes your advise works! Sorry for the super late reply!

Blessings,
Rocky

---

### Post by oedha on 2008-01-29
may i join.......
this case is the case like mine couple weeks ago. check o
[http://ubuntuforums.org/showthread.php?p=4177548](http://ubuntuforums.org/showthread.php?p=4177548)

i suggest not to use places > connect to server
because it only applied for copy/paste/delete
have you try to save directly from firefox or gimp ?
the link was not appear on the nautilus......
but it will be ok if you save from openoffice

maybe you can try just like mine.......
but first...you have to install smbfs : sudo apt-get install smbfs

regards;
~E~

---

