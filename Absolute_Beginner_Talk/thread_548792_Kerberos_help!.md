---
title: "Kerberos help!"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by cAllison on 2007-09-11
Hi, I have a file server in my office that is on 6.10 and using krb5/samba to serve up files on my AD domain.

Everything has been gravy for a month, then something happen to server, after i fixed it and booted it back up I'm getting a wierd error in the AD event log. saying:

" The account $ did not have a suitable key for generating a kerberos ticket. ... "

Then it says something about setting/resetting a password to fix it.

HOW DO I RESET THE PASSWORD!?:confused::confused:

---

### Post by Pinger05 on 2007-09-12
It should not need a Kerberos ticket in order to serve files to the domain.  Ok lets try this:

1)Do you log on to the Draper server to perform work tasks?
2)What was broken on your server that you fixed?  What did you do to fix it?

In order to serve files to a Windows domain you have to be 'identified' in AD.  The Domain Controller will issue a Ticket Granting Ticket (TGT) to the user workstation when you log on.  Then when you access services the DC will add tickets to your TGT allowing you to have a single logon.  There should not be an account on the server named $ that needs a TGT but then again who says that M$ did things exactly by the book.

What I am thinking is that whatever you did to fix the server broke it's AD link...  You can try removing it from the AD domain (not sure how to do this), then remove the server from Active Directory Users and Computers then re add it back in Active Directory Users and Computers.

Hopefully it is that simple.

---

### Post by cAllison on 2007-09-12
CMOS battery, server freaked out. So I replaced the battery, brought the server back up, and I can do:
wbinfo -u
and wbinfo -g and get the right results

but..

getent passwd
and getent group will only return local accounts, and it used to return all the domain accounts.

the $ in the OP is supposed to be <machine name>$

edit:
I've tried deleted the machine from AD and rejoining the domain - didnt work
tried renaming the machine and rejoining domain - didnt work
Windows clients can see the file server, but when connecting to it, the file server will not accept any user/pass
tried all sorts of different things in the conf files - but to no avail.

---

### Post by cAllison on 2007-09-12
welp..

---

