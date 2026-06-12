---
title: "Uninstalling a daemon created in init.d"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by sri1025 on 2006-07-31
Hi, I have a program which I wanted to start as a daemon, so I dropped my script at /etc/init.d/ by modifying the 'skeleton' script.

And then, I went to the command line and installed the daemon using the update-rc.d command.

```

$ update-rc.d my_program defaults

```

Now, I want to uninstall the daemon so that it won't start when I reboot the next time. What command should I use?

Thank you!

---

### Post by sri1025 on 2006-07-31
Never mind,

Figured out, it's this command that will do the trick

```

$ update-rc.d -f my_program remove

```

---

