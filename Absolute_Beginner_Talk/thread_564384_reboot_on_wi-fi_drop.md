---
title: "reboot on wi-fi drop?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by sblanzio on 2007-10-01
Hi!
I have an old laptop that I'm using in command line mode only, with ssh installed, connected via wi-fi.

Unluckily, because of the disance from the access point, sometimes this laptop loses the internet connection (it loses the AP association) and doesn't seem to rejoin by itself. This happens maybe about once or twice a day. Sometimes never.

However everytime this happens I have to manually reboot that (a network restart shell command won't fix it), but I HAVE to be physically there.

I'm looking for a script that could check at certain time intervals if the wi-fi connection is ok (maybe pinging the AP?) and if it gets no response it will reboot the system.

I'm trying to find out what is the best way to do that... expecially I don't know how to launch that periodically..

anybody could help me?
thanksss!!!!
bye
lanz

---

### Post by jfinkels on 2007-10-02
You shouldn't have to restart the system to reconnect to the access point. You should try:```
sudo iwconfig eth0 essid *networkname* && sudo ifdown eth0 && sudo ifup eth0
``` where *networkname* is the ESSID (the 'name') of the network to which you connect.

However, it is possible to have a script that runs periodically, and it is possible to have a script that pings an address, and it is possible to have a script that restarts the computer! So here it goes:

A script might look something like this:
```

#!/bin/bash
#
# this script reboots the computer if ping of $ADDR fails twice.
#
# NB: this script must be run as root in order to use the shutdown
#  command to shutdown the computer.
#


# address to ping
ADDR="192.168.1.1"
# number of times to ping before giving up
COUNT="10"

# number of packets received after pinging the address
PCKTSRCVD=`ping -c $COUNT $ADDR | grep -o -e "[0-9]* received" | cut -d " " -f 1`

echo "Received $PCKTSRCVD packets."

if [ $PCKTSRCVD -gt "0" ]
then
    echo "You are still connected :D"
else
    echo "You are no longer connected."
    echo "I will try one more time before restarting..."
fi

#
# try one more time
#

PCKTSRCVD=`ping -c $COUNT $ADDR | grep -o -e "[0-9]* received" | cut -d " " -f 1`

echo "Received $PCKTSRCVD packets."

if [ $PCKTSRCVD -gt 0 ]
then
    echo "You are still connected :D"
else
    echo "Rebooting now..."
    # reboot the computer
    shutdown -r now
fi

exit 0

```

You might want to test this out a bit before using it.

Anyway, as it says, you can only use the program 'shutdown' as root, so the script must be run as root.

Now to run a script on a schedule, we use a program called "cron" which is a daemon that runs programs, appropriately, on a schedule that we define. See here for a general how-to: [http://www.howtoforge.com/forums/showthread.php?t=7922](http://www.howtoforge.com/forums/showthread.php?t=7922)

In brief, though, if you want it to run at 6am and 6pm every day, you might do something like this.

First log in as root (because our script needs to be run as root):```
su

```
and enter the root password.

Then, save the script at some awesome location, like "/usr/bin/myawesomescript.sh".

Then, type:```
crontab -e
```You will be in the "nano" text editor.

After the commented lines (lines starting with the hash symbol, "#"), type the following:```
00 06,18 * * * /usr/bin/myawesomescript.sh
```

This means, run /usr/bin/myawesomescript.sh at 0600 and 1800, every day of the month, every month of the year, and every day of the week.

Save it by pressing <Ctrl>-<O> and exit by pressing <Ctrl>-<X>.

Now crontab automatically adds the crontab that you just saved to its list of stuff to do automatically, and it will be done. Let me know if you have any other questions.

---

### Post by sblanzio on 2007-10-02
I couldn't be more grateful! :)
This is exactly what I looked for! (and a good chance to learn some good scripting!)

Now I'll be testing this and then I'll let you know.

Thank you very much!! :)

sblanzio

---

### Post by jfinkels on 2007-10-02
No problem! :D

---

