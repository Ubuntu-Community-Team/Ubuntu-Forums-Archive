---
title: "Do i understand this and Is this secure?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by StRiFe10101 on 2007-07-20
So if i understand the vsftpd config properly when you set local_user=YES it makes it so any user that has an account on the ubuntu box to be able to login using a username and password.  Onced logged in the user is "jailed" to their directory /home/username and with write_enable=YES and anon_write=NO (i know that is not the exact wording) the ftp server should have a directory /home/ftp/opendir where all the 
anonymous logins go for read only access while users have read write access in their home directories.
is that correct?  If not please correct me.  

also, how secure is this?  fairly?  should i have to worry about anything.  i'm not going to have vital info on it but i would jsut like to know what i would have to do if i did have sensitive info to secure later on.

Also... another security question.  I have vsftpd running with the configuration somewhat explained above(almost default) and it is used just for file sharing amongst friends and family.  Now, the easiest way for me to move things around in my ftp files (between user and anonymous folders s) is from a different windows box on my home lan. So i have to have all the anonymous ftp folders and user home directories shared with samba.  With this enabled is there anyway someone could access the rest of my computer (shared stuff) having my FTP folders shared with samab?  Now i mean access this stuff from the internet not from my home lan, that is different senario.  i hope you all can understand my question. 

Thanks for you time helping me understand Linux/Ubuntu.

---

### Post by Raineer on 2007-07-20
When I was setting up vsftpd several months ago I went through many google results and was darn impressed at some of the feedback.  After reviewing the information out there I highly recommend it as a ftp solution, at least security-wise.  I've seen quite a few posts about how it's tricky to setup (eh?) but I think that's just from a lack of a GUI.  I'm sure there might be some advanced features it is missing, but from a simple FTP server perspective I think it's great.

I'd have to go back through the config file to ensure all those settings you mentioned are correct, but yes it's possible to make one directory for anon and have it be jailed and download-only.

---

### Post by asmoore82 on 2007-07-20
anonymous FTP is very safe; however ...

**__NEVER__** login as a local user over ftp across the internet; FTP usernames and passwords are not encrypted and I cannot be more serious when I say PEOPLE/MACHINES **__ARE__** LISTENING !!!!!

backstory...

i logged in as a local user over ftp from a computer lab at a small private college to a computer in my bedroom in Podunk, USA just 30 min. away by car. I just got a few favorite mp3's... this was at about 11:30pm.
By 6:30pm the very next day, a **__ROOTKIT__** was dropped in place on the computer in my bedroom but
not yet activated ==> computer reformated > no real harm done > lesson learned

I have since gotten many-a-file over the wide internet from that same computer by logging in securely via ssh and linking the need files to the anonymous ftp directory and then connecting via anonymous ftp and downloading the files. Also keep in mind that using this method anyone can connect after you and get a copy of the files. i.e. they can't harm your ftp compy directly but the files may contain sensitive info.

if you are not looking for a real full-time FTP solution and just in need of a few files here and there i would
```
~$ man scp
``` and use that; all it requires is for a ssh server to be running. Also there is a free,
working Windows version "pscp.exe" at [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by StRiFe10101 on 2007-07-20
So, if i understand what is said, that an anonymous connection is ok because it's read only... but don't connect using user accounts because people will get you password and either delete things or upload things to mess everything up?  And also what i get is you would use a remote (secure) connection to connect to your machine, move files to your anonymous ftp dirctory then disconnected and then downloaded it via ftp?

that sounds like a little more work and not as easy to use with multiple users if they wanna upload things... hummmm.  that that $man scp thing is a remote connection? i don't understand what that does for me. please explain.  

So, i really don't have any other option to allow friends and family to upload things but through ftp.  is there a different ftpd that allows password encryption or any other ideas?

---

### Post by StRiFe10101 on 2007-07-20
just thinking. could you get around the idea of someone giving you a virus by making the ftp user directories read and write only... so you can't execute a file from there.  Or is that possible because it's a user home directory? sorry if this sounded dumb.  anyone can set me straight if i'm way off?

---

### Post by asmoore82 on 2007-07-20
you don't have to worry about viruses for linux...
but with ftp-ing and passwords flying around you have stop your machine from becoming "compromised"
I.E. someone beeing able to login whenever/wherever they want without your knowledge.

open a terminal and type ```
man scp
``` to read about the safest way to move files around.

oh and all the security stuff only becomes an issue if you are going to let people do stuff across the internet....
if the setup is just for LAN/Home use you can do about anything you want and not worry about it.

---

