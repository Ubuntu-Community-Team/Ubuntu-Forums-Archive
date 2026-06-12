---
title: "/[username] and port 631 = &quot;Access denied&quot;"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by rlcramer on 2006-04-25
Hello, and thanks for reading this.

I have followed the tutorial for installing and configuring Ubuntu 5.10 as a domain server, installing and enabling CUPS and SAMBA. I am, in fact, able to access the server shares /ALLUSERS and /NETLOGON, but when I try to access either /[username] or /HOMES from my Windows XP Pro workstation, I receive a message as follows: "[directory name] is not accessible. Blah de blah blah.  Network access is denied."

Also, I receive a "403 Forbidden" error when I attempt to connect to the CUPS configuration application via a browser at the server address, as in 'http://192.168.1.100:631'

I have searched the various forums, I am searching through my copy of the Linux Bible, but at this point, I think I am in need of a clue.](*,)

---

### Post by 5-HT on 2006-04-26
I can help you with the CUPS problem (that's it I'm afraid).

For security reasons, Ubuntu blocks access to the CUPS webadmin (at least on Breezy).
The safest way (IMO) to get around this is to:
```
sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart 
``` 
That should let you access the web interface.
To remove the cupsys user and get things back to default:
```
sudo deluser cupsys shadow
sudo /etc/init.d/cupsys restart 
``` 
Hope that helps.

---

### Post by rlcramer on 2006-04-26
[QUOTE=5-HT]I can help you with the CUPS problem (that's it I'm afraid).

For security reasons, Ubuntu blocks access to the CUPS webadmin (at least on Breezy).
The safest way (IMO) to get around this is to:
```
sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart 
``` 
That should let you access the web interface.
To remove the cupsys user and get things back to default:
```
sudo deluser cupsys shadow
sudo /etc/init.d/cupsys restart 
``` 
Hope that helps.[/QUOTE]


Thanks.  Tried that and system responded that user cupsys is already a member of shadow.  I have a feeling that the access denied messages and this problem are related.  Just a guess at this point.

Thanks for the reply, though.

---

