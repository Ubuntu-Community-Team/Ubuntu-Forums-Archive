---
title: "NetworkManager/Iptables script not working"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by p252 on 2007-11-18
Ok, I've followed the instructions for setting up iptables with NetworkManager in this community doc [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo). The NetworkMangaer script provided on the page works well until my system is rebooted. For some reason after a reboot my /etc/iptables.rules file is empty. I know nothing about scripting or programming. Is there anyone who can let me know if the problem is the script or just something I'm doing wrong? Here is the script:

> #!/bin/bash

if [ -x /usr/bin/logger ]; then
        LOGGER="/usr/bin/logger -s -p daemon.info -t FirewallHandler"
else
        LOGGER=echo
fi

case "$2" in
        pre-up)
                if [ ! -r /etc/iptables.rules ]; then
                        ${LOGGER} "No iptables rules exist to restore."
                        return
                fi
                if [ ! -x /sbin/iptables-restore ]; then
                        ${LOGGER} "No program exists to restore iptables rules."
                        return
                fi
                ${LOGGER} "Restoring iptables rules"
                /sbin/iptables-restore -c < /etc/iptables.rules
                ;;
        post-down)
                if [ ! -x /sbin/iptables-save ]; then
                        ${LOGGER} "No program exists to save iptables rules."
                        return
                fi
                ${LOGGER} "Saving iptables rules."
                /sbin/iptables-save -c > /etc/iptables.rules
                ;;
        *)
                ;;
esac


Thank you for your help!

---

### Post by p252 on 2007-11-26
OK, I'm forgetting the script. How do I just make it so iptables is restored on each boot, preferably before any network interfaces come up. I know you can put things in the rc.* something or other but I don't know what I would put there or in which one. Just need to restore iptables from /etc/iptables.rules on each boot and maybe save the rules when I shut the computer down. 

Thank you,
p252

---

