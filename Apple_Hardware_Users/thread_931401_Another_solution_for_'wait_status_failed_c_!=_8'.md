---
title: "Another solution for 'wait status failed: c != 8'"
date: 2008-09-27
forum: Apple Hardware Users
---

### Post by droll on 2008-09-27
Tested on MBP 3.1 Should be model independent (for Intel).

Prerequisites: keep original applesmc module from ubuntu kernel package; stop logging 'wait status failed: c !=' to system logs.

Solution: replace **syslog** with **syslog-ng** package.

Description:

Execute:
```
sudo apt-get install syslog-ng
```

Then edit **/etc/syslog-ng/sylog-ng.conf** by adding following lines just after last filter definition (in my case it was line 190)

```
filter not_applesmc {
    not match(".*applesmc: wait status.*");
};
```

Then we have to add that filter to syslog, kern_log and message: 

```
log {
        source(s_all);
        filter(**f_syslog**);
	**filter(not_applesmc);**
        destination(df_syslog);
};
```

```
log {
        source(s_all);
        filter(**f_kern**);
	**filter(not_applesmc);**
        destination(df_kern);
};
```

```
log {
        source(s_all);
        filter(**f_messages**);
	filter(**not_applesmc**);
        destination(df_messages);
};
```

And finally execute:
```
sudo /etc/init.d/syslogd restart
```

---

