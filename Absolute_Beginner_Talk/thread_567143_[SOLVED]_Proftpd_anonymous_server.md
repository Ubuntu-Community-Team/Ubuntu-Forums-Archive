---
title: "[SOLVED] Proftpd anonymous server"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by pognonec on 2007-10-04
Hi there,
I am NOT too familiar with UBUNTU yet, and I have to set up an anonymous FTP server using Proftpd. I went through several conf examples (some pretty unaccessible to me...), but it does not work when people try to access the server (IP ping is OK, though).
Is there  a tutorial somewhere for simple minded people like me describing STEP BY STEP how to set up such a server (anonymous access, no upload), together with all the stuff that has to be done (creating user, or group, or anonymous file, or whatever).
Thanx in advance, even though I saw on that forum that similar requests remained unanswered...

---

### Post by shankhs on 2007-10-04
Hey pognonec just check this tutorial:

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

You said you are new to Ubuntu.......
Nobody is new to "ubuntu"
It will take a few days,a few tutorials and I m sure u will enjoy Ubuntu.
Just continue posting your problems.
:guitar:

---

### Post by n3tfury on 2007-10-04
> **shankhs said:**
> 

You said you are new to Ubuntu.......
Nobody is new to "ubuntu"


um.  everyone was once new to ubuntu.  whether you're talking about the OS or its meaning.

---

### Post by shankhs on 2007-10-04
hi n3tfury
Its an individual's point of view.
:)

---

### Post by pognonec on 2007-10-08
The FTP anonymously lost guy again.
Thanx for the link (one of the ones I was mentioning, that unfortunately did not allow me to solve my problem). 
I tried and tried again, with many .conf examples found on the web, but nothing worked.
May be I am screwing up at a different level?
Could it be some "secret" settings on the network configuration panel that I did wrong? (but my LAN and internet work fine).
Is there by default a firewall in Ubuntu 7.04 that could block access to the FTP server?
I really would like to avoid having Bill as my only vista...

---

### Post by hyper_ch on 2007-10-08
Have a look at the FTP section over at [http://www.howtoforge.com](http://www.howtoforge.com)

They have some really good tutorials that are (mostly) just copy'n'paste

---

### Post by pognonec on 2007-10-11
Good news, I got my proftpd server running. The problem was that I did not associate my IP address properly in the System/Network Settings/Hosts section. Now, when I log in my IP, enter my user name and password, it's a breeze!
But I still encounter a little problem:
I want anonymous FTP login too, restricted in the directory home/FTP/anonymous, for download only. Nothing else.
I created a user (anonymous) and a group (anonymous) in which I put this user.
I created in the home directory a directory (FTP) in which their is another directory (anonymous) with the stuff I  want accessible to the world.
When I log in , I get an error 530.
Where is my mistake? Wrong path? What should it be?

The config file for the anonymous part is:
<Anonymous /home/FTP/anonymous>
  User				anonymous
  Group				anonymous

  # We want clients to be able to login with "anonymous" as well as "ftp"
  UserAlias			anonymous ftp

  # Limit the maximum number of anonymous logins
  MaxClients			10

  # We want 'welcome.msg' displayed at login, and '.message' displayed
  # in each newly chdired directory.
  DisplayLogin			welcome.msg
  DisplayFirstChdir		.message

  # Limit WRITE everywhere in the anonymous chroot
  <Limit WRITE>
    DenyAll
  </Limit>
</Anonymous>

---

### Post by grim4593 on 2007-12-23
bump

---

### Post by pognonec on 2008-04-16
This is a follow up and to close the thread:
I definitively could not get the anonymous to work with ProFTPd. I thus installed Very Secure FTPd, and everything worked flawlessly right away...
Both registered users with passwords, as well as anonymous, restricted to an anonymous FTP folder.

---

