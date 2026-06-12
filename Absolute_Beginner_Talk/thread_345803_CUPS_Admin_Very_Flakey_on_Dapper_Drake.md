---
title: "CUPS Admin Very Flakey on Dapper Drake"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Busta999 on 2007-01-24
I would really appreciate any inpu/thelp here please.

I am trying to enable the working printer attached to the Ubuntu box to be shared for other LAN users.

I have added my user mikeh to lpadmin group, and added cupsys to the shadow group, 

CUPS admin won't accept my username/password.

I have added other users to the lpadmin group and they don't work either.

I have created a new group - system, added mikeh to it, changed the cupsd.conf file  'SystemGroup system' and that still doesn't work.

While I realise that Linux is more secure than Windows, please assure me it is this way because no one can configure it :-) 

Heeeeeeeeeelp

---

### Post by scrooge_74 on 2007-01-25
You have not configure CUPS properly so he can let others browse your printer.

Post your conf files so people can tell you what is wrong

It took me a while to learn how to configure my system so it can add printers from inside Ubuntu or from the webrowser

[http://www.ubuntuforums.org/showthread.php?t=231630&highlight=cups](http://www.ubuntuforums.org/showthread.php?t=231630&highlight=cups)
[http://www.ubuntuforums.org/showthread.php?t=297423&highlight=parallel+port](http://www.ubuntuforums.org/showthread.php?t=297423&highlight=parallel+port)

---

