---
title: "Restore Thunderbird Contacs after restoring from backup"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-09-14
Using this information i have made a backup of my thunderbird info and have fully restored it

[http://www.cyberciti.biz/faq/linux-backup-thunderbird-email-profile/](http://www.cyberciti.biz/faq/linux-backup-thunderbird-email-profile/)


now my next drama is...

Where have all my contacts gone???
they are supposed to be in a file called "abook.mab"
but in side this file is only 3 contacts.... where have the the other 20 gone??

any ideas?

---

### Post by philinux on 2007-09-14
The file should be in your 
/home/yourname/.mozilla-thunderbird/xxxxxxx.default profile

---

### Post by justleen on 2007-09-14
thunbird create a new unique folder for you when you launch it for the first time (just cancel the server setup details)
home/yourname/.mozilla-thunderbird/xxxxxxx.default profile

copy the contents(!) from the old unique folder to the new unique folder. restarting thunderbird, and you should have everything back

---

### Post by stinger30au on 2007-09-14
thanks guys, will try it later today

---

