---
title: "running multiple commands as superuser at start-up"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by mr love and justice on 2006-11-13
I'd like to fire up my VPN client everytime the computer boots, but it requires multiple commands to be run from the terminal in sequence, and they must be run as the superuser. Is there a way to set this up so it all happens automatically? 

mlaj

---

### Post by yabbadabbadont on 2006-11-13
Add them to /etc/rc.local

---

### Post by mr love and justice on 2006-11-15
Still having a bit of trouble with this.. I added the two commands to rc.local and rebooted the computer but nothing happens. My rc.local now looks like the following:

```

#!/bin/sh -e
#
# rc.local
#

/etc/init.d/vpnclient_init start
vpnclient connect VPNProfile

exit 0

```

The end result of running these commands should be an open terminal window awaiting my VPN password input, but nothing happens at start-up.

Another question: should I type sudo in front of the commands if I want them to be run as the superuser or is that assumed for commands run from rc.local?

Thanks in advance for any help.

---

### Post by izmaelis on 2006-11-15
> **mr love and justice said:**
> Still having a bit of trouble with this.. I added the two commands to rc.local and rebooted the computer but nothing happens. My rc.local now looks like the following:

```

#!/bin/sh -e
#
# rc.local
#

/etc/init.d/vpnclient_init start
vpnclient connect VPNProfile

exit 0

```

The end result of running these commands should be an open terminal window awaiting my VPN password input, but nothing happens at start-up.

Another question: should I type sudo in front of the commands if I want them to be run as the superuser or is that assumed for commands run from rc.local?

Thanks in advance for any help.

You should describe full path for *vpnclient* in your rc.local config file if I remember correctly. It should be something like /etc/init.d/vpnclient connect VPNProfile

---

### Post by petit.padavoine on 2006-11-15
> **mr love and justice said:**
> 

Another question: should I type sudo in front of the commands if I want them to be run as the superuser or is that assumed for commands run from rc.local?


I think so.
You should also edit your "sudoers" file:
```
sudo visudo
```

---

### Post by mr love and justice on 2006-11-15
Well, I made the corrections suggested. I added my local username to sudoers.tmp and it now looks like:

```

# User privilege specification
root    ALL=(ALL) ALL
usrname ALL=(ALL) ALL

```

I also editted rc.local, which currently reads:

```

sudo /etc/init.d/vpnclient_init start
sudo /usr/local/bin/vpnclient connect VPNProfile

```

I know that the first command line is being run successfully, but the vpnclient is still not coming up. I think I'll just add it to my sessions start-up list, and things should work fine. Before I end this post, though, I'm just curious about what the changes I made are supposed to do. By adding my username to sudoers, should all of my sudo commands now be run without prompting me for my password (I'm still getting the password prompt)? And what's the purpose of rc.local when I can just add start-up commands to 'sessions?'

---

### Post by That_Geek on 2006-11-15
dont make username ALL have acsess to everything, you are just asking to mess the computer up when you arent paying attention

---

### Post by Redache on 2006-11-15
BAD IDEA!. Don't give your self admin access so you can set your VNC client to start up automatically to log in.....

Just prefix one of the commands with Sudo.

---

