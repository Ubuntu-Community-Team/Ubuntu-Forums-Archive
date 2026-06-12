---
title: "Remotely Shut Down VM PC Windows XP2?"
date: 2012-07-10
forum: Any Other OS
---

### Post by ijspegeltje on 2012-07-10
Hello guys,

I'm trying to get the shutdown command to work to connect to a local Windows XP2 machine with a known username and password.  I cannot ping this machine either so I'm not sure this is going to work, but I cannot physically approach it as it's a VM machine.

I am tunneled in to the same network as the Windows XP computer, and I have the IP address as well as my password and log in for the XP computer.  The problem I run into is that my shutdown command here doesn't have the helpful suggestions that the internet keeps giving me such as;

"shutdown -i //ipaddress"

and

"shutdown -m //ipaddress"

Any tips on where I can look for help?

---

### Post by CharlesA on 2012-07-10
```
shutdown -m \\computernameoripaddress -s -t 0
```

[http://www.mydigitallife.info/restart-or-shutdown-windows-xp-2000-and-vista-from-command-line-or-one-click-shortcut/](http://www.mydigitallife.info/restart-or-shutdown-windows-xp-2000-and-vista-from-command-line-or-one-click-shortcut/)

Also, moved to Other OS.

---

### Post by ijspegeltje on 2012-07-10
> **CharlesA said:**
> ```
shutdown -m \\computernameoripaddress -s -t 0
```

[http://www.mydigitallife.info/restart-or-shutdown-windows-xp-2000-and-vista-from-command-line-or-one-click-shortcut/](http://www.mydigitallife.info/restart-or-shutdown-windows-xp-2000-and-vista-from-command-line-or-one-click-shortcut/)

Also, moved to Other OS.

Hey Charles, thanks!  But that doesn't work.

I'm inside Ubuntu when I try to use the commandline to shut it down.  My shutdown does not come with "-m".  Sorry if that was unclear.

This is my shutdown;
shutdown --help
Usage: shutdown [OPTION]... TIME [MESSAGE]
Bring the system down.

Options:
  -r                          reboot after shutdown
  -h                          halt or power off after shutdown
  -H                          halt after shutdown (implies -h)
  -P                          power off after shutdown (implies -h)
  -c                          cancel a running shutdown
  -k                          only send warnings, don't shutdown
  -q, --quiet                 reduce output to errors only
  -v, --verbose               increase output to include informational messages
      --help                  display this help and exit
      --version               output version information and exit

Can I expand on my shutdown command somehow, or is there another way for me to force the VM-WinXP2 SP2 I'm trying to reboot?

---

### Post by CharlesA on 2012-07-10
As far as I know you can only shutdown a Windows machine remotely from a Windows machine unless you use an RPC call.

See here:
[http://lifehacker.com/5275652/shut-down-your-windows-pc-remotely-from-linux](http://lifehacker.com/5275652/shut-down-your-windows-pc-remotely-from-linux)

---

### Post by ijspegeltje on 2012-07-12
Hmm.

Okay, thanks for the information and the links.  I'll fiddle with it some more and see how far this takes me.  I appreciate you taking the time. :)

---

