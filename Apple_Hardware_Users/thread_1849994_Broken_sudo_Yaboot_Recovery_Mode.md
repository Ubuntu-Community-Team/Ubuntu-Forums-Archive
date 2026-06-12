---
title: "Broken sudo: Yaboot Recovery Mode"
date: 2011-09-25
forum: Apple Hardware Users
---

### Post by sgy on 2011-09-25
I am running Dapper Drake server edition on an old iBook. I broke sudo by changing my hostname in file etc/hostname but not anywhere else. Now I'm trying to regain root privileges by booting into recovery mode but I haven't been able to figure out how to boot into recovery mode with yaboot. 

I have tried all of the following during reboot without success:
Shift 
Control+Alt+F1
Command+option+p+r 

Any help or suggestions would be much appreciated.

Thanks, 
Sam

PS I have a complicating issue that this iBook has an Italian keyboard.

---

### Post by rsavage on 2011-09-25
[http://ubuntuforums.org/showpost.php?p=11283476&postcount=2](http://ubuntuforums.org/showpost.php?p=11283476&postcount=2)

Btw, isn't dapper no longer supported?  You might want to think about an update....

---

### Post by sgy on 2011-09-25
'Linux single' worked perfectly.  I was able to edit the /etc/hostname file back to the original hostname, and sudo is working once again. 

Thank you very much.

---

