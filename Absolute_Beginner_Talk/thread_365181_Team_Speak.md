---
title: "Team Speak"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by mrwasabi on 2007-02-19
Hello,
I recently added teamspeak-server to my ubuntu test server and need to force it to start when I reboot the server. It came with a script to start and stop ts but I have no idea how to add it to my rc.local. The script for ts is "teamspeak2-server_startscript" (start or stop). Thanks in advance for any help you can provide.


MrWasabi

---

### Post by frodon on 2007-02-19
To execute a script on boot, just put it under /etc/init.d then tun this command :
```
sudo update-rc.d *name_of_script* defaults
```

---

### Post by mrwasabi on 2007-02-19
TY Frodon :-)

---

