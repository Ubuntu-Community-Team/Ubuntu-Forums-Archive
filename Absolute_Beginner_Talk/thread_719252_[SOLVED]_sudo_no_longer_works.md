---
title: "[SOLVED] sudo no longer works"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Riffer on 2008-03-08
[SIZE="2"]Am running Hardy.  And after trying to setup my samba shares everytime I try and us sudo I get and error message "unable to resolve host "my computer name".

What crazy thing have I've done now?  :lolflag: [/SIZE]

---

### Post by dcstar on 2008-03-09
> **Riffer said:**
> [SIZE="2"]Am running Hardy.  And after trying to setup my samba shares everytime I try and us sudo I get and error message "unable to resolve host "my computer name".

What crazy thing have I've done now?  :lolflag: [/SIZE]

System-Administration-Network-Hosts and put in a single name (that makes sense) for 127.0.0.1

---

### Post by InfinityCircuit on 2008-03-09
In other words, the first two lines of /etc/hosts should looks like this:

127.0.0.1 localhost youronewordhostname
127.0.1.1 youronewordhostname

If that doesn't work, the next step is to reboot into single user mode, which will log you in as root, and then delete the file /var/run/sudo/* and then reboot again.

---

### Post by Riffer on 2008-03-09
[SIZE="2"]ok that work thanks guys.  Just 1 more question.  Where do I add my workgroup name?[/SIZE]

---

### Post by jordanmthomas on 2008-03-09
> **Riffer said:**
> [SIZE="2"]ok that work thanks guys.  Just 1 more question.  Where do I add my workgroup name?[/SIZE]

I don't know if Ubuntu has some magical GUI that does it for you, but I personally just edit /etc/samba/smb.conf.  In it there's a line that says 
```
workgroup = SOMETHING
```
Change it to what you want your workgroup to be and save the file.
Then I'd restart samba (may not be needed, but whatever)
```
sudo /etc/init.d/samba restart
```

Hope this helps.

---

### Post by Riffer on 2008-03-09
[SIZE="2"]Thanks guys.  And yes editing the config file works, I followed the HOWTO.
[/SIZE]

---

### Post by MinceMedallion on 2008-04-26
> **dcstar said:**
> System-Administration-Network-Hosts and put in a single name (that makes sense) for 127.0.0.1
I had this same problem following upgrade to Hardy from Gutsy. Following the instructions above I went System > Administration > Network > Hosts. Select 'unlock' which will require your password. In 'Properties' for the first line 127.0.0.1 I amended the host name from 'localhost' to 'localhost youronewordhostname'. Back out and hey presto - sudo works again. Check /etc/hosts to read the line '127.0.0.1 localhost youronewordhostname' as confirmation. Thanks for the help.

---

### Post by new2GNU on 2008-05-05
> **MinceMedallion said:**
> I had this same problem following upgrade to Hardy from Gutsy. Following the instructions above I went System > Administration > Network > Hosts. Select 'unlock' which will require your password. In 'Properties' for the first line 127.0.0.1 I amended the host name from 'localhost' to 'localhost youronewordhostname'. Back out and hey presto - sudo works again. Check /etc/hosts to read the line '127.0.0.1 localhost youronewordhostname' as confirmation. Thanks for the help.

Thanks for your help this worked great for me!!

---

