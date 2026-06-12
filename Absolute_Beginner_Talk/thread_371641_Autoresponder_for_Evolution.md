---
title: "Autoresponder for Evolution?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Monsieur le Comte on 2007-02-27
I've looked around for a way to get autoresponding going in Evolution.  Is there a plug-in that I'm not finding that will work in Edgy?

If there isn't any such thing I suppose it would be possible to write a perl script to telnet in to my ISP's mail server and compose a message.

The end-goal is to be able to mail an account of mine from work and have it respond from home so that I can get my home network's external IP address (it's not a static IP).

If there is any other way to do this, it would be much appreciated.

---

### Post by Monsieur le Comte on 2007-02-27
So here is what I chose as a solution:

(of course, web address, username and pass are all replaced and the shell script is made executable)

```

#put output of ifconfig into ipaddress.txt
ifconfig > ipaddress.txt

#FTPing in to site
ftp -n <web address> <<End-of-Session
user <username> "<password>"
binary
bell

# Move to a subdirectory called 'ip'
cd ip

#upload address
put ipaddress.txt
bye
End-of-Session

exit 0

```

Then I used Evolution's ability to execute a command when e-mailed a certain subject line.


So, now when I want to get my home IP I simply mail an e-mail acct with certain text in the subject line and my IP is uploaded to a storage area.

---

