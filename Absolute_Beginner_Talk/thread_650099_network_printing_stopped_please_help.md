---
title: "network printing stopped please help"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by stevieb on 2007-12-25
hello,

my laptop has recently lost the ability to find network printers.  i cannot add/install printers from the System-Administration-Printing window (nothing is detected), and visiting localhost:631 in a browser returns error 404.

i can vnc on to the print server and print a test page, so i know the printer is working.  for some reason, my laptop won't detect any network printers.

i have uninstalled and reinstalled cupsys (i'm running feisty BTW), and disabled IPv6.  the output of "lpstat -p" is: lpstat: No destinations added.

something happened during the last kernel update; i don't know.  i've also tried booting into a 2-6-20-15 kernel to no avail.   

any help or suggestions is appreciated.  let me know what output i can post.

thanks,

steve

---

### Post by spiderbatdad on 2007-12-25
check for smb-client and smbfs

---

### Post by stevieb on 2007-12-25
thanks for the reply- if you mean smbclient, it's installed.  smbfs is not.  i didn't mention this, but the printer server is a dapper box.  sorry for the omission- do i even need to be looking at samba settings here?

-steve

---

### Post by spiderbatdad on 2007-12-25
sorry i assumed you were trying to print to a windows printer. I guess I would go to synaptic and choose completely remove on the cups packages so the .conf files are removed, then reinstall them. Good luck. I had the same problem a couple of days ago, and that is what I did to reconnect to localhost:631

---

### Post by stevieb on 2007-12-26
my friend, you rock! totally fixed it!

thanks

---

