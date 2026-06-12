---
title: "Installing WINE"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by marcks on 2008-04-05
Hi

I am trying to install WINE.  I am using the Terminal and add the following and then end up with the following error:

sudo apt-get install wine

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

So I tried:  sudo apt-get update wine  (no good)  and sudo apt-get update  (also no good)


can someone help please
Karen

---

### Post by LaRoza on 2008-04-05
Go to Applications->Add/Remove

Change it to "All available Applications", in the drop down box in the top of the Window, reload it, and install Wine (type "Wine" in the search box)

---

### Post by marcks on 2008-04-05
I went to add/remove and did as you advised.  It appeared in the list so I ticked the box.  All  went well until I got the following error:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/b/binfmt-support/binfmt-support_1.2.10_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/b/binfmt-support/binfmt-support_1.2.10_all.deb)
  407 Proxy Authentication Required

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.46-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.46-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


Does this mean I need to add the Repository and if so what exactly do I need to type in?

---

### Post by marcks on 2008-04-05
> **LaRoza said:**
> Go to Applications->Add/Remove

Change it to "All available Applications", in the drop down box in the top of the Window, reload it, and install Wine (type "Wine" in the search box)

Did what you said and got the error that I put in the Reply.

Thought it might mean that I needed to add the Repository so I went the the WineHQ website and used their directions:

karen@karen-laptop:~$ wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
[sudo] password for karen:
gpg: no valid OpenPGP data found.

Then add:

karen@karen-laptop:~$ sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.lis
--17:31:08--  [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/winehq.lis'
Resolving acs.vicone.netspace.net.au... 210.15.254.246
Connecting to acs.vicone.netspace.net.au|210.15.254.246|:8080... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required
17:31:08 ERROR 407: Proxy Authentication Required.

the proxy error is for the wired connection that I use at work (only set it up today) at home I use a wireless connection.

How do I tell it to use the wireless connection?

---

### Post by LaRoza on 2008-04-05
> **marcks said:**
> 
the proxy error is for the wired connection that I use at work (only set it up today) at home I use a wireless connection.

How do I tell it to use the wireless connection?

Disconnect the wire? That would be the simplest way. I am not very experienced with network configurations.

---

### Post by marcks on 2008-04-05
> **LaRoza said:**
> Disconnect the wire? That would be the simplest way. I am not very experienced with network configurations.

Thank You

Changed the Network Proxy setting to: connect directly

Went back into Add/Remove, ticked wine and it is now installed

thanks again
Karen

Went

---

