---
title: "How do I use http://localhost:631/admin? The root password doesn't work . . ."
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by MatthewJS on 2007-10-17
. . . when I try and change the printer settings. I try to put in the root username and password, as I did with Fedora, but I get:

> 401 Unauthorized

Enter your username and password or the root username and password to access this page.

I tried to effect the changes suggested in the thread:

[http://ubuntuforums.org/showthread.php?t=54007](http://ubuntuforums.org/showthread.php?t=54007)

but I don't have the user "cupsys" and a group "shadow" they refer to.

Regards

Matthew

---

### Post by dwhitney67 on 2007-10-17
set your root password.

$ sudo passwd

Then try the HTTP CUPS interface again, and when prompted for the user id and password, enter root and the root-password... same as in Fedora.

---

### Post by MatthewJS on 2007-10-17
There's no question about the password! I am definitely using the right password!

---

### Post by hyper_ch on 2007-10-17
By default, the root account is disabled - meaning there is no password set. The above given command does set a password for the root account and hence enabling it ;)

---

### Post by MatthewJS on 2007-10-17
Worked. Doesn't make sense to me though since I've been using root privileges in many other contexts and using the password I gave and they all worked.

Thx 

Matthew

---

### Post by hyper_ch on 2007-10-17
sudo != root

---

### Post by MatthewJS on 2007-10-18
Thx

---

### Post by sdb2028 on 2007-10-20
I am having the same problem as outlined in this thread, however, following the instructions has not resolved the problem. I still cannot get past the modification password request box. I am using Dapper. Any suggestions. Also, what exactly are they asking for in the Device URI field. How do I find the hostname?
Examples:

    [http://hostname:631/ipp/](http://hostname:631/ipp/)
    [http://hostname:631/ipp/port1](http://hostname:631/ipp/port1)

    ipp://hostname/ipp/
    ipp://hostname/ipp/port1

    lpd://hostname/queue

    socket://hostname
    socket://hostname:9100

---

### Post by dwhitney67 on 2007-10-20
Those are merely examples of what a URI would look like.  As system administrator, you _should know_ what the IP address is of your printer.  If you do not know, then you should take one step back to find out before proceeding with CUPS.

Once you have determined the IP address of your printer, you can key it in directly with the URI.  For example:  lpd://<ip address>/lp1

Or alternatively, you can add the IP address to the /etc/hosts files, then specify the URI something like: lpd://printerIPAlias/lp1

---

### Post by sdb2028 on 2007-10-21
I realize those are only examples, and I do know the IP address of my printer. The question is- how do you get through the password request stage when modifying the printer. I have a root password, it works fine in the terminal, however the cups page won't except it. 
Here are some screenshots of what happens when I try to modify the printer, and thats as far as I get. I click on Modify Printer, A box opens asking for user name and password, I have try'd both my standard login name/password and the root login/password, niether af which is accepted.
Any suggestions?

---

### Post by dwhitney67 on 2007-10-21
It seems odd that the CUPS config tool wouldn't accept the root/password combo.  Have you tried using your root/password in a terminal.  If not, try this:

[FONT="Courier New"]$ su - root
< enter root password >[/FONT]

If that does not work, then perhaps what is needed is to set your root password.  That can be done using this:

[FONT="Courier New"]$ sudo passwd[/FONT]

Btw, to answer my curiosity, can you tell me why you have elected to use the CUPS HTML interface?  Did the **System -> Administration -> Printing** interface not help?  I think when working through that interface, one must enter their "sudo" (normal login password) in lieu of the root password.

---

### Post by sdb2028 on 2007-10-21
root password works in terminal fine as stated in my earlier post

---

