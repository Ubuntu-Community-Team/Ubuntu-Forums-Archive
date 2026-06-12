---
title: "&quot;sudo trackpad notap&quot; on wake-up"
date: 2010-06-21
forum: Apple Hardware Users
---

### Post by zeroti on 2010-06-21
whenever I wake my computer from sleep, it forgets the "notap" setting for the trackpad until reboot. I can fix this using the command "sudo trackpad notap".

Is there a way to have this done automatically on wake-up?

---

### Post by linuxopjemac on 2010-06-21
Note: I am not entirely sure whether it will work on PPC.

You could try to make a hook in /etc/pm/power.d as root. You could call this hook 20_notap:

```
sudo nano /etc/pm/power.d/20_notap
```

and put the following lines:

```
#!/bin/sh
trackpad notap
```

CTRL-X and "y" to save.

Make the script executable:

```
sudo chmod +x /etc/pm/power.d/20_notap
```

At a next sleep/suspend, it should then issue your command. But as I said, I am not entirely sure whether on PPC this is also working like on Intel. I use this trick to load a kernel module after sleep on my Intel MacBook 2,1.

---

### Post by zeroti on 2010-06-21
thanks linuxopjemac, that worked! :p

---

### Post by linuxopjemac on 2010-06-21
Great!

---

### Post by zeroti on 2010-07-02
ok, I made a small change to the above file and I think this might be a better solution:

```

#!/bin/sh
pbbcmd reinit

```

This way, if there are other users on the system or I decide to change my preferences, I don't have the "notap" option being set every time on wake-up.

---

