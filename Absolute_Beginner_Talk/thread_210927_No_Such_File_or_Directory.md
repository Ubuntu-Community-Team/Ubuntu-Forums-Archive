---
title: "No Such File or Directory"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Bull Moose on 2006-07-07
CUPS configuration:

Attempting to set printer sharing from Dapper to W2K using SAMBA.  All the neccesary pieces of SAMBA are installed. 

Dapper connected to W2K with this command: /usr/bin/smbclient -L rice -U fred.

ls -l /usr/lib/cups/backend/smb  [smb backend is installed]

The next command:

sudo /usr/sbin/lpadmin -p RicePrinter -v smb://fred:mypass@rice/HPPSC1400 -P /root/hppsc1400.ppd

Does not work, because it reports lpadmin file or directoy does not exit.  When CD /usr/sbin/ and then ls -l it shows lpadmin in light blue.  I check /usr/sbin/ files and it shows an diamond shaped icon for lpadmin. I right click on the diamond shaped icon and then do properties, it indicates lpadmin is an executable.

I'm stuck. Will somebody please tell me what I'm doing wrong.

Thanking you advance:)****

---

### Post by sitedesign on 2006-08-05
I have got the final release of Dapper installed and lpadmin seems to be where you say and works fine.

You could try 'whereis lpadmin' which should let you know the various locations of the file.

I find the easiest way to share the printers from Linux to windows is by using CUPS.

Try taking a look at /etc/cups/cupsd.conf for details. Also there are some sample configs on this forums, just search for CUPS printer sharing.

---

### Post by OU812 on 2006-08-05
I'm on my kubuntu machine so I don't have colors in bash. I wonder if this will work:

In bash, cd to (at the appropriate time) /usr/sbin. Then do

sudo ./lpadmin -p RicePrinter -v smb://fred:mypass@rice/HPPSC1400 -P /root/hppsc1400.ppd

No guarantees.

john

---

