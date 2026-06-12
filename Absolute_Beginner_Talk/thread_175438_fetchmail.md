---
title: "fetchmail"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by skippy81 on 2006-05-13
Hi, I want ubuntu to regulary download my email from a pop server.  At the moment I am typing 

> fetchmail -d 300

Into a terminal when i log in and it is working.  I understand that I could just make a script, but isnt there a more 'integrated' way of doing this?  Fetchmail shows up as a 'service' in gnome, even before I have started the daemon, is this normal?  I notice that before I manually start the daemon fetchmail is nowhere to be found in my pstree.  

Thanks.

---

### Post by MacMan on 2006-07-09
> **skippy81 said:**
> I understand that I could just make a script, but isnt there a more 'integrated' way of doing this?

You can set it up to start as a service at boot. Those are the steps you can follow:

1) Stop fetchmail:
```
$ skill fetchmail
```

2) You should have a file called fetchmailrc somewhere in your system. I guess it is in your home and called .fetchmailrc but I'm not sure: so try to find it using this command:
```
$ find ~ -name "*fetchmailrc*"
```
You have to move that file in your /etc directory, change its owner to "fetchmail", and make it readable only by its owner. You do:
```
$ sudo cp <name of file you found> /etc/fetchmailrc
$ sudo chown fetchmail:root /etc/fetchmailrc
$ sudo chmod 600 /etc/fetchmailrc

```

3) Tell Ubuntu you want fetchmail to start at boot: you should edit the file called /etc/default/fetchmail, for example using this command:
```
$ sudo nano -w /etc/default/fetchmail
```
The file should read:
```
# This file will be used to declare some vars for fetchmail

# Declare here if we want to start fetchmail. 'yes' or 'no'
**START_DAEMON=yes**

```

4) Now fetchmail should start automatically at boot. You can stop and restart the deamon using invoke-rc.d. For example to start fetchmail you can type:
```
$ sudo invoke-rc.d fetchmail start
```

That should do the trick. I hope this helps.

Ciao.
-- 
MacMan

---

