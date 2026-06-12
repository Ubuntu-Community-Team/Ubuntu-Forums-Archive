---
title: "best way to launch daemons at startup?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by frank_costanza on 2007-05-15
Is there a preferred way to configure daemons to launch at startup?

I'm trying to launch svnserve (Subversion) at startup running as the user 'svn'. There are various lauch facilities that I've read about including inetd and xinetd among others. Is there a commonly used or recommended facility that I should be using in Ubuntu?

Thanks!

---

### Post by vikram on 2007-05-17
not sure if this is the preferred way but this is how i got my firewall to start up on booting. replace firewall for the daemon you want. is you need to find the the location of the file use the whereis command.

```

# **sudo cp ~/Desktop/firewall /etc/init.d/firewall**
# **sudo chmod 755 /etc/init.d/firewall**
# **sudo ln -sf ../init.d/firewall /etc/rcS.d/S42firewall**
# **sudo /etc/rcS.d/S42firewall restart**
```btw the relevant parts to the firewall code is :
```

#!/bin/sh

if [ -r /lib/lsb/init-functions ]; then
    . /lib/lsb/init-functions
fi

firewall_start()
{
  ##code to start service goes here
}

firewall_stop()
{
  ##code to stop service goes here 
}

case "$1" in
    start)
        log_begin_msg "Starting firewall..."
        firewall_start
        log_end_msg 0
        ;;

    stop)
        log_begin_msg "Stopping firewall..."
        firewall_stop
        log_end_msg 0
        ;;

    restart)
        log_begin_msg "Restarting firewall..."
        firewall_stop
        firewall_start
        log_end_msg 0
        ;;

    *)
        echo "Usage: $0 {start|stop|restart}"
        exit 1

esac
```
this works for me flawlessly. got the info from [http://users.piuha.net/martti/comp/ubuntu/firewall](http://users.piuha.net/martti/comp/ubuntu/firewall)

---

### Post by FuturePast on 2007-05-17
Yes, the scripts in /etc/init.d and links in /etc/rc*.d are the preferred way of starting a daemon.

---

