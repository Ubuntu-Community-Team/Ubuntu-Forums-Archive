---
title: "iptables log?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Matthyis on 2007-06-30
I have been looking at ip tables and I cant seem to find the log I went to this sight
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
and used this command  where or what folder is the log in that I can check  or is this not the right command to add the log?

# iptables -I INPUT 5 -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7

---

### Post by yagood on 2007-06-30
You might want to check syslog:

Go to menu System > Administration and then click System Log and select "syslog" in the left column.

---

