---
title: "File sharing question?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Onay on 2007-10-26
Myself and my brother have files that we like to transfer between us, but it's so annoying to have to upload it by torrents or use a free uploading site. Is there anyway that I can just see certain files of his and visa versa while we're both on the computer? Is there some private file sharing without having to have a home server? Is there anyway that I can password secure it or only "turn it on" when I need it?

---

### Post by Dr Small on 2007-10-26
I really do not understand what you really want to do....
Maybe SAMBA, FTP or SSH ?

---

### Post by MegaJim on 2007-10-26
Just to set the scene.  You and your brother are not on the same network?  You are in different cities or something?

---

### Post by Onay on 2007-10-26
Similar to FTP I guess...

For example, he can connect to my "network" and access certain files for viewing/downloading. What is Samba anyway?

---

### Post by n3tfury on 2007-10-26
sounds like it.  i'd say go with ftp

---

### Post by Dr Small on 2007-10-26
Setting up a simple ftp server with gproftpd and proftpd should do it.

---

### Post by Onay on 2007-10-26
Can I just install those and they work? I should probably stop asking questions and do more searching.

Thanks for the help.

---

### Post by Dr Small on 2007-10-26
> **Onay said:**
> Can I just install those and they work? I should probably stop asking questions and do more searching.

Thanks for the help.
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by Onay on 2007-10-26
Do I need to have a server in order to use this?

---

### Post by Dr Small on 2007-10-26
No, not at all. You can install those packages on any Ubuntu system ;)

---

### Post by Onay on 2007-10-26
And how do others access this ftp network?

---

### Post by Dr Small on 2007-10-26
They will need either a FTP Client, or use the one built into gnome.
Then connect to *ipaddress* with the username and password you specify in gproftpd.
You can also setup a directory to where everything is uploaded / downloaded to.

Dr Small

---

### Post by Onay on 2007-10-26
1. Where is gnome's build in client? I'm pretty sure that the terminal server client is for remote desktop stuff, not ftp...
2. How do I set up that directory? I want it to be /home/ftp, but the GUI keeps setting it to /var/ftp, which doesn't even exist.

Sorry if I sound dumb, I have never configured anything like this before.

---

### Post by Dr Small on 2007-10-26
> **Onay said:**
> 1. Where is gnome's build in client? I'm pretty sure that the terminal server client is for remote desktop stuff, not ftp...
2. How do I set up that directory? I want it to be /home/ftp, but the GUI keeps setting it to /var/ftp, which doesn't even exist.

Sorry if I sound dumb, I have never configured anything like this before.
1.) Gnome's built in FTP Client can be found, by first launching Gnome, and clicking File > Connect to Server.
Select Public FTP, enter the details, and connect.
A folder will then be placed on your desktop to quickly access it.

2.) To get gproftpd to change a directory on one of your users, (i had this problem too), try to "Deactivate" (from the button at the top), change settings, and then click "Apply", then "Activate".

---

### Post by Onay on 2007-10-26
Ugh I'm so frustrated. Can people access these files anywhere in the US kinda thing, or is it just for the computer's users...?

---

### Post by Dr Small on 2007-10-26
Both. Computer users and anyone in the world, who has the proper credentials, can access your FTP server.

You must open port 21 (FTP Port) on your firewall and router (if you have one), in order for incoming traffic to access your FTP server, though.

Dr Small

---

### Post by n3tfury on 2007-10-26
you setup who you want to access it.  i hope you're following that guide that was linked on the first page.

---

