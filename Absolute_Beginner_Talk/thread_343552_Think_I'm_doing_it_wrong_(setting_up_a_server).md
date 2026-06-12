---
title: "Think I'm doing it wrong (setting up a server)"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by peejaygee on 2007-01-21
Dear All, 

I'm looking for some steps to follow from an experienced user please.. I'm posted in here a few times, and what I'm trying to do is replace my Windows2k Server machine with a linux box running Ubuntu Server Edition.

So far, I'm installed OS, installed GUI, changed my ip details, added drives as shared, installed Samba, and I can see the linux box in "My Network Places" on windows and if I go into it I can see netlogon and profiles, but I can't go any further as I think I've set the users up wrong. (using smbpasswd -l -a [user])

What I'm trying to do at present, is run both my Win2k Server box, alongside the Linux box, untill I'm happy with the set up, and running programs etc. and then remove the Win2k Box

But for the life of me, when I start my machine up, or log off my current session on my WinXP machine, I can't see the Linux Box in the lists of available Domains, and I don't know how to refresh it? (I hope all this makes sense)

I've read something about, needing the users in there, but I can't get it to broadcast to allow me to attempt to logon (and expect a failed attempt).

I've perused [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/configuring-samba.html) and I think, I've done what it is asking me to do. Is there more I should be doing?

Am I barking up the wrong tree, I'm guessing there is something blatantly obvious I've forgotton...

Can anybody point me in the right direction please, or a Easy, Step by Step guide. 

Thanks in advance.

Paul.

I've also tried to follow the instructions at [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10) but even that doesn't help me, I still don't see the server listed in my WinXP dropdown at the CTRL_ALT+DEL logon page...

---

### Post by crispy_420 on 2007-01-22
So what exactly do you want? Your final setup?

A file share?

FTP?

Print server?

---

### Post by peejaygee on 2007-01-22
> **crispy_420 said:**
> So what exactly do you want? Your final setup?

A file share?

FTP?

Print server?

My final setup, I would like a user on a XP machine to enter a username and password, and they can logon, applying policy settings to the user.

There will be file share for certain users, I'm going to install Squid so certain things can be blocked by putting a proxy in their IE settings and not in other users.

I'd like a printer server to allow monitoring of printed documents.

Ideally I'd like a email server, so I can reduce my ISP's bandwidth usage, as I could send big files internally.

I'm not that bothered about a FTP server, but if it is there it would probably be used..

I'd eventually like to set up a repository (but that can be done at a later date)

I'd like a bandwidth limiter, so I can restrict users usage and applications running on the server, as I'd ideally like an emule equiviant running.

I'd like a similar program to mIRC, as I run a bot in a friends channel.

I've already installed SAMBA and SWAT, have Webmin installed and ISPConfig (but I'm thinking now I won't need ISPConfig, as I'm not planning on hosting websites yet)

one problem, I can't get the server to list in my XP machine logon screen, even though I've called it a different name to my currently running server on a NT box.

I'm fairly quick to pick things up, and fairly computer litterate, but as I'm new to Linux (as such) I maybe expecting more than I can get

Since my first post, I've done a re-install, and I'm not bothering with a GUI just yet, I'm trying to get it running from command prompt, and then possible install a GUI when I know it all works...I've also user [http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10) for reference.

Hope all that makes sense....

Regards
Paul.

---

### Post by chalex on 2007-01-22
For samba, I've found the samba book to be helpful: [http://samba.org/samba/docs/man/Samba-Guide/](http://samba.org/samba/docs/man/Samba-Guide/)  You probably want to read the "simple scenario" chapter.

For a print server, you want to install cups and the associated programs, and then use the CUPS web interface to configure the printers and then point the Windows machines at those printers.  There's probably a nice tutorial that you can find through google.

---

