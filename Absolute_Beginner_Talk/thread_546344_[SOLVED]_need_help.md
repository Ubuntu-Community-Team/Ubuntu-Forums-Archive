---
title: "[SOLVED] need help"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by comradexiactura on 2007-09-08
Thanks to everyone in advance for the help. I have just installed Ubuntu and everything is working great. I couldn't be happier with the installation process and everything it took to get it running. The question i have is, how do i move files into certain directories without having to log into root? I have been told that it isn't a good idea to log into root. Any help or direction would be very appreciated, once again thank you in advance.

---

### Post by Jimmyfj on 2007-09-08
You could do that by opening a terminal and enter:

```
gksu nautilus
```

This gives you the root privileges until you close the program, nautilus.

---

### Post by El Rogueo on 2007-09-08
In Ubuntu, you don't actually login to Root, instead you use the sudo (Superuser Do) command to allow you root privileges temporarily (being one action at a time). It's a safety feature to ensure you don't, say, move those files into the void and lose them forever. You can go around it, but it's best to just enter your password at the prompt, rather than risk that you might do something fatal (and unrecoverable)

---

### Post by comradexiactura on 2007-09-08
Thanks, this really helps. Using Nautilus worked great. Do you guys know of any tutorial that has a commands list and defines them.

---

### Post by overdrank on 2007-09-08
> **comradexiactura said:**
> Thanks, this really helps. Using Nautilus worked great. Do you guys know of any tutorial that has a commands list and defines them.

Hi these links may help! Good luck! 
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

