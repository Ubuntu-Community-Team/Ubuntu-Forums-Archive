---
title: "Dapper / W2K Printer Sharing // Cups Configuration"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Bull Moose on 2006-07-07
CUPS configuration:

Attempting to set printer sharing from Dapper to W2K using SAMBA. All the neccesary pieces of SAMBA are installed.

Dapper connected to W2K with this command: /usr/bin/smbclient -L rice -U fred.

ls -l /usr/lib/cups/backend/smb [smb backend is installed]

The next command:

sudo /usr/sbin/lpadmin -p RicePrinter -v smb://fred:mypass@rice/HPPSC1400 -P /root/hppsc1400.ppd

Does not work, because it reports lpadmin file or directoy does not exit. When CD /usr/sbin/ and then ls -l it shows lpadmin in light blue. I check /usr/sbin/ files and it shows an diamond shaped icon for lpadmin. I right click on the diamond shaped icon and then do properties, it indicates lpadmin is an executable.

I'm stuck. Will somebody please tell me what I'm doing wrong.

Thanking you advance:)

---

### Post by richbarna on 2006-07-07
A little piece of advice, just trying to help by the way :)
[http://www.ubuntuforums.org/showthread.php?t=82471](http://www.ubuntuforums.org/showthread.php?t=82471)

Sometimes it's frustrating having to wait, I know. But the problem is if you keep posting new threads and different people answer them, it gets confusing for us when we try to help as we can't see what other advice you have been given.

Another tip, sometimes (if you have waited a long time) it's acceptible to type *bump* on your thread to move it to the top of the queue again.

Sorry I can't help with your question.

Good luck !!

---

