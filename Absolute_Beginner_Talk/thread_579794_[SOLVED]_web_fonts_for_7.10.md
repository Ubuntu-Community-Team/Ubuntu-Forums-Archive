---
title: "[SOLVED] web fonts for 7.10?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-10-18
I just installed 7.10 and notice that the web fonts are all off again throw some pages all out of wack. I tried to do "sudo apt-get install msttcorefonts" to get the fonts like I used to for previous ubuntu versions, but it no longer works saying it's not available.

Is there a way to get the fonts I need for web pages to appear normally?

---

### Post by Technoviking on 2007-10-18
Install ubuntu-restricted-extras
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by -Ghost9- on 2007-10-18
it didn't work.
and i get this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "ubuntu-restricted-extras"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by NilsE on 2007-10-18
Go into software sources and turn all repos on.  Then reload in Synaptic and it should be there.

---

### Post by -Ghost9- on 2007-10-18
had to switch to the USA versus the main servers and it worked. I had already activated all the repos. Thanks for the help!!! I really like this version. It's nice.

---

### Post by khan Singh on 2007-10-19
I am having similar font problems, however I was able to install ubuntu-restricted-extras and msttcorefonts from the very beginning.  But when msttcorefonts  installed I got a message concerning DeFoMa and to install x-ttcidfont-conf to configure the msttcorefonts.  I have tried to uninstall and reinstall msttcorefonts but nothing works.  I have read the  x-ttcidfont-conf documentation and it was of little use.  

Thanks

Khan

---

