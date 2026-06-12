---
title: "Citrix ICA Client Problems"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by houseisland on 2006-09-22
Hi,

Has anyone had any success getting the Citrix ICA client for Linux working on Dapper?

There are instructions and testimonials of success for Breezy:

[http://bin-false.org/?p=13](http://bin-false.org/?p=13)

But these instructions do not work quite as they should in Dapper.  Everything seems to go OK, but the end result is that the keyboard does not work for the Citrix login screen.  The standard Dapper TS client works, though, with the RDP protocol.  The Citrix server in question is ancient -- NT 4 TSE with Metaframe 1.8. 

Thanks.

[Edit:  I do realize that the Citrix client is unsupported.]

---

### Post by FerGeCo on 2006-10-09
> **houseisland said:**
> Hi,

Has anyone had any success getting the Citrix ICA client for Linux working on Dapper?

There are instructions and testimonials of success for Breezy:

[http://bin-false.org/?p=13](http://bin-false.org/?p=13)

But these instructions do not work quite as they should in Dapper.  Everything seems to go OK, but the end result is that the keyboard does not work for the Citrix login screen.  The standard Dapper TS client works, though, with the RDP protocol.  The Citrix server in question is ancient -- NT 4 TSE with Metaframe 1.8. 

Thanks.

[Edit:  I do realize that the Citrix client is unsupported.]

Just download the tar.gz package.
use :

```
sudo apt-get install libmotif3
```

Extract the tar.gz package and run the sudo ./setupwfc

-- FerGeCo

---

### Post by Mithrilhall on 2007-01-29
I'm having the same issue.

It doesn't look like the keyboard is working but if you type in the username, hit tab, type in the password and hit enter it goes to connect and the ICA Client just closes.


> 
Just download the tar.gz package.
use :

Code:

sudo apt-get install libmotif3

Extract the tar.gz package and run the sudo ./setupwfc

-- FerGeCo


Did that....still doesn't work.


###################################
UPDATE
###################################

I uninstalled the Linux client and installed the Windows client via Wine and it works fine so I'll just stick with that.

---

### Post by houseisland on 2007-04-02
> **Mithrilhall said:**
> 

###################################
UPDATE
###################################

I uninstalled the Linux client and installed the Windows client via Wine and it works fine so I'll just stick with that.

Clever.

I will have to file this info away in the back of my brain should I encounter the problem again.


Another question: Can you get printers on the Linux box to map in the Citrix session?

---

### Post by kygil on 2007-04-04
How do I install "wine" and then how do I get citrix to work through wine.  I've tried every way possible via linux and I get to the point where it asks what you would like to open the application with.  I choose "wfica.sh", the download screen pops up but nothing else happens after that.  Detailed steps on how you got it to work through wine would be much appreciated.

Thanks,
Kyle

---

### Post by kygil on 2007-04-04
I've downloaded wine via the repository, now what steps do I take to get citrix to work?

---

### Post by kygil on 2007-04-09
Which Windows citrix client did you install?

---

### Post by dtmilano on 2007-04-10
If you're having problems running Citrix ICA Client 10.0 for Linux in Ubuntu you can give citrix-icaclient-10-ubuntu script a try. The intention of this script is to solve most common problems found in running the client.
Download the script from [http://codtech.com/downloads/citrix-icaclient-10-ubuntu]("http://codtech.com/downloads/citrix-icaclient-10-ubuntu")
.

You must have Citrix ICA Client 10.0 for Linux installed before running the script.
If Citrix is installed in a system location use sudo to run it, and if the installation directory is not /usr/lib/ICAClient set ICAROOT=/path/to/your/dir in the environment.

```

diego@bruce$ export ICAROOT=/usr/lib/ICAClient
diego@bruce$ sudo bash /tmp/citrix-icaclient-10-ubuntu

```

---

