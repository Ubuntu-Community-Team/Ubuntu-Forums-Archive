---
title: "Restart Script"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by lexor on 2006-03-28
How do I make a script that will restart a application, for example iptables.

sudo /etc/init.d/iptables restart

I would like to place icons next to the firefox icon on the top desktop panel for easy access, three in total.

sudo /etc/init.d/iptables stop
sudo /etc/init.d/iptables start
sudo /etc/init.d/iptables restart 

So I have three scripts, each with its own icon.

---

### Post by mdmarmer on 2006-03-28
You just want to know how to write a script?

It's a good idea to search

Try here

[http://www.qnd-guides.org/qnd-bootup.html](http://www.qnd-guides.org/qnd-bootup.html)

Mike

---

### Post by trent dillman on 2006-03-28
Try this on for size...

Create a new file and save the following:

```

#!/bin/bash

option=
case $1 in
        "stop")
                echo "Stopping...";
                option="stop"
                ;;
        "start")
                echo "Starting...";
                option="start"
                ;;
        "restart")
                echo "Restarting...";
                option="restart"
                ;;
        *)
                echo "I don't know that option!";
                exit 1
                ;;
esac
gksu /etc/init.d/iptables $option
exit 0

```

Make the file executable:

```
chmod 755 file
```

Now, make 3 buttons with custom app launcher, with the commands

/path/to/file stop
/path/to/file start
/path/to/file restart

---

### Post by lexor on 2006-03-29
thanks for the info :)

---

