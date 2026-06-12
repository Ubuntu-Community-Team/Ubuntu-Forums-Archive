---
title: "[SOLVED] Gutsy - Printer configuration requires password"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-24
I am having trouble printing in Gutsy - a fresh install.

The Printer configuration  is asking me for a password:

Password required
Password for carl on local host?
Password:
  Cancel    OK


My login password does not seem to work.

Carl

---

### Post by schuelaw on 2007-10-24
All I can say is same here.

In this case, it's an ipp printer on my local network.  The printer configuration tool successfully scanned for it, but alas will not finalize the configuration without a password.  I typed in the password (the only password on the whole machine) and it won't authenticate.

A

---

### Post by schuelaw on 2007-10-24
More...  So during the install, I created an account called "test".  Afterwards, I created an account called "schuelaw" since that's my regular userid and the home directory already existed.  I granted "schuelaw" administrative priviledges.  Synaptic runs fine from that userid (after authenticating).  As mentioned previously, the printer configuration tool requires a password and won't accept the password on the "schuelaw" account (same as on the "test" account). 

I switched over to the original account ("test") and ran the printer configuration tool there and it worked fine (authenticated on "test"'s password).

That's it for now...

A

---

### Post by cwmoser on 2007-10-25
Thats similar to what I found -- one account will not accept a password but the other will accept a password.

I did copy a lot of files from my home directory in my prior Feisty Fawn version.  I wonder if there is a permissions issue with some hidden file in the home directory?

Carl

---

### Post by rivalarrival on 2007-10-26
Had the same problem: went to add printer, it asked for user password but would not accept it. Running gutsy from a machine initially loaded with edgy, upgraded to feisty, then Gutsy.  Am I a glutton for punishment or what? :)

I had previously assigned a password to my root account,(sudo passwd) so I was able to use the following workaround:

On the printer configuration page (System>Administration>Printers) there is a button marked "Goto Server" - I simply changed the username to root, and tried again, using the root password.

A bit of a bug...  Still, this tool is a dozen times faster than the old one, and seems to work much better, at least in my situation. The old one took more than a minute to scan for network printers, and it could never find one of the printers we use.

---

### Post by philinux on 2007-10-26
Sounds like a bug for launchpad!

---

### Post by cwmoser on 2007-10-26
No printer admin rights for added users:

Users must be in the printing administration group, "lpadmin", to be able to configure printer settings. The first system user created during installation is added to this group, but users added or modified with the user-admin tool at System -> Administration -> Users and Groups will not be added to this group. As a workaround, you can grant "lpadmin" privileges to users by running the command sudo adduser <user> lpadmin in a terminal window.

Bug #152107 

[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)


Carl

---

### Post by mikesmith36 on 2007-11-11
Excellent - another problem solved by the forums - thanks :KS

---

