---
title: "pureftpd how do I make home dir on a mounted drive"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by sheepfunk on 2006-12-02
My basic question is, if I'm running a PureFTP server how do I make the home directory of a user be on a mounted drive? 

I'm trying to create an ftp server so my friends can gab stuff off an external hard drive of mine, but 

whenever I make an ftp user who's home directory is on my external hard drive they get this error every time they try to log in:

550 Can't change directory to /: Permission denied

I'm currently using the pureftp server software with virtual user authentication, which I setup via the steps at [https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP). I also tried to create the same setup with ProFTPD to no avail.

Any advice ya'll have to offer would be much appreciated.

---

### Post by biffta on 2006-12-02
What's in your /etc/passwd file? Specifically the line regarding the user account who your friend is trying to login as. It could be that their home directory is incorrectly set.

Further to that, try taking things back a few steps. What happens when you try to login as this ftp user locally?

$ su - remoteusername

Do you get the permission denied error then? If not what directory are you in? Can you cd to the external disk?

---

### Post by sheepfunk on 2006-12-05
Thank you very much for responding, hope I didn't lag to much getting back to you.

In my /etc/passwd file there is one user called ftpuser and their line in /etc/passwd looks like this:

ftpuser:x:1001:1001::/dev/null:/etc

I use a command called pure-pw to create passworded acounts the don't have entries on my server, so I'm guessing when I log in to my ftp server it's pretending to be ftpuser for a minute and then acessing the password file for authentication. I have UnixAuthentication set to no in my config directory. 

Since the user I'm trying to ftp with isn't a user on the rest of the server I can't $su remoteuser.

When I ssh into my server and then ftp to localhost with the ftp user I'm having problems with, my user is able to log in, but I can't run the ls command once I'm ftp'd in, which is making it hard for me to figure out where I am. Here's what the ssh to ftp process looks like.  


ftp localhost
Connected to localhost.
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 23:11. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
/dev/null/.netrc: Not a directory
Name (localhost:root): MYPROBLEMUSER
331 User MYPROBLEMUSER OK. Password required
Password:
230-User MYPROBLEMUSER has group access to:  1001
230 OK. Current directory is /
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful
150 Connecting to port 52334
226-Sorry, we were unable to read [.]
226-Options: -l
226 0 matches total
ftp> cd ..
550 Can't change directory to ..: Permission denied
ftp> pwd
257 "/" is your current location


Also I can't seem to chmod the home directory of MYPROBLEMUSER or anything on the mounted drive for that matter.

---

### Post by sheepfunk on 2006-12-05
damn emoticons, that line in /etc/passwd looks like this

ftpuser: x:1001:1001::/dev/null:/etc

---

### Post by biffta on 2006-12-05
> damn emoticons, 
I thought ftpuser was looking a bit angry!

basically I think the ftpuser account has a home directory of /etc which really does not sound like a good idea. The ftpuser probably does not have any read/write permissions to /etc (which he shouldnt do really!) so after he logs in he is in a position where he cannot really do anything.

Have you tried ftp'ing in as yourself (your default account)? Does that work ok?

> Also I can't seem to chmod the home directory of MYPROBLEMUSER or anything on the mounted drive for that matter.
What do you think his home directory is? Because I think it is /etc. If you edit the passwd file i.e.

gksudo gedit /etc/passwd

and change the bit of the line with the ftpuser on 
from /etc to /remotedrive/ftpuser

Then again from the command line
mkdir -p /remotedrive/ftpuser
chown ftpuser /remotedrive/ftpuser

Obvioulsy you might need to replace "remotedrive" to the place where all your stuff is.

See if that gets you any closer.

---

