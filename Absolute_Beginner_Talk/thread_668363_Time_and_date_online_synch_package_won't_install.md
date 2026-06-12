---
title: "Time and date online synch package won't install"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-15
I have tried installing the online synching package for Date and Time on Ubuntu 7.10 but everytime i try to install nothing happens- when i go into the date and time options and try to change my time setting from Manual to synched online, i get the prompt to install the package necessry for this feature, so when i choose the option to install it, i see the mouse pointer change to a busy icon for a moment then it goes back to the Date and Time screen and nothing happens.  i've tried putting the Ubuntu CD in to see if if needs to get the package off the disc, but that didn't work.  Any suggestions would be appreciated.  Thanks.

---

### Post by Cypher on 2008-01-15
Open a terminal and do
```

sudo apt-get install ntp

```
That will get you the necessary software to keep your PC in sync.

---

### Post by Matt26 on 2008-01-15
thanks for the response- i just finished a major install of updates to the OS last night and tried again to download the package and it worked this time!

---

