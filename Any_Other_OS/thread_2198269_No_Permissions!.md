---
title: "No Permissions!"
date: 2014-01-08
forum: Any Other OS
---

### Post by helen.mcilroy on 2014-01-08
[COLOR=#141414][FONT=Georgia]I just installed Chrubuntu on my new Acer Chromebook. I followed a tutorial on YouTube. It went OK except the user interface did not come up. That was ok because I just want to learn the command line. [/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]However, it asked me for a login and password which it had not asked me to set before. I hunted around and found the defaults are user and user. Fine except that this user has no real permissions. [/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Can anyone tell me how to get admin rights without starting again?[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]Thanks[/FONT][/COLOR]

---

### Post by 3rdalbum on 2014-01-08
On Ubuntu, your user accounts only have basic user permissions. Your first user account can use 'sudo' to access administrator permissions.

Does "sudo" work?

For instance:

```
sudo whoami
```

should ask you for your password and then tell you "root", indicating that you can run commands as administrator by prefacing them with the keyword Sudo.

---

### Post by Bucky Ball on 2014-01-08
*Thread moved to **Other OS/Distro Support**.*

Chrubuntu is not officially supported in the main support areas of the forum. Good luck.

---

