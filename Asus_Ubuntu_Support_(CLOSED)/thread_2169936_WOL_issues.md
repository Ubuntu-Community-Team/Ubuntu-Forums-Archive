---
title: "WOL issues"
date: 2013-08-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by steven_richards on 2013-08-24
I have an Asus motherboard in my PC, I have enabled WOL so I can start it with Magic Packet, however when I shut down the system it instantly restarts itself, this happens even when the network cable isn't plugged in. However if I just suspend the system WOL works flawlessly. I'm sure this is something to do with Ubuntu settings rather than my motherboard because I have a second drive in the machine running windows 7 and if I open up windows and shut it down it stays shutdown.


Any ideas?

Thanks Steve

---

### Post by Crusty Old Fart on 2013-08-24
WOL is a little weird to get working.
I have a "local" machine running Ubuntu 10.04 that I connect with my "remote" machine, which is running Ubuntu 8.04 server version.
I'll skip the procedure I use to wake up and log in to the remote machine since your difficulty involves shutting down the remote machine.
So, what follows assumes that my remote machine is already up and running.

Three files are involved to shutdown my remote machine in order for it to power off and be left in a state from which it can be woken later with a magic packet.
I run the the first file, which exists on my local machine, it then causes a second file to run on my remote machine, which makes a call to a third file that exists on the remote machine.

In detail, the process goes as follows:
I run a script on my local machine named: [COLOR=#ff0000]**remote_off.sh**[/COLOR]
It tells the remote machine to run a script, which exists on the remote machine, named: [COLOR=#0000ff]**powerdown.sh**[/COLOR]
[COLOR=#ff0000]**remote_off.sh**[/COLOR] contains the following code:
```

#!/bin/bash
ssh remote_machine_name /path/to/file/[COLOR=#0000ff]**powerdown.sh**[/COLOR]
exit 0

```
The script named [COLOR=#0000ff]**powerdown.sh**[/COLOR] on the remote machine runs another script, which exists on the remote machine, named: [COLOR=#008000]**wolready.sh**[/COLOR]
[COLOR=#0000ff]**powerdown.sh**[/COLOR] contains the following code:
```

#!/bin/bash

/path/to/file/[COLOR=#008000]**wolready.sh**[/COLOR]
sudo shutdown -P now
echo -e " Attempting LAN access to the remote machine...\n"
checkcount=1
echo " Attempt number:" $checkcount

while (( $(ping -c 1 012.345.678.9 | grep -c "100% packet loss") != 0 )); do
  (( ++checkcount ))
  echo " Attempt number:" $checkcount
done

sleep 2s

exit 0

```
[COLOR=#008000]**wolready.sh**[/COLOR] contains the following code:
```

#!/bin/bash

# Enable ethernet reception of magic packet transmission
# if it is not already enabled.

sudo ethtool eth0 | grep "Wake-on: g" > /dev/null || \
sudo ethtool -s eth0 wol g

while (( $(sudo ethtool eth0 | grep -c "Wake-on: g") < 1 )); do
  sleep 1s
  echo Waiting for Wake On Lan activation.
done 

echo The remote machine is awake.
sleep 3s

exit 0

```

I have been using this code for several years. I use my remote machine as a backup server. The script on my local machine named: [COLOR=#ff0000]**remote_off.sh**[/COLOR] is called as the last command by a custom backup script, which runs as a cronjob, once a week while I'm sleeping.

If you need more detail about how any of this works, I'll be happy to explain any part of it in greater depth.

Hope it helps,

Crusty

---

