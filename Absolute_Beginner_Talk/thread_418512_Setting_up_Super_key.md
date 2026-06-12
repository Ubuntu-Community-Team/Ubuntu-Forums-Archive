---
title: "Setting up Super key"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-04-22
How do I set up my windows key to act as the Super key?  I thought I had enabled it in the keyboard setup but apparently I haven't.  I have a US keybard and I believe it has 104 keys on it

---

### Post by Ocxic on 2007-04-22
in a terminal type
"sudo dpkg-reconfigure xserver-xorg"

through-out the process of reconfiguring it'll ask about the keyboard and options for it, add the option alt_meta:win I'm not sure if it's the exact option, but if you read every screen it will tell you what to do to enable you windows key.

TIP: b4 you do that do this:
"sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bk" to make a backup of you config file just in case it messes something up,
if it does you can reload your config file by doing:
"sudo cp /etc/X11/xorg.conf.bk /etc/X11/xorg.conf"

---

### Post by zhinker on 2007-04-22
> **Ocxic said:**
> in a terminal type
"sudo dpkg-reconfigure xserver-xorg"

through-out the process of reconfiguring it'll ask about the keyboard and options for it, add the option alt_meta:win I'm not sure if it's the exact option, but if you read every screen it will tell you what to do to enable you windows key.

TIP: b4 you do that do this:
"sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bk" to make a backup of you config file just in case it messes something up,
if it does you can reload your config file by doing:
"sudo cp /etc/X11/xorg.conf.bk /etc/X11/xorg.conf"

I'm not sure I want to do that.  I had to mess around with my configurations to get Beryl working in the first place and doing the autoconfiguration might undo some of those changes.  Could you tell me how I can directly access the config file and change only the parts I need to?

---

