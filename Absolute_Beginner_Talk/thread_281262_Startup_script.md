---
title: "Startup script?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Stomstedt on 2006-10-20
I'm just wondering.  How do I get a program to start automatically upon logging in or it working when I'm on the login screen?

Thanks

---

### Post by taurus on 2006-10-20
Stuff in /etc/init.d will be started when the system is up!!!

---

### Post by Stomstedt on 2006-10-20
What if I wanted to run proftpd at startup, /usr/local/ircd/bin/ircd, and /usr/local/bin/noip2 ?

---

### Post by taurus on 2006-10-20
Then you link them to /etc/init.d...

```

sudo ln -s /usr/local/ircd/bin/ircd /etc/init.d/ircd
sudo ln -s /usr/local/bin/noip2  /etc/init.d/noips

```

---

### Post by Chaos5lw on 2006-10-21
How would i add it so "sudo dhclient" was run at startup so my wireless network auto-connected?

---

### Post by Chaos5lw on 2006-10-21
*bump*

---

### Post by amrendra on 2006-11-06
for proftpd...

go to System > Administration > Services

give your password when asked and mark the 'FTP Service (proftpd)' thru checkbox.

worked for me.

---

### Post by Kegir on 2006-11-26
How would I go about linking this to startup, 
sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o /home/user/backup/lkl_log.log

also does anything else have to be done if it requires root?

---

### Post by Kegir on 2006-11-26
...bueller...

---

### Post by swigrid on 2006-12-19
and how would i set order of startup scripts? for example. i have created hamachi script but trouble is, it doesn't work, because dhcp script is after hamachi script and hamachi can't resolve ip address, cause of internet connection which is not started yet. in gentoo is file, where i can write any my script and those scripts are done after all init.d scripts.

thanx guys for help

---

### Post by Subw00fer on 2006-12-19
I am also interested in running a sudo script that starts my wireless internet at the startup.

BUMPY

---

### Post by tabilozzo on 2007-01-02
I'm not expert (and this is my first post in this forum) but to execute a script at startup you can add it in the "/etc/rc.local" file.

You shoud have something like this:

./path_to_you_script/yourscript
exit 0

---

