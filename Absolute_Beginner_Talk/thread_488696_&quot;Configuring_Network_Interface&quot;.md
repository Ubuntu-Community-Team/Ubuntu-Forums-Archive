---
title: "&quot;Configuring Network Interface&quot;"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Xs1t0ry on 2007-06-30
At startup, the loading bar on Xubuntu 7.04 goes very slow and when it is a bit less than halfway the screen changes to a console looking format where it lists the processes that have already been completed (indicated by the [OK] next to them) and then process currently being run. In my case, when it gets to the 'Configuring Network Interface' process, it just sits there. The [OK] never appears and I inevitably have to restart my PC. I am using a dual boot with Windows, which is how I'm able to talk to you good people right now, and I need to know how I can fix this so I can actually get into my desktop!

Note: This problem started happening after an install of ndiswrapper failed.

---

### Post by mummra1 on 2007-06-30
hey!  I have the exact same problem.  It was dual-booting fine until the other day.  Now it lists all the processes and takes forever.  I still haven't figured it out yet, but can you please let me know if you find anything?  Thanks!

---

### Post by testube_babies on 2007-06-30
[http://ubuntuforums.org/showthread.php?t=485868](http://ubuntuforums.org/showthread.php?t=485868)

...You may need to install the ext2ifs driver in Windows to be able to edit some files on your linux drive.

---

### Post by Xs1t0ry on 2007-06-30
The thing is that I can never get to my desktop at all. Do you think if I wait long enough the 'configuring network interface' will succeed? I've waited 10 mins. and nothing happened so I figured nothing would happen. What else can I do?

---

### Post by testube_babies on 2007-06-30
Sorry...I definitely should have been more clear.  My fault.

Try hitting CTRL+C when it freezes on "Configuring Network Interface."  If that doesn't do anything, then boot into Windows and try the following:

Download either [explore2fs]("http://www.chrysocome.net/explore2fs") or [ext2ifs]("http://www.fs-driver.org/") for Windows.  With these tools, you can grab the /etc/network/interfaces file from your Linux disk and open it in notepad/wordpad.  Then follow my directions [here]("http://ubuntuforums.org/showthread.php?p=2926155#post2926155") and copy the file back to your Linux disk (if necessary).

Note:  if this doesn't solve your problem, undo all of the steps above.  I have a feeling your problem is more complicated than this...

---

