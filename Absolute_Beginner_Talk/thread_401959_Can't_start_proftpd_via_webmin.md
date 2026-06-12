---
title: "Can't start proftpd via webmin"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by fatphilthethird on 2007-04-05
Hi 

Really not sure this is the right place to ask this but here goes.

I've installed a LAMP server on an old box and am administering it through webmin. I've installed proftpd through webmin but when I try to start the ftp server I get the following error:


> Failed to start FTP server :

 * Starting ftp server proftpd
 - no such user 'proftpd'
 - Fatal: User: Unknown user 'proftpd' on line 44 of '/etc/proftpd/proftpd.conf'
   ...fail!

Noob question: does this mean I need to add the user proftpd? If so, do I need to add it to /etc/passwd or is it somewhere else?

Cheers

Fat

---

### Post by richbarna on 2007-04-06
I think you have somehow got proftp set as the user in the config file.

To check it, open your terminal/console and copy and paste this command:_
> sudo nano /etc/proftpd/proftpd.conf

Then look at this part of the file:-
>  ServerName                      "fatphilthethird"
ServerType                      inetd
DefaultServer                   on

SystemLog                       /var/log/proftp
Port                            21
Umask         006
MaxInstances                    30

 User                            **nobody**
Group                           **nobody**

 RequireValidShell off

 # Normally, we want files to be overwriteable.
<Directory /*>
    AllowOverwrite                on
</Directory>

And see if where it should say nobody, it says proftpd.

The other thing I notice is that you have it installed in the etc/proftpd directory, whereas I thought by default proftp installs in the /usr/local/etc directory.

Here is a link to the [proftpd forums]("http://forums.proftpd.org/smf/"), just in case.

---

