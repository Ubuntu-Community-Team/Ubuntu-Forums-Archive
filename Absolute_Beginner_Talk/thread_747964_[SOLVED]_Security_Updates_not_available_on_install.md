---
title: "[SOLVED] Security Updates not available on installation"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by marcks on 2008-04-07
Hi

I had to reinstall Gutsy and during the installation there was a message to say Security Updates were not available and were commented out of a file.  Didn't write it down so not sure which file.

I had enable the Internet connection before installation.

What do I need to do now?


Karen

---

### Post by wormser on 2008-04-07
I think you need to enable the repositories.  System> Administration> Software Sources and check main, universe, multiverse and uncheck Cdrom.  Then go to System> Administration> Update Manager.

---

### Post by hyper_ch on 2008-04-07
Just uncomment it by editing your /etc/apt/sources.list

---

### Post by marcks on 2008-04-07
> **wormser said:**
> I think you need to enable the repositories.  System> Administration> Software Sources and check main, universe, multiverse and uncheck Cdrom.  Then go to System> Administration> Update Manager.

Worked well.  I also checked the Import security updates on the Updates tab, just for good measure because after the 1st lot of changes there were no updates. 

thank you very much
Karen

---

