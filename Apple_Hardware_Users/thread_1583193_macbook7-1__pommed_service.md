---
title: "macbook7-1  pommed service"
date: 2010-09-27
forum: Apple Hardware Users
---

### Post by watgrad on 2010-09-27
Hello great ubuntu gurus - I'm a humble noob with a question for you all.

I followed the directions in the MacBook7-1 setup thread for lucid to install pommed: [https://help.ubuntu.com/community/MacBookPro7-1/Lucid](https://help.ubuntu.com/community/MacBookPro7-1/Lucid)

This works well, I can control brightness, volume and keyboard backlights using the function keys.

However, pommed doesn't start automatically on login.  I have to maually start the service.  

Is their a way to have this service start automatically on login?

---

### Post by ajgreeny on 2010-09-27
How do you manually start the service after boot?  If it is a simple command "pommed" you can add it to System ->Preferences ->Startup Applications.  If you need to have it start before gnome has appeared, or it needs sudo to start, you may have to turn the command into an entry in /etc/rc.local.

Tell me how you start it now, and I'll try to help.

---

### Post by watgrad on 2010-09-27
OK-the command is:

sudo service pommed start

---

### Post by ajgreeny on 2010-09-27
OK, you need to edit /etc/rc.local and add the line **service pommed start** above the **exit 0** line.

Note that the sudo is not needed.

You should also be able to start it with a shell script added to /etc/init.d in a similar way
```
#!/bin/bash
service pommed start
```
Copy that to a txt file in gedit, save it as pommed.sh, make it executable and copy it to /etc/init.d.  As far as I can see, either way should work.

---

